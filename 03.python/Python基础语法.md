# Python基础语法

## 1、输入和输出

### 1.1 输入



- 输入：

```python
a = input()
# 可以输出提示信息
a = input('这里是提示信息')
# 从控制太获得多个变量,用逗号隔开
a,b = eval(input())
```



### 1.2 输出



- 输出：

```python
print('a')

# 可接受多个字符串,用逗号“,”隔开,可连成一串输出
print('a','b')	# 结果：a b
# 可使用内置方法sep将逗号转换为其他符号
print('a', 'b', sep='\n')
# 可以使用end将最后的换行换成其他
print('abc', end='\t')

# 如果字符串内部有很多换行，除了用\n,还能用'''...'''形式
print('''line1
... line2
... line3''')
line1
line2
line3
```

- `print()`会依次打印每个字符串，**遇到逗号“,”会输出一个空格**，**可以通过内置方法sep改为其他**。



####  1.2.1 格式化输出

在Python中，采用的格式化方式和C语言是一致的，用`%`实现，举例如下：

```python
>>> 'Hello, %s' % 'world'
'Hello, world'
>>> 'Hi, %s, you have $%d.' % ('Michael', 1000000)
'Hi, Michael, you have $1000000.'
```

- `%`运算符就是用来格式化字符串的。在字符串内部，`%s`表示用字符串替换，`%d`表示用整数替换，有几个`%?`占位符，后面就跟几个变量或者值，顺序要对应好。如果只有一个`%?`，括号可以省略。

- 如果你不太确定应该用什么，`%s`永远起作用，它会把任何数据类型转换为字符串：
- 有些时候，字符串里面的`%`是一个普通字符怎么办？这个时候就需要转义，==用`%%`来表示一个`%`==



- ==**格式化输出的对齐问题：**==
- %s控制字符串长度
    - %-10s，可以实现字符串左对齐输出，间隔10个字符
    - %+20s，可以实现字符串右对齐输出，间隔20个字符



#### 1.2.2 format()输出

另一种格式化字符串的方法是使用字符串的`format()`方法，它会用传入的参数依次替换字符串内的占位符`{0}`、`{1}`……，不过这种方式写起来比%要麻烦得多：

```python
>>> 'Hello, {0}, 成绩提升了 {1:.1f}%'.format('小明', 17.125)
'Hello, 小明, 成绩提升了 17.1%'
```

| :        | <填充>             | <对齐>                          | <宽度>         | <，>             | <.精度>                                | <类型>                        |
| -------- | ------------------ | ------------------------------- | -------------- | ---------------- | -------------------------------------- | ----------------------------- |
| 引导符号 | 用于填充的单个字符 | <左对齐<br />>右对齐<br />^居中 | 设定输出的宽度 | 数字的前位分隔符 | 浮点小数精度或字符串<br />最大输出长度 | 输出的类型<br />b,c,d,o,x,e,f |



#### 1.2.3 f-string输出

使用以`f`开头的字符串，称之为`f-string`，它和普通字符串不同之处在于，字符串如果包含`{xxx}`，就会以对应的变量替换：

```python
>>> r = 2.5
>>> s = 3.14 * r ** 2
>>> print(f'The area of a circle with radius {r} is {s:.2f}')
The area of a circle with radius 2.5 is 19.62
```

上述代码中，`{r}`被变量`r`的值替换，`{s:.2f}`被变量`s`的值替换，并且`:`后面的`.2f`指定了格式化参数（即保留两位小数），因此，`{s:.2f}`的替换结果是`19.62`。





## 2、基本数据类型

### 2.1 整数



- Python可以处理==任意大小==的整数，包括负整数。

- 有时候用十六进制表示整数比较方便，十六进制用`0x`前缀和0-9，a-f表示，例如：`0xff00`，`0xa5b4c3d2`，等等
- Python允许在数字中间以`_`分隔，因此，写成`10_000_000_000`和`10000000000`是完全一样的。



### 2.2 浮点数



- 浮点数也就是小数，之所以称为浮点数，是因为按照科学记数法表示时，一个浮点数的小数点位置是可变的，比如，1.23x109和12.3x108是完全相等的。
- 对于很大或很小的浮点数，就必须用科学计数法表示，把10用e替代，$1.23\times 10^9$就是`1.23e9`，或者`12.3e8`

- 整数和浮点数在计算机内部存储的方式是不同的，整数运算永远是精确的（除法难道也是精确的？是的！），而浮点数运算则**可能会有四舍五入的误差**。



### 2.3 字符串



- 字符串是以单引号`'`或双引号`"`括起来的任意文本

- 如果字符串内部既包含`'`又包含`"`怎么办？可以用转义字符`\`来标识

    转义字符`\`可以转义很多字符，比如`\n`表示换行，`\t`表示制表符，字符`\`本身也要转义，所以`\\`表示的字符就是`\`



### 2.4 布尔值



- 布尔值和布尔代数的表示完全一致，一个布尔值只有`True`、`False`两种值，要么是`True`，要么是`False`
- 在Python中，可以直接用`True`、`False`表示布尔值（请注意大小写）



### 2.5 空值



- 空值是Python里一个特殊的值，用`None`表示。
- `None`不能理解为`0`，因为`0`是有意义的，而`None`是一个特殊的空值。



### 2.6 变量



- 变量在程序中就是用一个变量名表示了，变量名必须是大小写英文、数字和`_`的组合，且不能用数字开头

- 在python中，变量的类型可以变。
- 这种变量本身类型不固定的语言称之为==*动态语言*==，与之对应的是==*静态语言*==。
- 静态语言在定义变量时必须指定变量类型，如果赋值的时候类型不匹配，就会报错。



#### 2.6.1 变量在计算机内存中的表示

```python
a = 'ABC'
```

Python解释器干了两件事情：

1. **在内存中创建了一个`'ABC'`的字符串；**
2. **在内存中创建了一个名为`a`的变量，并把它指向`'ABC'`。**

也可以把一个变量`a`赋值给另一个变量`b`，这个操作实际上是把变量`b`指向变量`a`所指向的数据



- 在python中，变量不同于数据值，各个变量都相当于一个没有指定数据类型的指针，即可以指针任何一个值，例如整数、字符串、函数等。
- 对变量赋值，实际上是让这个变量指向这个值，或指向被赋值变量指向的数据。



### 2.7 常量



- 所谓常量就是不能变的变量，比如常用的数学常数π就是一个常量。
- 在Python中，通常用**==全部大写==**的变量名表示常量，例如定义常量`PI=3.1415926`。
- Python根本没有任何机制保证`PI`不会被改变，所以，用全部大写的变量名表示常量只是一个习惯上的用法，如果你一定要改变变量`PI`的值，也没人能拦住你。





## 3、运算符

### 3.1 数值运算操作符



- 加减乘除：`+、-、*、/`。
- 地板除：`//`。两个整数的除法仍然是整数
- 取余运算：`%`。
- 幂运算：`**`。
    - `x**y`，当y为小数时，开放运算。



