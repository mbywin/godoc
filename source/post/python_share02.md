```toml
title = "Python分享-02"
slug = "2016"
date = "2016-07-28 09:49:59"
author = "miaoboyong"
tags = ["python"]
```
***
# python 学习分享-2
***
#### __python标准数据类型:__
1. ___整数、浮点数___
2. ___字符串___
	- *字符编码*
		- ASCII
		- Unicode
		- UTF-8

	> ![字符编码](http://www.liaoxuefeng.com/files/attachments/0013872491802084161ec9ef7d143a897e1584819535656000/0 "字符编码")
	> ![utf-8](http://www.liaoxuefeng.com/files/attachments/001387245992536e2ba28125cf04f5c8985dbc94a02245e000/0 "utf-8")

	> 注：由于Python源代码也是一个文本文件，所以，当你的源代码中包含中文的时候，在保存源代码时，就需要务必指定保存为UTF-8编码。当Python解释器读取源代码时，为了让它按UTF-8编码读取，我们通常在文件开头写上这两行：

	```python
		#!/usr/bin/env python3
		# -*- coding: utf-8 -*-
	```

	- *常用字符串函数*
		- find
		- join
		- lower
		- replace
		- split
		- strip
	- *字符串格式化

	```python
        通过位置:
        	'Hello, %s' % 'world' or 'Hello, {0}'.format('world')

        通过关键字参数:
        	'{name},{age}'.format(age=98, name='kfc')

        通过对象属性:
			class Person:
				def __init__(self,name,age):
					self.name,self.age = name,age
				def __str__(self):
					return 'This guy is {self.name},is {self.age} old'.format(self=self)

        通过下标:
			p=['kfc', 98]
			'{0[0]},{0[1]}'.format(p)

        精度与类型:
        	'{:.2f}'.format(3.1415926)
	```

3. ___序列（列表，元祖）___
	- *通用操作*
		- 索引
		- 分片
		- 加
		- 乘
		- 检查某个元素是否属于这序列
		- 计算序列长度
		- 找出最大元素和最小元素
	- *列表特点*
		- 有序的集合
		- 通过偏移来索引，从而读取数据
		- 支持嵌套
		- 可变的类型
		- 查找和插入的时间随着元素的增加而增加
		- 占用空间小，浪费内存很少
	- *元祖特点*
		- 有序的集合
		- 通过偏移来取数据
		- 属于不可变的对象，不能在原地修改内容，没有排序，修改等操作。
		*注：只有1个元素的tuple定义时必须加一个逗号,，来消除歧义: `t = (1,)`*
	- *列表操作*
		- *list函数*

		```python
			list()
		```

		- *基本的列表操作*
			- 元素赋值
			- 删除元素
			- 分片赋值
		- *列表方法*
			- append
			- count
			- extend
			- index
			- insert
			- pop
			- remove
			- sort
	- *列表解析*

	```python
		L = [(x+1,y+1) for x in range(3) for y in range(5) if y> 2 ]
	```

	- *元祖使用*
		- 元组可以在映射(和集合的成员)中作为键(key)使用，而列表不行
	    - 元组作为很多内建函数和方法的返回值存在
4. ___字典___
	- *特点*
		- 无序的
		- key必须是不可变对象
		- 查找和插入的速度极快，不会随着key的增加而变慢
		- 需要占用大量的内存，内存浪费多
	- *字典的基本操作*
		- 由于字典也是序列的一种，所起它有很多操作(比如len和成员资格)都和序列类似:

	```python
		len(d)：返回d中项的数量;
		d[key]：返回这个key对应的value;
		d[key] = v：将值v映射到key值为k的项;
		key in did:检查d中是否包含键为k的项;
	```

	- *字典常用函数*
		- clear
		- copy
		- fromkeys
		- get
		- has_key
		- items和iteritems
		- keys和iterkeys
		- values和itervalues
		- pop
		- popitem
		- setdefault
		- update
	- *字典遍历：*

	```python
		for i in d:
			t = i + d[i]

		for k,v in d.items():
			t = k + v

		for k,v in d.iteritems():
			t = k + v

		for k,v in zip(d.iterkeys(),d.itervalues()):
			t = k + v
	```

	- *字典解析：*

	```python
		{value:key for key ,value in a_dict.items()}
	```

5. ___集合___
	- *特点*
		- 无序的
		- 元素不重复（常用于列表去重）
	- *集合操作*

	```python
		a = 'hello'
		s = set(a)
		output: set(['h', 'e', 'l', 'o'])
		集合转列表
			l = list(s)
			l = [ i for i in s ]
		列表传集合
			s = set(l)
		集合的数据操作:
			交集、合集（并集）、差集等：
	```

	![集合操作](http://www.iplaypython.com/uploads/allimg/131215/2-131215203406215.jpg "集合操作")

***

#### __python流程控制:__
1. ___if 语句___

    ```python
        if x < 0:
            x = 0
            print('Negative changed to zero')
        elif x == 0:
            print('Zero')
        elif x == 1:
            print('Single')
        else:
            print('More')
    ```

2. ___for 语句___

    ```python
        words = ['cat', 'window', 'defenestrate', '']
        for word in words:
            if not words:
                break
        else:
            print(words)
    ```

3. ___range() 函数__

4. ___break 和 continue 语句___

	> break:	用于跳出最近的一级 for 或 while 循环。
	> continue:	 语句是从 C 中借鉴来的，它表示循环继续执行下一次迭代:
5. ___pass 语句___

	> pass 语句什么也不做。它用于那些语法上必须要有什么语句，但程序什么也不做的场合，例如:

    ```python
        while True:
            pass

        class MyEmptyClass:
            pass
    ```

#### __函数:__
1. ___调用函数___
2. ___定义函数___

    ```python
        def my_abs(x):
            if not isinstance(x, (int, float)):
                raise TypeError('bad operand type')
            if x >= 0:
                return x
            else:
                return -x
        返回多个值
        def test():
            return 1, 2
    ```

3. ___函数的参数___
	- 位置参数

    ```python
        def power(x, n):
            s = 1
            while n > 0:
                n = n - 1
                s = s * x
        return s
    ```

	- 默认参数

    ```python
        def power(x, n=2):
            s = 1
            while n > 0:
                n = n - 1
                s = s * x
            return s
    ```

	- 可变参数

    ```python
        def calc(*numbers):
            sum = 0
            for n in numbers:
                sum = sum + n * n
            return sum
    ```

	- 关键字参数

    ```python
        def person(name, age, **kw):
            print('name:', name, 'age:', age, 'other:', kw)
    ```

	- 命名关键字参数

    ```python
        def person(name, age, *args, city, job):
            print(name, age, args, city, job)
    ```

	- 参数组合

    ```python
        def f1(a, b, c=0, *args, **kw):
            print('a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw)
    -
        def f2(a, b, c=0, *, d, **kw):
            print('a =', a, 'b =', b, 'c =', c, 'd =', d, 'kw =', kw)
    ```

4. ___递归函数___

	> 在函数内部，可以调用其他函数。如果一个函数在内部调用自身本身，这个函数就是递归函数
	>
	> 使用递归函数的优点是逻辑简单清晰，缺点是过深的调用会导致栈溢出。

    ```python
        def fact(n):
            if n==1:
                return 1
            return n * fact(n - 1)
    ```

#### __高级特性__:
1. ___切片___(列表和元祖)

    ```python
        L = ['Michael', 'Sarah', 'Tracy', 'Bob', 'Jack']

        取前3个元素:
            L[0:3], L[:3]
        从索引1开始，取出2个元素出来:
            L[1:3]
        L[-1]取倒数第一个元素，那么它同样支持倒数切片
            L[-2:]
        原样复制一个list
            L[:]
    ```

2. ___迭代___

	> 我们已经知道，可以直接作用于for循环的数据类型有以下几种：
	> 一类是集合数据类型，如list、tuple、dict、set、str等；
	> 一类是generator，包括生成器和带yield的generator function。
	> 这些可以直接作用于for循环的对象统称为可迭代对象：Iterable。

    ```python
    	from collections import Iterable
        isinstance('abc', Iterable) # str是否可迭代
        isinstance([1,2,3], Iterable) # list是否可迭代
        isinstance(123, Iterable) # 整数是否可迭代

    	for i, value in enumerate(['A', 'B', 'C']):
     		print(i, value)
    ```

3. ___列表生成式___

	```python
    	[x * x for x in range(1, 11) if x % 2 == 0]

        import os
        [d for d in os.listdir('.')]
    ```

4. ___生成器___

	> 通过列表生成式，我们可以直接创建一个列表。但是，受到内存限制，列表容量肯定是有限的。而且，创建一个包含100万个元素的列表，不仅占用很大的存储空间，如果我们仅仅需要访问前面几个元素，那后面绝大多数元素占用的空间都白白浪费了。

	> 所以，如果列表元素可以按照某种算法推算出来，那我们是否可以在循环的过程中不断推算出后续的元素呢？这样就不必创建完整的list，从而节省大量的空间。在Python中，这种一边循环一边计算的机制，称为生成器：generator

    ```python
    	g = (x * x for x in range(10))

    	def fib(max):
    		n, a, b = 0, 0, 1
    		while n < max:
        		yield b
        		a, b = b, a + b
        		n = n + 1
    		return 'done'
    ```

5. ___迭代器___

	> 生成器不但可以作用于for循环，还可以被next()函数不断调用并返回下一个值，直到最后抛出StopIteration错误表示无法继续返回下一个值了
	>
	> 可以被next()函数调用并不断返回下一个值的对象称为迭代器：Iterator。
	>
	> 生成器都是Iterator对象，但list、dict、str虽然是Iterable，却不是Iterator。

    ```python
    	from collections import Iterator
		isinstance((x for x in range(10)), Iterator): True
		isinstance([], Iterator):False
		isinstance({}, Iterator):False
		isinstance('abc', Iterator):False
    ```

    > 凡是可作用于for循环的对象都是Iterable类型；

	> 凡是可作用于next()函数的对象都是Iterator类型，它们表示一个惰性计算的序列；

	> 集合数据类型如list、dict、str等是Iterable但不是Iterator，不过可以通过iter()函数获得一个Iterator对象。


#### __函数式编程__:
1. ___高阶函数___
	- map/reduce：

	```python
		def f(x):
			return x * x

		r = map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
		# 列表中int转为str
		list(map(str, [1, 2, 3, 4, 5, 6, 7, 8, 9]))

		# reduce
		from functools import reduce
		def fn(x, y):
			return x * 10 + y

		reduce(fn, [1, 3, 5, 7, 9])
	```
	- filter

	> 在一个list中，删掉偶数，只保留奇数:

    ```python
        def is_odd(n):
            return n % 2 == 1
        list(filter(is_odd, [1, 2, 4, 5, 6, 9, 10, 15]))
    ```
	- sorted

    ```python
        sorted(['bob', 'about', 'Zoo', 'Credit'], key=str.lower, reverse=True)
    ```
2. ___返回函数（闭包）___

	> 函数作为返回值：
	> 高阶函数除了可以接受函数作为参数外，还可以把函数作为结果值返回。

    ```python
        def lazy_sum(*args):
            def sum():
                ax = 0
                for n in args:
                ax = ax + n
                return ax
            return sum
        f = lazy_sum(1, 3, 5, 7, 9)
    ```

	> 注意到返回的函数在其定义内部引用了局部变量args，所以，当一个函数返回了一个函数后，其内部的局部变量还被新函数引用。

	```python
        def count():
            fs = []
            for i in range(1, 4):
                def f():
                    return i*i
                fs.append(f)
            return fs

        f1, f2, f3 = count()

        def count():
            def f(j):
                def g():
                    return j*j
                return g
            fs = []
            for i in range(1, 4):
                fs.append(f(i)) # f(i)立刻被执行，因此i的当前值被传入f()
            return fs
	```
3. ___匿名函数(lambda)___

    ```python
         list(map(lambda x: x * x, [1, 2, 3, 4, 5, 6, 7, 8, 9]))
    ```

4. ___装饰器___

    ```python
        import functools

        def log(func):
            @functools.wraps(func)
            def wrapper(*args, **kw):
                print('call %s():' % func.__name__)
                return func(*args, **kw)
            return wrapper

        def log(text):
            def decorator(func):
                @functools.wraps(func)
                def wrapper(*args, **kw):
                    print('%s %s():' % (text, func.__name__))
                    return func(*args, **kw)
                return wrapper
            return decorator
    ```

5. ___偏函数___

	> functools.partial的作用就是，把一个函数的某些参数给固定住（也就是设置默认值），返回一个新的函数，调用这个新函数会更简单。

    ```python
        int2 = functools.partial(int, base=2)
        max2 = functools.partial(max, 10)
    ```