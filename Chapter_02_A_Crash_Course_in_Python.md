# Chapter 2 Python快速入门课程
> 让我难以置信的是，25 年过去了，人们依旧为 Python 痴狂。

> Michael Palin

所有 DataSciencester 的新员工都被要求参加新员工的入职培训会，在入职培训会上最有意思的部分就是会有一个关于 Python 的快速入门课程。

这并不是一个无所不包的 Python 教程，但是这门课程将会重点讲授那些 DataSciencester 数据科学家们最常使用的知识点( 一部分知识点恰恰是通常的 Python 入门课程不怎么关注的。)。

## 基础知识

### 获取 Python

你可以直接从 Python.org 下载 Python。 但是如果你的机器上还有 Python， 我特别推荐你直接安装 Anaconda 这个 Python 发行版, 因为 Anaconda 几乎已经包括了所有你可能在数据科学中用到的 Python 包。

在我写作本书的时候，最新的 Python 版本已经升级到了 3.4 。但是在 DataSciencester 我们使用更加可靠的老版本， Python 2.7 。 Python 3 并不向后兼容 Python 2 而很多重要的软件包只能在 Python 2.7 下工作。 数据科学社区依然坚守在 Python 2.7 的版本上，这也意味着我们不得不遵守这个传统。 请确保你已经安装了正确的 Python 版本。

如果你不能安装 Anaconda，请一定要安装 pip 这个软件包， pip 是让你可以轻松安装第三方软件包，特别是有些我们必须的第三方软件包的 Python 包管理程序。 pip 也可以和 IPython很好的集合在一起工作，IPython是一个相当易用方便的 Python 交互式解释器。

( 如果你安装了 Anaconda 那么 pip 和 IPython应该已经自动安装了。)