### 3.2 逻辑运算符



- 与运算 ：`and`
- 或运算：`or`
- 非运算：`not`





## 4、字符编码问题

### 4.1 字符集

- 因为计算机只能处理数字，如果要处理文本，就必须先把文本转换为数字才能处理。
- 最早只有127个字符被编码到计算机里，也就是大小写英文字母、数字和一些符号，这个编码表被称为`ASCII`编码。
- 中国制定了`GB2312`编码，用来把中文编进去。



- `Unicode`字符集把所有语言都统一到一套编码里，这样就不会再有乱码问题了。
- 如果统一成Unicode编码，乱码问题从此消失了。但是，如果你写的文本基本上全部是英文的话，用Unicode编码比ASCII编码需要多一倍的存储空间，在存储和传输上就十分不划算。



- 本着节约的精神，又出现了把Unicode编码转化为“可变长编码”的`UTF-8`编码。UTF-8编码把一个Unicode字符根据不同的数字大小编码成1-6个字节，常用的英文字母被编码成1个字节，汉字通常是3个字节，只有很生僻的字符才会被编码成4-6个字节。

- UTF-8编码有一个额外的好处，就是ASCII编码实际上可以被看成是UTF-8编码的一部分，所以，大量只支持ASCII编码的历史遗留软件可以在UTF-8编码下继续工作。



### 4.2 字符编码在计算机中的工作方式

搞清楚了ASCII、Unicode和UTF-8的关系，我们就可以总结一下现在计算机系统通用的字符编码工作方式：

- 在计算机内存中，统一使用Unicode编码，当需要保存到硬盘或者需要传输的时候，就转换为UTF-8编码。

- 用记事本编辑的时候，从文件读取的UTF-8字符被转换为Unicode字符到内存里，编辑完成后，保存的时候再把Unicode转换为UTF-8保存到文件：

![rw-file-utf-8](assets/0.png)

- 浏览网页的时候，服务器会把动态生成的Unicode内容转换为UTF-8再传输到浏览器：

![web-utf-8](assets/0.png)



### 4.3 Python字符串

- 在最新的Python 3版本中，字符串是以Unicode编码的。
- 对于单个字符的编码，Python提供了`ord()`函数获取字符的整数表示，`chr()`函数把编码转换为对应的字符：

```python
>>> ord('A')
65
>>> ord('中')
20013
>>> chr(66)
'B'
>>> chr(25991)
'文'
```

如果知道字符的整数编码，还可以用十六进制这么写`str`：

```python
>>> '\u4e2d\u6587'
'中文'
```



- 由于Python的字符串类型是`str`，**在内存中以Unicode表示，一个字符对应若干个字节**。
- 如果要在网络上传输，或者保存到磁盘上，就需要把`str`变为以字节为单位的`bytes`。

Python对`bytes`类型的数据用带`b`前缀的单引号或双引号表示：

```python
x = b'ABC'
```

要注意区分`'ABC'`和`b'ABC'`，前者是`str`，后者虽然内容显示得和前者一样，但**`bytes`的每个字符都只占用一个字节。**

==以Unicode表示==的`str`通过`encode()`方法可以编码为指定的`bytes`，例如：

```python
>>> 'ABC'.encode('ascii')
b'ABC'
>>> '中文'.encode('utf-8')
b'\xe4\xb8\xad\xe6\x96\x87'
>>> '中文'.encode('ascii')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
UnicodeEncodeError: 'ascii' codec can't encode characters in position 0-1: ordinal not in range(128)
```

- 纯英文的`str`可以用`ASCII`编码为`bytes`，内容是一样的，含有中文的`str`可以用`UTF-8`编码为`bytes`。
- 含有中文的`str`无法用`ASCII`编码，因为中文编码的范围超过了`ASCII`编码的范围，Python会报错。
- 在`bytes`中，无法显示为ASCII字符的字节，用`\x##`显示。

反过来，如果我们**从网络或磁盘上读取了字节流，那么读到的数据就是`bytes`。**要把`bytes`变为`str`，就需要用`decode()`方法：

```python
>>> b'ABC'.decode('ascii')
'ABC'
>>> b'\xe4\xb8\xad\xe6\x96\x87'.decode('utf-8')
'中文'
```

如果`bytes`中包含无法解码的字节，`decode()`方法会报错：

```python
>>> b'\xe4\xb8\xad\xff'.decode('utf-8')
Traceback (most recent call last):
  ...
UnicodeDecodeError: 'utf-8' codec can't decode byte 0xff in position 3: invalid start byte
```

如果`bytes`中只有一小部分无效的字节，可以传入`errors='ignore'`忽略错误的字节：

```python
>>> b'\xe4\xb8\xad\xff'.decode('utf-8', errors='ignore')
'中'
```



要计算`str`包含多少个字符，可以用`len()`函数：

```python
>>> len('ABC')
3
>>> len('中文')
2
```

`len()`函数计算的是`str`的字符数，如果换成`bytes`，`len()`函数就计算字节数：

```python
>>> len(b'ABC')
3
>>> len(b'\xe4\xb8\xad\xe6\x96\x87')
6
>>> len('中文'.encode('utf-8'))
6
```

可见，1个中文字符经过UTF-8编码后通常会占用3个字节，而1个英文字符只占用1个字节。

在操作字符串时，我们经常遇到`str`和`bytes`的互相转换。为了避免乱码问题，应当始终坚持使用UTF-8编码对`str`和`bytes`进行转换。

```python
# -*- coding: utf-8 -*-
```

- **注释是为了告诉Python解释器，按照UTF-8编码读取源代码，否则，你在源代码中写的中文输出可能会有乱码。**



## 5、字符串

### 5.1 原始字符串

