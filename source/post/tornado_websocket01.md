```toml

title = "Python分享-01"
slug = "2016"
date = "2016-06-19 18:49:59"
author = "miaoboyong"
tags = ["python,tornado"]

```
<!--lang: python-->
    import os
    import tornado
    from tornado.websocket import WebSocketHandler
    from tornado.concurrent import run_on_executor
    from concurrent.futures import ThreadPoolExecutor
    from collections import deque
    import time

    logfile = '1.txt'
    default_line = 2000


    def tail(f):
        f.seek(0, 2)
        while True:
            line = f.readline()
            if not line:
                time.sleep(0.05)
                continue
            yield line


    class IndexHandler(tornado.web.RequestHandler):
        def get(self):
            self.render("index.html")


    class LogWebSocket(WebSocketHandler):
        executor = ThreadPoolExecutor(2)
        waiters = set()
        cache = []
        cache_size = 200
        is_send = False

        @classmethod
        def update_cache(cls, chat):
            cls.cache.append(chat)
            if len(cls.cache) > cls.cache_size:
                cls.cache = cls.cache[-cls.cache_size:]

        @classmethod
        def send_updates(cls, chat):
            for waiter in cls.waiters:
                try:
                    waiter.write_message(chat)
                except:
                    pass

        def open(self):
            LogWebSocket.waiters.add(self)

        @tornado.gen.coroutine
        def on_message(self, message):
            for line in deque(open(logfile), default_line):
                self.write_message(line.rstrip('\n'))
            if not LogWebSocket.is_send:
                LogWebSocket.is_send = True
                f = open(logfile)
                LogWebSocket.update(f)

        @classmethod
        @run_on_executor
        def update(cls, f):
            for line in tail(f):
                print(cls.waiters)
                if not cls.waiters:
                    cls.is_send = False
                    break
                line = line.rstrip('\n')
                cls.update_cache(line)
                cls.send_updates(line)

        def on_close(self):
            LogWebSocket.waiters.remove(self)

        def check_origin(self, origin):
            return True


    def make_app():
        settings = dict(
            template_path=os.path.join(os.path.dirname(__file__), "templates"),
            static_path=os.path.join(os.path.dirname(__file__), "static"),
        )
        return tornado.web.Application([
            (r"/", IndexHandler),
            (r"/log", LogWebSocket),
        ], **settings)

    if __name__ == "__main__":
        app = make_app()
        app.listen(8889)
        tornado.ioloop.IOLoop.current().start()