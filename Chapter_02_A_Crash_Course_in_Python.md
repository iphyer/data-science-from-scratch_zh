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
```python
```
```python
```

