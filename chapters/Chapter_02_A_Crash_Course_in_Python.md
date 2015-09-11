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

可能在 Python　中最基本的数据结构就是列表`list`了。列表简而言之就是一个有序的集合(在其他语言中列表可能被成为数组，但是　Python　中的列表更多了一些附加的功能。)

```python
integer_list = [1, 2, 3]
heterogeneous_list = ["string", 0.1, True]
list_of_lists = [integer_list, heterogeneous_list, [] ]

list_length= len(integer_list) #结果是３
list_sum= sum(integer_list)　　　 #结果是6
```
你可以通过方括号来取得或者设置列表中某个特定位置元素的值：
```python
x =  range(10)      # 建立[0,1,2...9]的新列表
zero = x[0]　　　　 #　结果是0,列表序号是从0开始的
one = x[1]　　　　  #　结果是１
nine = x[-1]　　　  #　结果是9，更加符合 Python 惯用法的引用最后一个列表元素的方法
eight = x[-2]　　   #　结果是8, 更加符合 Python 惯用法的引用倒数第二个列表元素的方法
x[0] = -1　　　　   #　现在x列表的结果是[-1,1,2...9]
```
你也可以通过方括号来对于列表进行切片操作：
```python
first_three=x[:3]  #[-1,1,2]
three_to_end=x[3:] #[3,4,...,9]
one_to_four=x[1:5] #[1,2,3,4]
last_three=x[-3:]  #[7,8,9]
ithout_first_and_last=x[1:-1] #[1,2,...,8]
copy_of_x = x[:]  #[-1,1,2,...,9]
```
Python 有`in`操作符来帮助你检查某个元素是不是在列表中
```python
1 in [1,2,3]  #真
0 in [1,2,3]  #假
```
需要注意的是`in`操作符的检查挨个检查列表中的元素，所以除非你知道你的列表很短否则你不应该使用它。(或者你不是那么在乎时间的时候。)

可以很容易地把两个列表拼接在一起：

```python
x = [1,2,3]
x.extend[4,5,6] #现在x为[1,2,3,4,5,6]
```

如果你不希望修改x，你可以使用列表加法：

```python
x=[1,2,3]
y=x+[4,5,6] #现在y为[1,2,3,4,5,6],而x没有改变
```
更经常出现的情况是，我们需要一次添加一个元素进列表：

```python
x=[1,2,3]
x.append(0) #现在x是[1,2,3,0]
y=x[-1]     #结果是0
z=len(x)    #结果是４
```

如果你知道列表有多少元素，我们就可以很容易的分叉整个列表：

```python
x,y = [1,2] #现在ｘ是１，y是２
```
当然如果你在等号两边没有同样数目的元素，那么你会得到一个`ValueError`的报错信息。

经常我们也会通过使用下划线来扔掉那些我们不需要的元素：
```python
_,y = [1,2] #现在ｙ是２，当然我们并不关心第一个元素
```

### 元组

元组是不可的列表。很多你可以在列表上做的事情在元组上没办法实现。你可以用括号(或不加任何标记)来表示元组，而不是在列表形式中的方括号:
```python
my_list = [1,2]
my_tuple = (1,2)
other_tuple = 3,4
my_list[1] = 3 #现在列表是[ 1, 3 ]

try:
     my_tuple[1] = 3
except TypeError:
     print "can not modify a tuple"
```

元组是从函数返回多个值的方法，比如:

```python
def sum_and_product(x,y):
    return (x+y),(x * y)

sp = sum_and_product(2, 3)  #结果是元组(5,6)
s,p = sum_and_product(5,10) #s值为 15, p值为 50
```
元组和列表也都可以用来赋多个值。

```python
x,y = 1,2
x,y = y,x #Pythonic规范的交换x,y的方法
```
### 字典

字典是另一种非常重要的基本数据类型。字典将键和值联系在一起，所以字典允许你可以快速地依照特定的键值得到值。

```python
 empty_dict = {}  #Pythonic
 empty_dict2 = dict() #less Pythonic
 grades = {"Joel" : 80,"Tim": 95}
```

你可以使用方括号来通过一个键获得相应的值。

```python
 joel_grade = grades["Joel"]
```

当然如果你使用字典中不存在的键，则会得到一个`KeyError`：
```python
try:
　  kates_grad = grades["Kate"]
except KeyError:
     print "no grad for Kate!"
```
你可以使用`in`方法来检查一个键是否存在。

