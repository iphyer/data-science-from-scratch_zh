# Chapter 2 Python快速入门课程
> 让我难以置信的是，25 年过去了，人们依旧为 Python 痴狂。

> Michael Palin

所有 DataSciencester 的新员工都被要求参加新员工的入职培训会，在入职培训会上最有意思的部分就是会有一个关于 Python 的快速入门课程。

这并不是一个无所不包的 Python 教程，但是这门课程将会重点讲授那些 DataSciencester 数据科学家们最常使用的知识点( 一部分知识点恰恰是通常的 Python 入门课程不怎么关注的。)。

## 基础知识

### 获取 Python

你可以直接从 [Python.org](https://www.python.org/) 下载 Python。 但是如果你的机器上还有 Python， 我特别推荐你直接安装 [Anaconda](https://store.continuum.io/cshop/anaconda/) 这个 Python 发行版, 因为 Anaconda 几乎已经包括了所有你可能在数据科学中用到的 Python 包。

在我写作本书的时候，最新的 Python 版本已经升级到了 3.4 。但是在 DataSciencester 我们使用更加可靠的老版本， Python 2.7 。 Python 3 并不向后兼容 Python 2 而很多重要的软件包只能在 Python 2.7 下工作。 数据科学社区依然坚守在 Python 2.7 的版本上，这也意味着我们不得不遵守这个传统。 请确保你已经安装了正确的 Python 版本。

如果你不能安装 Anaconda，请一定要安装`pip` 这个软件包， `pip` 是让你可以轻松安装第三方软件包，特别是有些我们必须的第三方软件包的 Python 包管理程序。 `pip` 也可以和 IPython很好的集合在一起工作，`IPython`是一个相当易用方便的 Python 交互式解释器。

( 如果你安装了 Anaconda 那么 `pip` 和 `IPython` 应该已经自动安装了。)

```bash
 pip install ipython
```
如果出现了任何奇怪晦涩的错误信息，请直接搜索网络，那儿肯定有很多好的解决方法。

### Python 之禅

Python 是一门有着自己独特设计理念的语言，这些设计理念通过 Python 之禅这个框架来解释，你可以在 Python 的交互解释器中通过输入 `import this` 来查看。

人们最长讨论和提到的是如下几句：

> ( 任何问题)应该有一个解决方法，也只有一个最好的解决方案，请使用最显然直接的方法实现它。

> (英文原版：There should be one-- and preferably only one --obvious way to do it.)
按照最直接的方式( 虽然对于初学者可能并不是那么直接。)写下的代码通常被认为是符合 Python 惯用法( Pythonic )的代码。虽然这本书并不是一本单纯的关于 Python 的书，但是只有偶然的几次我们会违背 Python 惯用法也就是我们使用非 Python 惯用法 的方式来实现可以用 Python 惯用法 完成的目标，大多数情况下我们倾向使用符合 Python 惯用法的方法解决问题。

### 空格格式

许多语言习惯使用花括号来表示程序块的起始与结束。但是 Python 使用缩进，比如：
```python
for i in [1,2,3,    4,5]:
      print    i                    #    对 i 做循环
      for j in [1,    2,3,4,5]:
          print j                   #    对 j 做循环
          print i + j               #    对 j 做循环的最后一行代码
      print    i                    #    对 i 做循环的最后一行代码
print    "done looping"
```
这种缩进的方式让 Python 的代码非常具有可读性，当然这也要求你对于代码的格式非常小心。对于非常长的多行计算公式而言，一个非常有用的 Python 特性是， Python会自动忽略在圆括号和花括号之间的空格，比如：
```python
long_winded_computation = (1 + 2 + 3 + 4 + 5 + 6 +7 + 8 + 9 + 10 + 11 + 12 +
                          13 + 14 + 15 + 16 + 17 + 18 + 19 + 20 )
```
利用这个特性你可以写出更加容易阅读的代码，比如：
```python
list_of_list = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]

easier_to_read_list_lists = [[1, 2, 3],
                             [4, 5, 6],
                             [7, 8, 9] ]
```
你也可以用反斜线来提示语句会延续到下一行，虽然我们很少这样做：
```python
two_plus_three = 2 + \
                 3
```
使用空格格式的一个结果就是我们不能够像在其他语言中那样，简单地在 Python 交互解释器中复制或者粘贴代码。比如，如果你想粘贴如下的代码到 Python 交互解释器中：
```python
for i in [1, 2, 3, 4, 5]:

#注意上方的空格
print i
```
你可能会得到如下的提示信息:
> 译者注，这里需要特别注意输入代码的格式区别。 具体详情请见 [Github Issue Report#11](https://github.com/joelgrus/data-science-from-scratch/issues/11)。

```python
IndentationError: unexpected indent
```
因为交互解释器认为空行代表了`for`循环的结束。

当然如果利用`Ipython`的话就可以体验`Ipython`自带的 `%paste`函数，`%paste`函数可以正确的系统剪贴板上的任意内容到交互解释器中，包括空格和其他格式。单单这点就值得你使用`Ipython`来编辑你的 Python 代码。

### 模块

有些功能 Python 并不默认载入。这些功能既包括 Python 自带的一部分功能也包括你自行下载的第三方软件包。为了使用这些功能你需要首先用 `import` 命令导入包含这些功能的模块。

一个简单的方法是直接导入模块本身，比如：

```python
import re
my_regex = re.compile("[0-9]+",re.I)
```
这里的 `re` 就是包括了正则表达式功能的模块。通过直接使用`import` 命令导入相应的包之后，你就可以通过在模块包含的函数或者方法之前加上该模块名作为前缀比如`re`来使用他们了。

如果 `re` 在你的程序中已经被占用了的话，你就可以如下的方法来引入 `re` 模块。

```python
import re as regex
my_regex = regex.compile("[0-9]+",re.I)
```
通常在你的模块名比较难以记住或者需要输入很多字符的时候，你会使用上面的第二种方法导入特定的模块。比如，当我们使用 `matplotlib` 可视化数据的时候，通常我们这样导入需要的模块：

```python
import matplotlib.pyplot as plt
```
如果你只是需要某个模块的特定功能，你就可以直接导入这些功能然后不需要在这些功能前面加上前缀，比如：
```python
from collections import defaultdict, Counter
lookup = defaultdict(int)
my_counter = Counter()
```
如果你喜欢做些破坏，你可以将某个模块的所有内容导入到 Python 的命名空间，这很有可能覆盖你已经定义的某些变量名，比如：
```python
match = 10
from re import *  #注意，re 模块含有 match 函数
print match         #“<function re.match>”
```
当然因为你不是个破坏狂，所以你是不会这么做的，对吧？

###算数运算

Python 2.7 默认使用整数除法，因为 `5 / 2` 的结果是 `2` 。 但是，大多数情况下这不是你希望的得到的结果，因此我们总会在我们的程序文件的开头使用如下语句：
```python
from __future__ import division
```
这样 `5/2` 的结果就是 `2.5` 。 这本书的所有程序都使用这种形式的除法。只有极个别的例子，当我们需要整数除法的时候，我们可以通过使用双反斜杠来得打整数除法，比如 `5 // 2`。

### 函数

函数简而言之就是一种规则，这种规则对于零个或者多个输入进行处理并给出一个相应的输出。 在 Python 中，我们使用关键字 `def`来定义函数，比如：
```python
def double(x):
     '''这里通常会协商函数的说明文档,文档一般会解释函数的功能.
     比如对于这个函数而言，我们会写上：    这个函数将把输入都乘以2作为输出'''
     return x * 2
```
在 Python 中函数是一级（First-class）公民，这也就是意味着你可以像对待参数一样自由地把函数赋值给变量或者将函数传递给函数，比如：
```python
def apply_to_one(f):
       '''该函数将自动把 1 作为函数的参数'''
      return f(1)

my_double = double         #调用前面定义的函数
x = apply_to_one(my_double) #结果为2
```

同样 Python 允许你非常方便的定义Lambda表达式，比如：
```python
y = apply_to_one(lambda x : x+4) #结果是5
```
你也可以把 `lambds`表达式赋值给变量，尽管很多人会告诉你你应该使用`def`定义函数的方法来代替：
```python
another_double =lambda x : 2 * x   #最好不要这样
def another_double(x): return 2 *x #推荐这样
```
函数的参数也可以事先赋值，只有在你不希望出现默认值的时候这个方法才需要特别注意。

```python
def my_print(message = "my default message"):
    print message

my_print("hello") #输出 "hello"
my_print()        #输出 "my default message"
```

有时候通过参数名来确定特定参数也是非常有用的，比如：
```python
def subtract(a = 0 , b = 0):
     return a - b
subtract(10,5) #输出是5
subtract(0,5)  #输出是-5
subtract(b=5)  #输出是-5
```
在这本书里我们可能需要自己编写很多的函数，做好准备！

### 字符串

字符串的内容会被单引号或者双引号括起来，当然在这里你的单引号或者双引号必须配对。

```python
single_quoted_string = 'data science'
double_quoted_string = 'data science'
```
Python 通过反斜杠来表示特殊字符，比如:
```python
tab_string = "\t" #代表制表符
len(tab_string) 　 #输出结果是１
```
如果你就是希望使用反斜杠(　比如在　Windows　操作系统中表示路径或者在正则表达式中　)，你可以通过`r`使用　`raw`　字符串:
```python
not_tab_string = r"\t" #表示　"\" 和 "t"
len(not_tab_string)    #输出结果是２
```

你也可以通过使用三重引号来建立多行字符串：
```python
 multi_line_string= """THis is the first line
 and this is the second line
and this is the third line"""
```
### 异常

当程序发生错误的时候，　Python　会捕获并处理异常。如果不处理，这些异常会导致程序崩溃。你可以通过使用`try`和`except`来处理异常：
```python
try:
     print 0 / 0
except ZeroDivisionError:
  　print "can not divied by zero"
```
虽然在很多其他语言中异常被认为是编程的错误，但是在 Python 的世界中通过异常来使得程序更加整洁是没什么不好意思的，在这本书中，我们有时候也会使用异常。

### 列表

可能在 Python　中最基本的数据结构就是列表list了。列表简而言之就是一个有序的集合(在其他语言中列表可能被成为数组，但是　Python　中的列表更多了一些附加的功能。)

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

```python
```

