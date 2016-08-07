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
1. 整数、浮点数
2. 字符串
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
		由于字典也是序列的一种，所起它有很多操作(比如len和成员资格)都和序列类似：
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
	- break:	用于跳出最近的一级 for 或 while 循环。
	- continue:	 语句是从 C 中借鉴来的，它表示循环继续执行下一次迭代:
5. ___pass 语句___
```python
	pass 语句什么也不做。它用于那些语法上必须要有什么语句，但程序什么也不做的场合，例如:

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
	在函数内部，可以调用其他函数。如果一个函数在内部调用自身本身，这个函数就是递归函数
	使用递归函数的优点是逻辑简单清晰，缺点是过深的调用会导致栈溢出。
```python
	def fact(n):
		if n==1:
			return 1
		return n * fact(n - 1)
```
5. ___函数式编程___
	- 高阶函数
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