```python
joel_has_grade = "Joel" in grades #True
kate_has_grade = "Kate" in grades #False
```
当你使用`get`方法的时候，如果你查找的键不在字典中，则会返回默认值而不是抛出错误。
```python
joel_grade =  grades.get( "joel" ,0 ) #结果是80
kates_grade=grades.get( "Kate" ,0 )   #结果是　０
no_ones_grade = grades.get("No One")  #给出默认值　None
```
同样的，你可以使用方括号给键值对赋值。

```python
grades["Tim"] = 99
grades["Kate"] = 100
num_students = len(grades)
```
我们经常使用字典来表示结构化的数据，比如:

```python
tweet = {
"users" : "Joelgrus",
"text"  : "Data Science is Awesome",
"retweet_count" : 100,
"hashtags" : ["#data","science","#datascience","#awesome","#yolo"]
}
```
除了可以查看特定的键值我们还可以查看所有的键值，比如:

```python
tweet_keys = tweet.keys()  #键列表
tweet_values = tweet.values()　#值列表
tweet_items = tweet.items() #(键，值)元组列表

"user" in tweet_keys ＃真，但是使用更短的列表更好
"user" in tweet      # 更加符合Pythonic的方式，使用更快的方法
"joelgrus" in tweet  #真

```

字典的键是不可以更改的。值得注意的是，`lists`是不可以作为键的。如果你需要使用多组成的键，你可以使用元组或者想办法把键转化成一个字符串来使用字典结构。

#### defaultdict

假设你正在考虑统计一个文档的单词数目，一个显然的方法是使用字典结构，键代表单词，值代表单词出现的次数。这样你就可以通过读取每一个单词增加该单词的出现次数或者对于新出现的单词增加一个新的键，具体实现如下:

```python

word_counts = {}
for word in document:
    if word in word_counts:
        word_counts[word] + = 1
    else:
        word_counts[word] = 1


```

当然你也可以使用" Forgiveness is better than Permission(异常处理比强制要求更好)"的原则来处理查找一个不存在的键的异常情况,比如：

```python

word_counts = {}

for word in document :
    try:
        word_counts[word] + = 1
    except KeyError:
        word_counts[word] = 1

```　

第三种方法就是使用`get`方法，这个可以更加优雅的处理缺失的键值:

```python

word_counts = {}

for word in document:
    previous_count = word_counts.get(word,0)
    word_counts[word] = previous_count + 1

```

任何看到这几种方法的人都会觉得这些方法有点别扭，就是为什么`defaultdict`非常有用的原因。`defaultdict`看起来就像Python自带的字典结构，但是当你尝试查找一个字典中不存在的键的时候两者表现出极大的不同，`defaultdict`会尝试使用添加这个本来不存在的键并使用你预先设定的零值函数来设置该键对应的值。为了使用`defaultdict`你必须首先从`collections`包中引入它:

```python

from collections import defaultdict

word_counts = defaultdict(int) #int() 产生 0

for word in document:
    word_counts[word] += 1

```

`defaultdict`也可以很方便的和`list`或者`dict`甚至其他函数整合在一起:

```python

dd_list = defaultdict(list) #产生空列表
dd_list[2].append(1)        #现在dd_list变成{2:[1]}

dd_dict = defaultdict(dict) ＃产生空字典
dd_dict["Joel"]["City"] = "Seattle" #{"Joel":{"City" : "Seattle"}}

dd_pair = defaultdict(lambda: [0,0]) 
dd_pair[2][1] = 1 #现在dd_pair是{2:[0,1]}

```

这种方法在我们搜集相应的键和值的时候特别有用，因为我们可以不必每次都检查当前键是不是存在。

### Counter

`Counter`将一个序列值转换成类似`defaultdict`的键值结构来统计对象出现的次数，我们一般使用这个结构来建立柱状图:

```python

form collections import Counter

c = Counter([0, 1, 2, 0]) ＃c　现在变成 {0 : 2, 1 : 1, 2 : 1}


```

这让我们可以非常轻松地解决单词统计问题:

```python

word_counts = Counter(document)

```

一个`Counter`对象最经常使用的方法是`most_common`:

```python

#输出前10个出现最多的单词和相应的频率

for word,count in word_counts.most_common(10):
    print word,count

```

###集合

下一个数据结构是集合(set)，集合由一系列不同元素组成：

```python

s = set() #创建空集合
s.add(1)  #现在集合为( 1 )
s.add(2)  #现在集合为( 1 2 )
s.add(2)  #现在集合依然是( 1 2 )
x = len(s) #结果是2
y = 2 in s #结果是True
z = 3 in s #结果是False
```