在字符串前面加`r`，可以屏蔽`\`的作用

```python
s='python'
s='py\nthon'
s=r'py\nthon\t'
```

### 5.2 字符串的内置函数

```python
#切割
str.split(str1) #以str1为分隔符对字符串切割，返回一个列表
#替换
str.replace(str1,str2) #将字符串中的str1替换为str2生成的新的字符串
#大小写转换
str.lower()
str.upper()
str.title()	#首字母大写每个单词
#删除空白
str.strip()
str.lstrip()
str.rstrip()
#拼接
str.join(iter) #将所给参数中的每个元素以指定的字符连接生成一个新的字符串
"-".join("python")
"p-y-t-h-o-n"
```

### 5.3 字符串拼接

```python
# 字符串可以直接通过加号拼接
first_name = "ada" 
last_name = "lovelace" 
full_name = first_name + " " + last_name
print("Hello, " + full_name.title() + "!") 
```

### 5.4 使用str()避免类型错误

```python
age = 23 
# 将int类型转化为string才能拼接
message = "Happy " + str(age) + "rd Birthday!" 
```



## 6、Python之禅

- 编程语言Perl曾在互联网领域长期占据着统治地位，早期的大多数交互式网站使用的都是 Perl脚本。
- 彼时，“解决问题的办法有多个”被Perl社区奉为座右铭。这种理念一度深受大家的喜 爱，因为这种语言固有的灵活性使得大多数问题都有很多不同的解决之道。
- 在开发项目期间，这 种灵活性是可以接受的，但大家最终认识到，过于强调灵活性会导致大型项目难以维护：要通过 研究代码搞清楚当时解决复杂问题的人是怎么想的，既困难又麻烦，还会耗费大量的时间。
- 经验丰富的程序员倡导尽可能避繁就简。Python社区的理念都包含在Tim Peters撰写的 “Python之禅”中。要获悉这些有关编写优秀Python代码的指导原则，只需在解释器中执行命令 import this。

```python
>>> import this
The Zen of Python, by Tim Peters 
```





## 7、list列表

### 7.1 创建和索引

- Python内置的一种数据类型是列表：`list`。
- list是一种有序的集合，可以随时添加和删除其中的元素。

```python
# 列出班里所有同学的名字，就可以用一个list表示:
>>> classmates = ['Michael', 'Bob', 'Tracy']
# 用len()函数可以获得list元素的个数：
>>> len(classmates)
3
# 用索引来访问list中每一个位置的元素，记得索引是从0开始的：
>>> classmates[0]
'Michael'
# 如果要取最后一个元素，除了计算索引位置外，还可以用-1做索引，直接获取最后一个元素：
>>> classmates[-1]
'Tracy'
```

- 当索引超出了范围时，Python会报一个`IndexError`错误



- list里面的元素的数据类型也可以不同
- list元素也可以是另一个list
- **列表可以为空**



### 7.2 修改、添加和删除元素

- **修改列表元素**

    ```python
    motorcycles = ['honda', 'yamaha', 'suzuki'] 
    
    motorcycles[0] = 'ducati'
    ```

- **在列表中添加元素**

    ```python
    # 1. 在列表末尾添加元素
    motorcycles.append('ducati') 
    
    # 2. 在列表中插入元素
    motorcycles.insert(0, 'ducati')  # 需要指定新元素的索引和值
    ```

- **从列表中删除元素**

    技巧：

    如果你要从列表 中删除一个元素，且**不再以任何方式使用它**，就使用**del语句**；

    如果你要在删除元素后还能**继续使用它**，就使用**方法pop()**。

    ```python
    # 1. 使用del语句删除元素
    # 如果知道要删除的元素在列表中的位置，可使用del语句。
    del motorcycles[0]
    
    # 2. 使用方法pop()删除元素
    # 方法pop()可删除列表末尾的元素，并让你能够接着使用它。
    a = motorcycles.pop()
    
    # 3. 弹出列表中任何位置处的元素
    # 实际上，你可以使用pop()来删除列表中任何位置的元素，只需在括号中指定要删除的元素的索引即可。
    a = motorcycles.pop(0) 
    
    # 4. 根据值删除元素
    motorcycles.remove('ducati')
    # 注意 方法remove()只删除第一个指定的值。如果要删除的值可能在列表中出现多次，就需要使用循环来判断是否删除了所有这样的值。
    ```

    

### 7.3 组织列表(排序、反转等)

- 使用==方法== `sort()`对列表进行==**永久性排序**==

    ```python
    cars = ['bmw', 'audi', 'toyota', 'subaru'] 
    cars.sort()
    # 输出：['audi', 'bmw', 'subaru', 'toyota'] 
    
    # 若要反向排序，只需向sort()方法传递参数reverse=True。
    cars.sort(reverse=True)
    # 输出：['toyota', 'subaru', 'bmw', 'audi'] 
    ```

- 使用==函数== `sorted()`对列表进行==**临时排序**==

    ```python
    sorted(cars)
    sorted(cars, reverse=True)
    ```

- 反转列表元素，可使用方法reverse()

    ```python
    cars.reverse()
    # 永久修改，要恢复，再次调用即可
    ```

- 确定列表的长度

    ```python
    len(cars)
    ```

    

### 7.4 操作列表(遍历、求和等)

- 遍历列表

    ```python
     magicians = ['alice', 'david', 'carolina'] 
    for magician in magicians: 
    	print(magician) 
    ```

- 创建数值列表

    ```python
    numbers = list(range(1,6)) 
    # [1, 2, 3, 4, 5] 
    even_numbers = list(range(2,11,2)) 
    # [2, 4, 6, 8, 10] 
    ```

- 对数字列表执行简单的统计计算

    ```python
    >>> digits = [1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
    >>> min(digits)
    0 
    >>> max(digits)
    9 
    >>> sum(digits)
    45 
    ```

- 列表解析

    列表解析将for循环和创建新元素的代码合并成一行，并自动附加新元素。

    ```python
    squares = [value**2 for value in range(1,11)] 
    ```



### 7.5 使用列表的一部分(切片、硬拷贝)

- 切片

    ```python
    players = ['charles', 'martina', 'michael', 'florence', 'eli'] 
    print(players[0:3]) # 0、1、2
    ```

- 遍历切片

    ```python
    for player in players[:3]: 
    print(player.title()) 
    ```

- 硬拷贝

    ```python
    my_foods = ['pizza', 'falafel', 'carrot cake'] 
    friend_foods = my_foods[:] 
    ```




### 7.6 数据拷贝问题

- 浅拷贝（copy()），表面结构进行拷贝，**嵌套结构的元素是引用**。修改嵌套结构的数据会影响到拷贝得到的数据。
- 深拷贝，解决了嵌套结构中深层结构只是引用的问题，它会**对所有的数据进行一次复制**，修改之前的数据不会改变拷贝得到的数据。

```python
# 数据赋值
a = [1,2,3,[4,5]]
b = a #赋值
c = a.copy() # 浅拷贝

import copy
d = copy.deepcopy(a) # 深拷贝
```





## 8、tuple元组

- 另一种有序列表叫元组：tuple
- tuple和list非常类似，但是**tuple一旦初始化就不能修改**
- 它也没有append()，insert()这样的方法。其他获取元素的方法和list是一样的，你可以正常地使用`classmates[0]`，`classmates[-1]`，但不能赋值成另外的元素。

```python
>>> classmates = ('Michael', 'Bob', 'Tracy')
```



**tuple的注意事项:**

```python
#创建单个元素的元组需要用“，”来标明是元组
t1=(5)		# t1 <class 'int'>
t2=(5,)		# t2 <class 'tuple'>
```



**“可变的”tuple：**

```python
>>> t = ('a', 'b', ['A', 'B'])
>>> t[2][0] = 'X'
>>> t[2][1] = 'Y'
>>> t
('a', 'b', ['X', 'Y'])
```

- 表面上看，tuple的元素确实变了，但其实变的不是tuple的元素，而是list的元素。
- tuple所谓的“不变”是说，tuple的每个元素，指向永远不变。



## 9、代码编写格式指南

### 9.1 格式设置指南

- 若要提出Python语言修改建议，需要编写**Python改进提案（Python Enhancement Proposal， PEP）**。
- **PEP 8**是最古老的PEP之一，它向Python程序员提供了代码格式设置指南。



### 9.2 缩进

- PEP 8建议每级缩进都使用四个空格，这既可提高可读性，又留下了足够的多级缩进空间。



### 9.3 行长

- 很多Python程序员都建议每行不超过80字符。最初制定这样的指南时，在大多数计算机中， 终端窗口每行只能容纳79字符。
- 专业程序员通常会在同一个屏幕上打开多个文件，使用标准行长可以让他们在屏幕上并排打开两三个文件时能同时看到各个文件的完整行。
- PEP 8还建议**注释的行长都不超过72字符**，因为有些工具为大型项目自动生成文档时，会在每行注释开头**添加格式化字符**。
- 在大多数编辑器中，都可设置一个视觉标志——通常是一条竖线，让你知道不能越过的界线在什 么地方。



### 9.4 空行

- 要将程序的不同部分分开，可使用空行。你应该使用空行来组织程序文件，但也不能滥用；
- 空行不会影响代码的运行，但会影响代码的可读性。
- Python解释器根据水平缩进情况来解读 代码，但不关心垂直间距。



### 9.5 设置 if 语句的格式

- 在条件测试的格式设置方面，PEP 8提供的唯一建议是，在诸如==、>=和<=等比较运算符两边各添加一个空格，例如，if age < 4:要比if age<4:好。



### 9.6 函数编写指南

1. 应给函数指定描述性名称，且==**只在其中使用小写字母和下划线**==。描述性名称可帮助你和别人明白代码想要做什么。==**给模块命名时也应遵循上述约定。**==

2. 每个函数都应包含简要地阐述其功能的**注释**，该注释应紧跟在函数定义后面，并==**采用文档字符串格式**。==

    文档良好的函数让其他程序员只需阅读文档字符串中的描述就能够使用它：他们完全可以相信代码如描述的那样运行；只要知道函数的名称、需要的实参以及返回值的类型，就能在自己的程序中使用它。

3. ==**给形参指定默认值时，等号两边不要有空格**==：

    ```python
    def function_name(parameter_0, parameter_1='default value') 
    ```

    ==**对于函数调用中的关键字实参，也应遵循这种约定。**==

    ```python
    function_name(value_0, parameter_1='value') 
    ```

4. 如果形参很多，导致函数定义的长度超过了79字符，可在函数定义中输入**左括号后按回车键**，并在**下一行按两次Tab键**，从而==**将形参列表和只缩进一层的函数体区分开来**==。

    ```python
    def function_name( 
    		parameter_0, parameter_1, parameter_2, 
    		parameter_3, parameter_4, parameter_5): 
    	function body...
    ```

    

### 9.7 类编写指南

1. 我们通常可以认为**首字母大写的名称（如 Dog）指的是类**，而**小写的名称（如my_dog）指的是根据类创建的实例**。
2. **类名**应采用==**驼峰命名法**==，即将类名中的每个单词的首字母都大写，而**不使用下划线**。**实例名和模块名**都采用小写格式，并在单词之间**加上下划线**。
3. 对于每个类，都应紧跟在类定义后面包含一个**文档字符串**。这种文档字符串简要地描述类的功能，并遵循编写函数的文档字符串时采用的格式约定。每个模块也都应包含一个文档字符串， 对其中的类可用于做什么进行描述。
4. 可使用空行来组织代码，但不要滥用。**在类中，可使用一个空行来分隔方法；而在模块中， 可使用两个空行来分隔类。**
5. 需要**同时导入标准库中的模块和你编写的模块**时，**先编写导入标准库模块**的import语句，再添加一个**空行**，然后编写导入你**自己编写的模块**的import语句。在包含多条import语句的程序中， 这种做法让人更容易明白程序使用的各个模块都来自何方。









## 10、条件判断和循环

### 10.1 条件判断

- 注意事项：比较数字是否相等要用两个等号：`==`

```python
if <条件判断1>:
    <执行1>
elif <条件判断2>:
    <执行2>
elif <条件判断3>:
    <执行3>
else:
    <执行4>
```



### 10.2 循环

- Python提供一个`range()`函数，可以生成一个整数序列，再通过`list()`函数可以转换为list。比如`range(5)`生成的序列是从0开始小于5的整数：

```python
>>> list(range(5))
[0, 1, 2, 3, 4]
```



```python
for ... in ...:
    ...
    
while ... :
    ...
```



### 10.3 break和continue

- 在循环中，`break`语句可以提前退出循环。
- `continue`语句，跳过当前的这次循环，直接开始下一次循环。





## 11、dict字典

- Python内置了字典：dict的支持，dict全称dictionary，在其他语言中也称为map，**使用键-值（key-value）存储**，具有极快的查找速度。

- 假设要根据同学的名字查找对应的成绩，如果用list实现，需要两个list：

```python
names = ['Michael', 'Bob', 'Tracy']
scores = [95, 75, 85]
```

​		给定一个名字，要查找对应的成绩，就先要在names中找到对应的位置，再从scores取出对应的成绩，list越长，耗时越长。



### 11.1 使用字典和访问字典的值

- 如果用dict实现，只需要一个“名字”-“成绩”的对照表，直接根据名字查找成绩，无论这个表有多大，查找速度都不会变慢。用Python写一个dict如下：

```python
>>> d = {'Michael': 95, 'Bob': 75, 'Tracy': 85}
>>> d['Michael']
95
```

- 这种key-value存储方式，**在放进去的时候，必须根据key算出value的存放位置**，这样，取的时候才能根据key直接拿到value。
- **如果key不存在，dict就会报错。**



### 11.2 添加键—值对

- 字典是一种动态结构，可随时在其中添加键—值对。

- 要添加键—值对，可依次指定字典名、用方括号括起的键和相关联的值。、

    ```python
    d['xiaoming'] = 60
    ```

- **注意，键—值对的排列顺序与添加顺序不同。Python不关心键—值对的添加顺序， 而只关心键和值之间的关联关系。**

- key在一个字典中是唯一且不可变的，因此**列表不能作为key。**

- 由于一个key只能对应一个value，所以，多次对一个key放入value，**后面的值会把前面的值冲掉**



### 11.3 删除键—值对

- 使用del语句时， 必须指定字典名和要删除的键。

    ```python
    alien_0 = {'color': 'green', 'points': 5} 
    del alien_0['points']
    ```

- 使用`pop(key)`方法。

    ```python
    point = alien_0.pop('points')
    ```

    

### 11.4 判断key存在的方法

1. 通过`in`判断key是否存在：

```python
>>> 'Thomas' in d
False
```

2. 通过dict提供的`get()`方法，**如果key不存在，可以返回`None`**，或者**自己指定的value**：

```python
>>> d.get('Thomas')
>>> d.get('Thomas', -1)
-1
```

注意：返回`None`的时候Python的交互环境不显示结果。



### 11.5 遍历字典

#### 11.5.1 遍历所有的键—值对

- 使用方法`items()` ，它返回一个键—值对列表。

    ```python
    for key, value in user_0.items(): 
    	print("Key: " + key) 
    	print("Value: " + value) 
    ```



#### 11.5.2 遍历字典中的所有键

- 使用方法`keys()` ，它返回字典中的所有键的列表。

    ```python
    for name in favorite_languages.keys(): 
    	print(name.title()) 
        
    for name in list(favorite_languages.keys()): 
    ```

- 遍历字典时，会默认遍历所有的键，所有也可以不使用方法keys()。

    ```python
    for name in favorite_languages: 
    ```

    

#### 11.5.3 按顺序遍历字典中的所有键

- 可使用函数sorted()来获得按特定顺序排列的键列表的副本

    ```python
    for name in sorted(favorite_languages.keys()): 
    ```

    

#### 11.5.4 遍历字典中的所有值

- 可使用方法values()，它返回一个值列表，而不包含任何键。

    ```python
    for language in favorite_languages.values(): 
     	print(language.title()) 
    ```

- 为剔除重复项，可使用集合（set）。 集合类似于列表，但每个元素都必须是独一无二的

    ```python
    for language in set(favorite_languages.values()): 
    ```

    

### 11.6 dict和list的比较

请务必注意，dict内部存放的顺序和key放入的顺序是没有关系的。



和list比较，dict有以下几个特点：

1. **查找和插入的速度极快**，不会随着key的增加而变慢；
2. 需要**占用大量的内存**，内存浪费多。

而list相反：

1. 查找和插入的时间随着元素的增加而增加；
2. 占用空间小，浪费内存很少。

所以，dict是==用空间来换取时间==的一种方法。



- dict可以用在需要高速查找的很多地方，在Python代码中几乎无处不在，正确使用dict非常重要，需要牢记的第一条就是==dict的key必须是**不可变对象**。==

- 这是因为dict根据key来计算value的存储位置，如果每次计算相同的key得出的结果不同，那dict内部就完全混乱了。

- ==**这个通过key计算位置的算法称为哈希算法（Hash）。**==

    要保证hash的正确性，作为key的对象就不能变。

- 在Python中，字符串、整数等都是不可变的，因此，可以放心地作为key。==**而list是可变的，就不能作为key**==



## 12、set集合

- **set和dict类似，也是一组key的集合，但不存储value。由于key不能重复，所以，在set中，没有重复的key。**





## 13、函数

### 13.1 定义函数

- 关键字 `def` 告诉Python你要定义一个函数，后面为函数名，括号内指出需要向函数传递的信息：

    ```python
    def greet_user(): 
    	"""显示简单的问候语""" 
    	print("Hello!")
    ```

- 紧跟在 `def greet_user():` 后面的所有缩进行构成了函数体。

- **紧跟的第一行的文本是被称为==文档字符串 （docstring）==的注释，描述了函数是做什么的。**

- **文档字符串用三引号括起，Python使用它们来生成有关程序中函数的文档。**



### 13.2 传递实参

#### 13.2.1 实参与形参

```python
def greet_user(username): 
	"""显示简单的问候语"""
	print("Hello, " + username.title() + "!") 
 
greet_user('jesse') 
```

- 在函数 `greet_user()` 的定义中，变量 `username` 是一个**形参**——函数完成其工作所需的一项信息。
- 在代码 `greet_user('jesse')` 中，值 `'jesse'` 是一个**实参**。**实参是调用函数时传递给函数的信息。**
- 我们调用函数时，将要让函数使用的信息放在括号内。



#### 13.2.2 位置实参

- 你调用函数时，Python必须将函数调用中的**每个实参都关联到函数定义中的一个形参**。
- 为此， **最简单的关联方式是基于实参的顺序**。这种关联方式被称为**位置实参**。

- ==使用位置实参来调用函数时，实参的顺序必须与形参的顺序对应。==



#### 13.2.3 关键字实参

- 关键字实参是传递给函数**名称—值对**。
- 你直接在实参中将名称和值关联起来了，因此向函数传递实参时不会混淆。
- ==关键字实参让你无需考虑函数调用中的实参顺序，还清楚地指出了函数调用中各个值的用途。==



#### 13.2.4 默认值

- 编写函数时，可给每个形参指定默认值。
- 在调用函数中给形参提供了实参时，Python将使用 指定的实参值；否则，将使用形参的默认值。
- 因此，给形参指定默认值后，**可在函数调用中省略对应的实参。**
- ==使用默认值可简化函数调用，还可清楚地指出函数的典型用法。==



### 13.3 返回值

- 函数并非总是直接显示输出，相反，它可以处理一些数据，并返回一个或一组值。
- 函数返回的值被称为**返回值**。在函数中，可使用 `return` 语句将值返回到调用函数的代码行。
- ==返回值让你能够将程序的大部分繁重工作移到函数中去完成，从而简化主程序。==



### 13.4 传递任意数量的实参

- 在形参名前加符号 `*` ，可以实现接受任意数量的参数，并将这些参数保存在名为参数名的元组中。

    ```python
    def make_pizza(*toppings): 
     	"""打印顾客点的所有配料""" 
     	print(toppings) 
     
    make_pizza('pepperoni') 
    make_pizza('mushrooms', 'green peppers', 'extra cheese') 
    ```

- 形参名 `*toppings` 中的星号让Python创建一个名为 `toppings` 的空元组，并将收到的所有值都封装到这个**元组**中。



#### 13.4.1 结合位置实参和任意数量实参

- 如果要让函数接受不同类型的实参，必须在函数定义中将接纳任意数量实参的形参放在最后。
- **Python先匹配位置实参和关键字实参，再将余下的实参都收集到最后一个形参中。**



#### 13.4.2 使用任意数量的关键字实参

- 在形参名前加两个星号 `**` ，可以实现接受任意数量的关键字参数，并将这些参数保存在名为参数名的**字典**中。

    ```python
    def build_profile(first, last, **user_info): 
     """创建一个字典，其中包含我们知道的有关用户的一切""" 
     	profile = {} 
    	profile['first_name'] = first 
     	profile['last_name'] = last 
    	for key, value in user_info.items():
            profile[key] = value 
     	return profile 
    ```

- 形参 `**user_info` 中的两个星号让Python创建一个名为 `user_info` 的空字典，并将收到的所有名称—值对都封装到这个字典中。

- 在这个函数中，可以像访问其他字典那样访问user_info中的名称—值对。





## 14、模块

- 将函数存储在被称为模块的独立文件中，再将模块导入到主程序中。
- import语句允许在当前运行的程序文件中使用模块中的代码。
- 通过将函数存储在独立的文件中，可隐藏程序代码的细节，将重点放在程序的高层逻辑上。 
- 这还能让你在众多不同的程序中重用函数。将函数存储在独立文件中后，可与其他程序员共享这些文件而不是整个程序。知道如何导入函数还能让你使用其他程序员编写的函数库。



### 14.1 导入整个模块

- 要让函数是可导入的，得先创建模块。
- 模块是扩展名为.py的文件，包含要导入到程序中的代码。

假设我们有一个模块 `pizza.py` ，其中有一个函数 `make_pizza()` 

- 导入模块：

    ```python
    import pizza
    
    # 调用函数
    pizza.make_pizze()
    ```

- 只要编写一条 `import` 语句，就可在程序中使用该模块中的所有函数。可使用下面的语法：

    ```python
    module_name.function_name()
    ```



### 14.2 导入特定的函数

```python
from module_name import function_name
from module_name import function_0, function_1, function_2
```



### 14.3 使用 as 给函数指定别名

```python
from module_name import function_name as fn
```



### 14.4 使用 as 给模块指定别名

```python
import module_name as mn
```



### 14.5 导入模块中的所有函数

```python
from module_name import *
```

- 不建议这样做，名称冲突时会覆盖函数





## 15、类与对象

Python创建类使用关键字class，并且具备封装、多态和继承的特点。

- **封装：**封装是一个概念，它的含义是把方法、属性、事件集中到一个统一的类中，并对使用者屏蔽其中的细节。
- **继承：**是一种创建类的方法，在现有类（被继承的类）基础上，进行扩展生成新的类，并对使用者屏蔽其中的细节。
- **多态：**一个同样的函数对于不同的对象可以具有不同的实现。

默认情况下，类的属性都是“public”，要是不想被访问和继承，可以对其进行私有化。

- 在**属性或方法**前加**一个**下划线，可以防止作为模块时的导入。
- 在**属性或方法**前加**两个**下划线，可以实现完全私有化。



### 15.1 创建类

```python
class Dog(): 
	"""一次模拟小狗的简单尝试""" 
 
	def __init__(self, name, age): 
		"""初始化属性name和age""" 
		self.name = name 
		self.age = age 
 
	def sit(self): 
		"""模拟小狗被命令时蹲下""" 
		print(self.name.title() + " is now sitting.") 
	def roll_over(self): 
		"""模拟小狗被命令时打滚""" 
		print(self.name.title() + " rolled over!") 
```

1. 方法 `__init__()` 

    **类中的函数称为方法**；你前面学到的有关函数的一切都适用于方法，就目前而言，**唯一重要的差别是调用方法的方式。**

    方法__init__()是一个特殊的方法，每当你根据Dog类创建新实例时，Python都会自动运行它。

    ==**在这个方法的名称中，开头和末尾各有两个下划线，这是一种约定，旨在避免Python默认方法与普通方法发生名称冲突。**==

2. 方法形参 `self` 

    在方法的定义中，形参self必不可少，**且必须位于其他形参的前面。**

    每个与类相关联的方法调用都自动传递实参self，它是一个指向实例本身的引用，**让实例能够访问类中的属性和方法。**

3. **类的属性**：以self为前缀的变量都可供类中的所有方法使用，我们还可以通过类的任何实例来访问这些变量。

    `self.name`



### 15.2 创建类实例

```python
my_dog = Dog('willie', 6)
print(my_dog.name)
my_dog.sit()
```

1. 访问属性

    要访问实例的属性，可使用句点表示法。

2. 调用方法

    用句点



### 15.3 修改属性的值

1. 直接修改属性的值

2. 通过方法修改属性的值

    **通过方法修改属性可以检查修改的值，禁止不合理的修改，更加安全。**



### 15.4 继承

- 一个类继承另一个类时，它将**自动获得另一个类的所有属性和方法**；
- 原有的类称为**父类**， 而新类称为**子类**。
- 子类继承了其父类的所有属性和方法，同时还**可以定义自己的属性和方法**。
- 创建子类时，父类必须包含在当前文件中，且位于子类前面。



#### 15.4.1 子类的方法__init__()

```python
class Car():
 	"""一次模拟汽车的简单尝试"""
 	def __init__(self, make, model, year):
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0
    
class ElectricCar(Car): 
 	"""电动汽车的独特之处""" 
 	def __init__(self, make, model, year): 
 		"""初始化父类的属性""" 
		super().__init__(make, model, year) 
        self.battery_size = 70 
```

- `super()` 是一个特殊函数，帮助Python将父类和子类关联起来。
- 这行代码让Python调用 ElectricCar的父类的方法__init__()，让ElectricCar实例包含父类的所有属性。
- 父类也称为超类（superclass），名称super因此而得名。

#### 15.4.2 给子类定义属性和方法

- ` self.battery_size` 是子类特有的属性

#### 15.4.3 重写父类的方法

- 对于父类的方法，只要它不符合子类模拟的实物的行为，都可对其进行重写。
- 为此，可在子类中定义一个这样的方法，即它与要重写的父类方法同名。
- 这样，Python将不会考虑这个父类方法，而只关注你在子类中定义的相应方法。





## 16、文件读写

Python内置了读写文件的函数：open，返回文件对象

通常的用法需要三个参数: **open(filename, mode, encoding)**。

- filename:	 包含了你要访问的文件名称的字符串值。
- mode:          决定了打开文件的模式   (  **r:只读、w:写入、a:追加; *b: 进制的形式操作**  )。
- encoding:    打开文件的编码格式，**默认为utf8**。

处理图像音频文件是，可以加上b，如rb,wb的形式操作。



### 16.1 从文件中读数据

```python
with open('pi_digits.txt') as file_object: 
 	contents = file_object.read() 
 	print(contents) 
```

- **函数open()** 接受一个参数： 要打开的文件的名称。==**文件可以是相对路径，也可是绝对路径。**==

- **函数open()** 返回一个表示文件的对象。

- **关键字with** 在不再需要访问文件后将其关闭。

    你也可以调用open()和close()来打开和关闭文件，但这样做时，如果程序存在bug，导致close()语句未执行，文件将不会关闭。

- 使用关键字with时，open()返回的文件对象只在with代码块内可用。

#### 16.1.1 read()方法读取整个文件

- ==使用 `read()` 方法==可以读取文件的全部内容，并作为一个长长的字符串存储在变量contents中。

    `contents = file_object.read()`

- 也可以指定参数，指定读取的字符数：

    ```python
    f.read(6) 		#读取6个字符，光标后移6个字符
    ```

#### 16.1.2 逐行读取

```python
filename = 'pi_digits.txt' 
with open(filename) as file_object: 
	for line in file_object: 
 		print(line)
```

- **要以每次一行的方式检查文件，可对文件对象使用for循环。**

#### 16.1.3 readlines()方法创建包含各行内容的列表

- 如果要在with代码块外 访问文件的内容，可在with代码块内将文件的各行存储在一个列表中，并在with代码块外使用该列表。
- ==使用方法 `readlines()`==

```python
filename = 'pi_digits.txt' 

with open(filename) as file_object: 
 	lines = file_object.readlines() 
    
for line in lines: 
	print(line.rstrip())
```

- ==**readlines()从文件中读取每一行，并将其存储在一个列表中。**==



### 16.2 写入文件

- 要将文本写入文件，你在调用open()时需要提供另一个实参，告诉Python你要写入打开的文 件。

```python
filename = 'programming.txt' 
with open(filename, 'w') as file_object: 
	file_object.write("I love programming.") 
```

- 调用open()时提供了两个实参。第一个实参也是要打开的文件的名称； 第二个实参（'w'）告诉Python，我们要以**写入模式**打开这个文件。

- 打开文件时，可指定：
    - ==读取模式（'r'）、写入模式（'w'）、附加模式（'a'）或让你能够读取和写入文件的模式（'r+'）。==
- 如果你省略了模式实参，Python将**以默认的只读模式打开文件**。
- **以写入（'w'）模式打开文件时千万要小心，因为如果指定的文件已经存在，Python将在返回文件对象前清空该文件。**



#### 16.2.1 write()方法写入

- ==使用方法 `write()`==

```python
filename = 'programming.txt' 
with open(filename, 'w') as file_object: 
 	file_object.write("I love programming.\n") 
 	file_object.write("I love creating new games.\n") 
```

#### 16.2.2 附加到文件

```python
filename = 'programming.txt' 
with open(filename, 'a') as file_object: 
	file_object.write("I also love finding meaning in large datasets.\n") 
 	file_object.write("I love creating apps that can run in a browser.\n") 
```



### 16.3 文件编码解码问题

- Windows 平台，Python默认编码是 gbk ，也就是说，当我们用 open() 方法打开一个文件的时候，会默认使用 gbk 编码对这个文件解码。

- 但是，我们的文件是使用 utf-8 编码的，因此有一些中文字符可能会出现无法解码的现象，就会报如下错误：

    ```
    UnicodeDecodeError: ‘gbk’ codec can’t decode byte
    ```

- 也就是说，我们用 gbk 编码无法解码某个字节，要解决这个问题，我们可以添加参数：`encoding='utf-8'`

    ```python
    open(filename, 'r', encoding='utf-8')
    ```

- 这样我们就告诉了Python，我们这个文件是使用 utf-8 编码的，你一会儿解码的时候就用utf-8解码，不要用gbk了。





## 17、异常捕获

**只要程序依赖于外部因素，如用户输入、存在指定的文件、有网络链接，就有可能出现异常。**凭借经验可判 断该在程序的什么地方包含异常处理块，以及出现错误时该向用户提供多少相关的信息。

程序出现问题无法执行时大多分为两种情况：

- 编码错误：代码编写时（运行时）出现错误。
- 异常：在运行时出现错误（比如除数为零、列表的下界越界、修改字符串等）。

```python
# 使用try except 捕获异常
try:
    print(1/0)
except Exception as e:
    print(e)
```

- `try`下面的语句为我们在运行过程中可能会出现错误的语句，我们将可能会出现错误的语句都写在这里
- `except`后面为可能出现的异常，不清楚出现的异常，可以使用`Exception`捕获所有的异常。下面为捕获了异常要执行的语句。
- 在程序运行时，这里即便出现了问题，也**只会捕获到异常**，然后继续执行下面的语句。

### 17.1 处理 ZeroDivisionError 异常

```python
try: 
 	answer = int(first_number) / int(second_number) 
except ZeroDivisionError: 
 	print("You can't divide by 0!") 
else: 
 	print(answer) 
```

### 17.2 处理 FileNotFoundError 异常

```python
filename = 'alice.txt' 

try: 
 	with open(filename) as f_obj: 
 	contents = f_obj.read() 
except FileNotFoundError: 
 	msg = "Sorry, the file " + filename + " does not exist." 
 	print(msg) 
```

### 17.3 失败时一声不吭

```python
try: 
 	--snip-- 
except FileNotFoundError: 
	pass 
else: 
 	--snip--
```



## 18、使用JSON存储数据

- JSON（JavaScript Object Notation）格式最初是为JavaScript开发的，但随后成了一种常见格式，被包括Python在内的众多语言采用。
- 很多程序都要求用户输入某种信息，如让用户存储游戏首选项或提供要可视化的数据。
- 模块json让你能够将简单的Python数据结构转储到文件中，并在程序再次运行时加载该文件中的数据。

### 18.1 使用 json.dump()和 json.load()

- 函数**json.dump()**接受两个实参：**要存储的数据**以及可用于**存储数据的文件对象**。

    ```python
    import json 	# 需要先导入模块json
    
    numbers = [2, 3, 5, 7, 11, 13] 
    
    filename = 'numbers.json' 
    with open(filename, 'w') as f_obj: 
    	json.dump(numbers, f_obj)
    ```

- **json.load()**

    ```python
    with open(filename) as f_obj: 
    	numbers = json.load(f_obj) 
     
    print(numbers)
    ```

    

### 18.2 保存和读取用户生成的数据

```python
import json 
# 如果以前存储了用户名，就加载它
# 否则，就提示用户输入用户名并存储它
filename = 'username.json' 
try: 
	with open(filename) as f_obj: 
	username = json.load(f_obj) 
except FileNotFoundError: 
	username = input("What is your name? ") 
	with open(filename, 'w') as f_obj: 
	json.dump(username, f_obj) 
	print("We'll remember you when you come back, " + username + "!") 
else: 
	print("Welcome back, " + username + "!") 
```



## 19、测试代码

- 编写函数或类时，还可为其编写测试。通过测试，可确定代码面对各种输入都能够按要求的那样工作。
- 测试让你信心满满，深信即便有更多的人使用你的程序，它也能正确地工作。
- 程序员都会犯错，因此每个程序员都必须经常测试其代码， 在用户发现问题前找出它们。

### 19.1 测试函数

#### 19.1.1 单元测试和测试用例

- Python标准库中的模块 `unittest` 提供了代码测试工具。
- **单元测试**用于核实函数的某个方面没有问题；
- **测试用例**是一组单元测试，这些单元测试一起核实函数在各种情形下的行为都符合要求。

- 良好的测试用例考虑到了函数可能收到的各种输入，包含针对所有这些情形的测试。
- **全覆盖式测试**用例包含一整套单元测试，涵盖了各种可能的函数使用方式。对于大型项目，要实现全覆盖可能很难。

#### 19.1.2 可通过的测试

- 要为函数编写测试用例，可先导入模块 `unittest` 以及要测试的函数，再创建一个继承 `unittest.TestCase` 的类，并编写一系列方法对函数行为的不同方面进行测试。

    ```python
    import unittest 
    from name_function import get_formatted_name 
    
    class NamesTestCase(unittest.TestCase): 
     	"""测试name_function.py""" 
     
     	def test_first_last_name(self): 
     		"""能够正确地处理像Janis Joplin这样的姓名吗？""" 
     		formatted_name = get_formatted_name('janis', 'joplin') 
     		self.assertEqual(formatted_name, 'Janis Joplin') 
            
    unittest.main()
    ```

- 你可随便给这个类命名，但最好让它看起来与要测试的函数相关，并包含字样Test。

- 这个类必须继承 unittest.TestCase类，这样Python才知道如何运行你编写的测试。

- 我们使用了unittest类最有用的功能之一：**一个断言方法**。断言方法用来核实得到 的结果是否与期望的结果一致。

    `self.assertEqual()`

- 测试通过的情况：

    ```python
    . 
    ---------------------------------------------------------------------- 
    Ran 1 test in 0.000s 
    OK
    ```

    第1行的句点表明有一个测试通过了。

#### 19.1.3 不能通过的测试

```python
E 
====================================================================== 
ERROR: test_first_last_name (__main__.NamesTestCase) 
---------------------------------------------------------------------- 
Traceback (most recent call last): 
 	File "test_name_function.py", line 8, in test_first_last_name 
 		formatted_name = get_formatted_name('janis', 'joplin') 
TypeError: get_formatted_name() missing 1 required positional argument: 'last' 
---------------------------------------------------------------------- 
Ran 1 test in 0.000s 
FAILED (errors=1) 
```

- 第1行输出只 有一个字母E，它指出测试用例中有一个单元测试导致了错误。

- 最后一句指出整个测试用例都未通过，因为运行该测试用例时发生了一个错误

#### 19.1.4 添加新测试

```python
class NamesTestCase(unittest.TestCase): 
 	"""测试name_function.py """ 
    --snip--
    
    def test_first_last_middle_name(self): 
        ...
```

- 直接在类内添加一个方法。



### 19.2 测试类

#### 19.2.1 各种断言方法

- Python在unittest.TestCase类中提供了很多断言方法。

    |          方 法          |       用 途        |
    | :---------------------: | :----------------: |
    |    assertEqual(a, b)    |     核实a == b     |
    |  assertNotEqual(a, b)   |     核实a != b     |
    |      assertTrue(x)      |    核实x为True     |
    |     assertFalse(x)      |    核实x为False    |
    |  assertIn(item, list)   |  核实item在list中  |
    | assertNotIn(item, list) | 核实item不在list中 |

#### 19.2.2 方法 setUp()

- unittest.TestCase类包含方法 `setUp()` ，让我们只需创建这些对象一 次，并在每个测试方法中使用它们。
- 如果你在TestCase类中包含了方法setUp()，**Python将先运行它，再运行各个以test_打头的方法。**这样，在你编写的每个测试方法中都可使用在方法setUp() 中创建的对象了。









## 常用工具库

Python中的工具库可分为两种：

- 标准库：安装Python后可以直接使用的。如：os,sys,time等模块。
- 第三方库：需要安装以后才可以使用的库，如NumPy（用于科学计算）、pandas（用于数据处理）、scikit-learn（机器学习库）

### sys模块

sys模块主要负责程序与Python解释器的交互，提供了一列的函数和变量，用于操纵Python运行时的环境。

```python
import sys
# sys.exit([n]): 此方法可以是当前程序退出，n为0时表示正常退出，其他值表示异常退出
sys.exit(0)
# sys.path: 获取模块搜索路径
sys.path
# sys.platform: 获取当前系统平台
sys.platform
```



### os模块

**os模块负责程序与操作系统的交互，提供了访问操作系统底层的接口。**

```python
import os
# os.getpid() 获取当前进程id
os.getpid()
# os.getppid() 获取当前父进程id
os.getppid()
# os.getcwd() 获取当前所在路径
cwd = os.getcwd()
# os.chdir(path) 改变当前工作目录
os.chdir("C:\\")
# os.listdir() 返回目录下所有文件
os.listdir(cwd)
# os.walk() 输出当前路径下所有文件
for root,dirs,files in os.walk(cwd,topdown=False):
    for name in files:
        print(os.path.join(root,name))		#打印当前路径下所有文件
    for name in dirs:
        print(os.path.join(root,name))		#打印当前路径下所有文件夹
# root 是根目录，dirs 是当前所有的文件夹，files 是当前所有的文件
# os.path.join() 是用于路径拼接的方法
```

`os.path`模块，主要用于**获取文件的属性**

```python
# os.path 模块：主要用于获取文件的属性
# os.path.abspath(path)：返回绝对路径
os.path.abspath("text.txt")
# os.path.exists(path)：文件存在返回True，不存在返回False
os.path.exists("text.txt")
# os.path.getsize(path)：返回文件的大小，如果文件不存在返回错误
os.path.getsize("text.txt")
# os.path.isfile(path)：判断路径是否为文件
print("text.txt是否为文件：",os.path.isfile("text.txt"))
# os.path.isdir(path)：判断路径是否为文件夹
print("text.txt是否为文件夹：",os.path.isdir("text.txt"))
```



### time模块

time模块时Python中处理时间的一个重要模块，包好了许多与时间操作相关的方法。

主要：处理日期用另外一个模块：datetime

```python
import time
# time.time()：获取当今时间戳
time_now = time.time()
# time.localtime()：获取时间元组
localtime = time.localtime(time_now)
# time.asctime()：获取格式化的时间
localtime = time.asctime(localtime)
# time.strftime(format[, t])：接受时间元组，并返回可读字符串表示的当地时间，格式由参数format决定。
print(time.strftime("$Y-%m-%d %H:%M:%S", time.localtime()))
```