我们主要因为以下两个原因使用`sets`，首先集合的`in`操作非常快。比如如果我们希望测试很多项目是不是在某个集合中，集合数据结构比列表更加合适：

```python

stopwords_list = ["a", "an", "at"]+hundreds_of_other_words +["yet", "you"]

"zip " in stopwords_list #假，但比较慢

stopwords_set = set(stopwords_list)

"zip" in stopwords_set #快

```

第二个原因是找出一个集合的不同元素：

```python

item_list = [1, 2, 3, 1, 2, 3]
num_items = len(item_list) #结果是6
item_set = set(item_list)　#结果是{1, 2, 3}
num_distinct_items =len(item_set)  #结果是3
distinct_item_list = list(item_set) #结果是[1, 2, 3]
```

但是综合而言，相对于字典和列表我们不是很经常地使用集合。

###流程控制

Python和其他语言类似，你可以使用`if`关键字来根据不同的条件进行不同的操作：

```python

if 1 > 2:
    message = "if only 1 were greater than two..."
elif 1 > 3:
    message = "elif stands for 'else if'"
else:
    message = "when all else fails use else (if you want to)"
    
```

你当然也可以把if-then-else结构利用三元操作符写在一行，我们有时也会采用这个方法：

```python

parity = "even" if x % 2 == 0 else "odd"

```

Python也有`while`循环：

```python
x = 0

while x < 10:
    print x,"is less than 10"
    x += 1

```

虽然我们更经常使用`for`和`in`来做循环操作:

```python

for x in range(10):
    print x,"is less than 10"

```

如果你想实现更加复杂的控制罗辑，你需要使用`continue`和`break`关键字:

```python

for x in range(10):
    if x == 3 :
        continue #立刻进入下一个循环
    if x == 5 :
        break    #结束整个循环
    print x

```

上面的代码将打印出0, 1, 2, 和 4。

###真值

布尔值在Python中和其他语言并没有什么不同，除了它们需要大写开头字母：

```python

one_is_less_than two = 1 < 2 #真
true_equals_false = True == False  #假

```

Python　使用`None`来指示并不存在的值，这和其他语言的`null`类似:

```python

x = None
print x == None #结果是True,但是这种方法并不 Pythonic
print x is None #结果是真，符合 Pythonic

```

Python 允许你在需要使用布尔值的时候使用任何的值。下面的都可以代表假:

* False
* None
* [] (空列表)
* {} (空字典)
* ""
* set()
* 0
* 0.0

相应地，没有列出的值都可以作为真值。这让你可以非常方便地使用`if`关键字来判断空列表，空字符串，空字典。这个特性也会引起一些特别的问题,比如你下面的代码:

```python

s =  some_function_that_returns_a_string()

if s:
    first_char = s[0]
else:
    first_char = ""

```

更加简单的方法是:

```python

first_char = s and s[0]

```

这是因为`and`会返回第二个值如果第一个值为真的时候，当第一个值非真的时候返回第一个值。类似地，如果x可能是一个数字或者空值(None):

```python

safe_x = x and 0

```

这一定会返回返回一个数字。

Python 也有一个`all`函数，`all`函数接收一个列表当每一个元素都为真的时候返回`True`; `any`函数则会在至少有一个元素为真的时候返回`True`:

```python

all([True, 1, { 3 }])  #结果为真
all([True, 1, {}])     #结果为假，因为{}代表空字典为假
any([True, 1, {}])     #结果为真
all([])                #结果为真，因为列表中没有假元素
any([])                #结果为假，因为列表中没有真元素

```

##高级部分

下面我们将看一些在处理数据的时候非常有用的Python高级特性。

###排序

每一个Python列表都有`sort`方法来实现排序功能。如果你不希望弄乱原来的数据顺序，你可以使用`sorted`函数，这会产生一个新的列表:

```python

x = [4, 1, 2, 3]
y = sorted(x)   #结果是[1, 2, 3, 4]，x没有改变
x.sort()        #现在x变成[1, 2, 3, 4]

```
默认情况下，`sort`和`sorted`按照从小到大的顺序简单地比较每个值的大小来排序。

如果你想从大到小排序，你可以指明`reverse`参数为`True`。同时你也可以通过指定特定的比较关键字`key`来实现更加复杂的函数结果比较:

```python

#从大到小按照绝对值大小排序
x = sorted([-4, 1, -2, 3], key = abs, reverse = True) #结果是[-4, 3, -2, 1]

#对于word和count从大到小排序

wc = sorted(word_counts.item(),
            key = lambda (word,count) : count,
            reverse = True)

```
###列表推导式(List Comprehensions也有翻译成列表生成式)

经常地我们需要把一个列表转换成另外一个列表，可能是选中的特定元素也可能是对于原始元素做一定的转化或者两者都有。列表推导式是实现这个目标更加Pythonic的方法:

```python

even_numbers = [x for x in range(5) if x % 2 == 0] #结果是[0, 2, 4]
squares      = [x * x for x in range(5)]           #结果是[0, 1, 4, 9, 16]
even_squares = [x * x for x in even_numbers]       #结果是[0, 4, 16]

```

你也可以相应的把列表转换成字典或者集合：

```python

square_dict = {x : x * x for x in range(5) } #结果是{ 0:0, 1:1, 2:4, 3:9, 4:16 }
square_set  = {x * x for x in [1,-1] }       #结果是{ 1 }

```
如果你不需要列表中的某个值，可以使用下划线去除相应的元素：

```python

zeros = [ 0 for _in even_numbers ] #和even_numbers有一样的长度

```

列表推导式也可以包含多个`for`循环:

```python

pairs = [(x, y)
        for x in range(10)
        for y in range(10)] #结果是100对(0,0), (0,1), ... (9,8),(9,9)

```
同时后面的`for`可以使用前一个`for`的结果：

```python

increasing_pairs = [(x, y)                       #只包括x<y的元组
                   for x in range(10)　　　　　　#range(low,high)为[low,low+1,...high-1]
                   for y in range(x+1,10)] 

```
我们经常需要使用列表推导式。


###生成器和迭代器

列表的一个问题在于它们常常会变得非常大。比如`range(1000000)`就会创建一个一百万个元素的列表。如果你必须一个元素一个元素地处理那将会非常没有效率或者超过内存限制。特别是如果你只是需要前几个值，那么计算所有值是一种巨大的浪费。

生成器`generator`可以让你遍历所有的元素(类似`for`)但是只在必须地时候生成值。


使用生成器的一个方法是使用函数和`yield`操作符：

```python

def lazy_range(n):
    """一个偷懒版本的range函数"""
    i = 0
    while i < n:
        yield i
        i += 1

```

下面的循环可以不断使用`yield`产生的值进行操作知道全部结束:

```python

for i in lazy_range(10):
    do_something_with(i)

```

这样意味着你甚至可以创建一个无限序列:

```python

def natural_number():
    """返回1, 2, 3,..."""
    n = 1
    while True:
        yield n
        n += 1

```

当然你应该指定一个方法来结束上述循环。

第二种使用生成器的方法就是使用括号中`for`循环推导式：

```python

lazy_even_below_20 = (i for i in lazy_range(20) if i % 2 == 0)

```

回忆下，我们知道字典有`items()`方法可以返回一个键值对列表。更经常出现的情况是我们使用`iteritems()`方法，因为这个方法可以让我们在遍历的时候一次只输出一个键值对。


###随机数

学习数据科学的时候，我们经常需要产生随机数，这可以使用`random`模块轻松实现:

```python

import random

four_uniform_randoms = [random.random() for _ in range(4)]

#random.random()产生0到1之间的随机数

```

事实上，`random`模块产生的是伪随机数，这也意味着你可以通过设置`random.seed`得到可以重复的随机数序列:

```python

random.seed(10)
print random.random()
random.seed(10)
print random.random() #两次产生相同的随机数

```

有时我们也会使用`random.randrange`来接受一个或者两个参数，同时随机产生相应范围中的一个随机数:

```python

random.randrange(10) #随机从range(10) = [1, 2, ... 9] 中挑选随机数
random.randrange(3,6)#随机从range(3,6) = [3, 4, 5]中挑选随机数

```

我们有时也会发现一些其他的简便方法，比如`random.shuffle`将列表中元素随机重新排序:

```python

up_to_tem = range(10)
random.shuffle(up_to_tem)
print up_to_tem

```

如果你需要随机地从一个列表中挑选出一个元素，使用`random.choice`:

```python

my_best_friend = random.choice(["Alice", "Bob", "Charlie"])

```

如果你需要对于列表中的元素进行一次无放回的抽样(这样不会出现同一个元素被抽样两次),你可以使用`random.sample`:

```python

lottery_number = range(60)
winning_number = random.sample(lottery_number,6)

```

如果是有放回的抽样的话，你可以多次调用`random.choice`方法：

```python

four_with_replacement = [random.choice(range(10))
                        for _ in range(4)]

```

###正则表达式

正则表达式提供了一种非常有用的检索文本的方法，但是正则表达式相应的也很复杂有不少书讨论它。我们将会在我们偶有的几次遇到它们的时候解释它们，这里给一个我们将在Python中使用正则表达式的例子:

```python

import re

print all([
    not re.match("a", "cat"),
    re.search("a", "cat"),
    not re.search("c", "dog"),
    3 == len(re.split("[ab]", carbs"")),
    "R-D-" == re.sub("[0-9]","-","R2D2")])

#输出为True

```

###面向对象编程

和许多语言类似，Python允许使用`classes`来封装数据和对应的函数方法。我们有时也会使用这个方法来使得我们的代码更加整洁和简单。或许下面这个详细注释的例子可以帮助你更好的理解面向对象编程的概念。


想象一下，如果没有 Python　内置的 `set`　结构，然后我们需要自己实现我们的 Set 类。

我们的Set类需要有什么样的行为? 对于一个　Set　的实例，我们需要可以添加元素，移除元素，检查是否已经包含某个特定元素。我们可以通过成员函数实现所有这些行为，也就是我们就可以通过点操作符对于一个 Set 对象使用这些方法:


```python

#依照传统，我们给类一个驼峰式命名

class Set:
    #对于每一个成员数
    #第一个参数都需要是self
    #self指示了该成员函数相应的Set对象

    def __init__(self, values=None):
        """这是构造函数，当你创建一个新的Set实例的将调用该方法
        你可以这样使用:
        s1 = Set()
        s2 = Set([1,2,3,4])
        """
        self.dict = {} # Set中的每一个元素都有自己的字典属性，这样方便我们查找

        if values is not None:
            for value in values:
                self.add(value)

    def __repr__(self):
        """
        这是Set对象的字符串表示，如果你在Python解释器或者将Set对象传递给str()方法的使用调用
        """
        return "Set: "+ str(self.dict.keys())

    #我们让元素在self.dict成为键，值统一令为True
    def add(self, value):
        self.dict[value] = True

    #value在Set中如果已经含有相应的键在字典中
    def contains(self, value):
        return value in self.dict

    def remove(self, value):
        del self.dict[value]

```

这样我们就可以使用如下方法调用相应的数据结构:

```python

s = Set([1,2,3])
s.add(4)
print s.contains(4)
s.remove(3)
print s.contains(3)

```

###函数式工具

在函数的传递中，有的时候我们需要通过函数来创建新的函数，作为一个简单的例子，我们使用如下的两个参数的函数:

```python

def exp(base, power):
    return base ** power

```

现在如果我们想基于上述函数创建以2为底的指数函数，我们可以当然可以`def`关键字，但是这种方法有点不太优雅:

```python

def two_to_the(power):
    return exp(2,power)

```

一个不一样的途径就是使用`functools.partial`：

```python

from functools import partial
two_to_the = partial(exp,2)
print two_to_the(3) #结果是8

```

你当然也可以使用`partial`来指定后一个参数的值，只要你给出相应的参数名:

```python

square_of = partial(exp, power = 2)
print square_of(3)  #结果是9

```

但是这个方法在指定更多的参数的时候会变得很混乱，所以通常我们希望避免这样的代码。

当然我们有时也会使用`map`，`reduce`和`filter`等函数式工具来代替列表推到:

```python

def double(x):
    return 2 * x

xs = [1, 2, 3, 4]
twice_xs = [double(x) for x in xs] #结果是[2, 4, 6, 8]
twice_xs = map(double, xs)         #结果同上

list_doubler = partial(map, double) #将一个列表双倍
twice_xs = list_doubler(xs)         #结果是[2, 4, 6, 8]

```

当然如果你提供了多个列表，你也可以对于多参数函数使用`map`:

```python

def multiply(x,y) : return x * y

products = map (multiply,[1,2],[4,5]) #结果是[1*4,2*5] = [4,10]

```

相应地，`filter`也起到了列表推导式中`if`的作用：

```python

def is_even(x):
    return x % 2 == 0

x_evens = [x for x in xs if is_even(x)] #结果[2, 4]
x_evens = filter(is_even, xs)
list_evenr = partial(filter, is_even)
x_evens = list_evenr(xs)

```

而`reduce`合并一个列表的前两个元素，并把得到的结果和第三个元素合并，然后将结果和第四个元素合并，最后产生单一的结果:


```python

x_product = reduce(multiply, xs) #结果是 1*2*3*4=24
list_product = partial(reduce,multiply)
x_product = list_product(xs)     #结果是24

```

###枚举

有时，我们需要遍历一个列表对于每一个元素使用它的值和序号:

```python

# 非　Pythonic

for i in range(len(documents)):
    document = documents[i]
    do_something(i, document)

#同样非 Pythonic

i = 0
for document in documents:
    do_something(i, document)
    i += 1

```
当然 Pythonic　的解决方法是使用可以产生(index, element)元组的`enumerate`:

```python

for i, document in enumerate(documents):
    do_something(i, document)

```

当然我们也可以只用序号:

```python
#非　Pythonic
for i in range(len(documents)): do_something(i)

# Pythonic

for i, _ in enumerate(documents): do_something(i)

```

我们经常会用到`enumerate`这种方法。

### zip函数和参数拆分

我们经常需要把两个或者更多的列表组合在一起。`zip`变换可以把多个列表打包到一个由元组组成的列表中:

```python

list1 = ['a', 'b', 'c']
list2 = [1, 2, 3]
zip(list1,list2) #结果是[('a',1), ('b', 2), ('c', 3)]

```
如果列表中有不同长度的列表，则`zip`在第一个元素结束的时候停止。

你也可以通过一种比较怪异的方法解包一个列表:

```python

pairs = [('a',1), ('b', 2), ('c', 3)]
letters,numbers = zip(*pairs)

```
这里的星号起到的作用就是参数拆分的作用，具体来说也就是将`pairs`中的每一个元素都作为独立的参数赋给`zip`函数。上述代码等价于如下代码:

```python

zip(('a', 1), ('b', 2), ('c', 3))

```

上述代码将返回`[('a', 'b', 'c'), ('1', '2', '3')]`。

当然你也可以对于其他函数使用参数拆分:

```python

def add( a, b ) : return a + b

add(1,2)
add([ 1, 2 ]) #类型错误
add(*[1, 2])  #结果为3

```
有时候你会发现这个特性特别有用，但是需要强调的是，这只是一个小技巧罢了。


### args 和　kwargs

如果你希望编写一个高阶函数，这个函数将某个函数作为参数输入，同时输出该参数函数值的两倍:

```python

def doubler(f):
    def g(x):
        return 2 * f(x)
    return g

```
有时这个方法可以成功:

```python

def f1(x):
    return x+1

g = doubler(f1)

print g(3) #结果是8(==(3+1)*2)
print g(-1)#结果是0

```

但是当输入多于一个参数的函数的时候上述方法就会失败:

```python

def f2(x, y):
    return x + y

g = doubler(f2)
print g(1, 2)

```

显然我们需要一个可以明确接受任意参数个数的方法。我们可以通过参数拆分和一些小魔法实现这个目标:


```python

def magic(*args, **kwargs):
    print "unnamed args:", args
    print "keyword args:", kwargs

magic(1,2,key="word",key2="word2")

#输出为
#unnamed args:(1,2)
#keyword args:{'key2':'word2','key':'word'}

```

也就是说当我们像这样来定义函数的时候，我们可以知道`args`代表了一个未命名参数的元组，而`kwargs`代表了一个命名参数的字典。当然这也意味着你可以通过一个元组和字典来向一个特定的函数输入需要的参数和命令。


```python

def other_way_magic(x,y,z):
    return x + y + z

x_y_list = [1, 2]
z_dict   = {"z" : 3}
print other_way_magic(*x_y_list,**z_dict) #结果是6

```

当然你可以做很多这样的小技巧。但是我们能主要是为了实现可以接受任意个数参数的函数而使用这个技巧:

```python

def doubler_correct(f):
    """可以无论 f 的输入如何变化都工作"""
    def g(*args.**kwargs):
        return 2*f(*args,**kwargs)
    return g

g = doubler_correct(f2)
print g(1,2)

```

###欢迎加入 DataSciencester!

现在新员工的入职培训正式结束。当然，遵守公司的规定，不要盗用任何东西。


## 进一步提高

* 已经有了很多很成熟的　Python 教程，Python 官网的[教程](https://docs.python.org/2/tutorial/)相当不错。
* IPython的官方教程并不是特别好，你或许可以参考他们的视频和讲义。或者你可以参考 Wes Mckinney的书*Python for Data Analysis*，这本书关于 IPython　的章节相当不错。
