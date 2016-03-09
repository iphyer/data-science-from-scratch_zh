# Data Science from Scratch First Principles with Python 试译

## 声明
该翻译仅供学习交流，不做任何商业用途，尊重作者的辛勤劳动，请到这里[购买]正版图书(http://www.amazon.com/Data-Science-Scratch-Principles-Python/dp/149190142X)
![buy](assets/images/buy.png)

* 作者**Joel Grus**的[Github链接](https://github.com/joelgrus)
* [书籍示例代码](https://github.com/joelgrus/data-science-from-scratch)

##前言

我在自学的过程中，遇到不少有趣的资源，比如在[Jason的网站](http://machinelearningmastery.com/)找到的对出于不同目标，不同背景学习机器学习的小伙伴划分派系（查看：[Find Your Machine Learning Tribe: Get Started And Avoid Getting The Wrong Advice](http://machinelearningmastery.com/machine-learning-tribe/)）从而更具有针对性的开始和深入。

作为一个（数学底子不扎实的）程序猿 :(，深刻体会到先去学习线性代数、概率论、统计学然后再开始机器学习是有多么枯燥和沮丧，Jason的观点 [Machine Learning for Programmers: Leap from developer to machine learning practitioner](http://machinelearningmastery.com/machine-learning-for-programmers/) 绝对是让人眼前一亮，在挖他得博文时知道了**[Data Science From Scratch: First Principles with Python](http://joelgrus.com/2015/04/26/data-science-from-scratch-first-principles-with-python/)** 这本书，在今年近5月份出版，现在还没有中文版。

啃书做笔记的时候想，也许还有很多小伙伴和我面临一样的困境呢，要不试试把它翻译一下，权当巩固，说不定能帮到一些小伙伴，在我还在思考时，iphyer小朋友很久之前已经在GitBook上展开他的工作了，并已经翻译了两章了（[点这里阅读](http://iphyer.gitbooks.io/data-science-from-scratch-with-python/content/index.html)），联系他后，很愉快的就决定一起实现这个计划！

我们尽力做到最好，但才疏学浅，如果有误，还望不吝赐教！

如果你想一起翻译，或者交流数据科学的学习心得，联系我们吧！:D

###2016.03.09 更新

因为各种原因这个项目进度比较缓慢。[iphyer](https://github.com/iphyer)和[hexcola](https://github.com/hexcola)都比较忙。

正好[iphyer](https://github.com/iphyer)参加了[bingjin](https://github.com/bingjin)的 [ThinkPython](https://github.com/bingjin/ThinkPython2-CN)　翻译项目，我们重新整理了下整个项目。也请[bingjin](https://github.com/bingjin)帮我们推广下，希望可以引入更多的人加入到这个项目中来。

##翻译指南
###任务分类

项目的任务主要是两类:

1. 翻译
2. 校对

欢迎大家加入进来，最近感觉到了data science的引爆点，希望这本书可以给大家更多的帮助。

###参与步骤

1. fork本项目
2. 修改进度表，添加自己的github账户。大家在commit里面标注下自己申请的章节号。
3. 提交到自己的github仓库
4. 向[iphyer](https://github.com/iphyer)pull requests
5. 翻译或者校对
6. 提交到自己的github仓库
7. 向我pull requests

主要就是这个流程。希望大家可以借助 Github　协同工作起来。

也可以微信联系我,微信号: iphyer。

###注意事项

1. 统一使用 Markdown　语言编辑。
2. 图片存放在assets/images/文件夹下,截图存为png格式即可,命名格式为
3. 翻译不需要包括英文，包括也可以，这样可以帮助校对的同学校对。但是为了减轻翻译负担不强制包括。
4. 这本书的翻译并不轻松，如果感觉翻译不下去，也可以提交已经翻译好的部分结果，在commit中说明即可。但是在最后完成名单中只保留首页的完成者。请量力而行，善始善终。

##翻译进度表

| 章节        | 译者           | 翻译进度  | 校对者 | 校对进度  |
| ------------- |:-------------:|:-----:|:-----:|
| [第1章：简介](chapters/Chapter_01_Introduction.md)      | [iphyer](https://github.com/iphyer) | 完成 |     |   待校对  |
| [第2章：Python快速入门教程](chapters/Chapter_02_A_Crash_Course_in_Python.md)      | [iphyer](https://github.com/iphyer)      |  完成 |      |  待校对  |
| [第3章：数据可视化](chapters/Chapter_03_Visualizing_Data.md) | [hexcola](https://github.com/hexcola)      |   完成  |      |  待校对  |
| [第4章：线性代数](chapters/Chapter_04_Linear_Algebra.md) | [hexcola](https://github.com/hexcola)      |   完成  |       | 待校对  |
| [第5章：统计](chapters/Chapter_05_Statistics.md) | [hexcola](https://github.com/hexcola)      |   完成  |     |   待校对  |
| [第6章：概率](chapters/Chapter_06_Probability.md) |  [iphyer](https://github.com/iphyer)       |   *正在进行*  |      |  待校对  |
| [第7章：假设和推理](chapters/Chapter_07_Hypothesis_and_Inference.md) |      | 待认领  |      |  待校对  |
| [第8章：梯度下降](chapters/Chapter_08_Gradient_Descent.md) |      | 待认领 |      |  待校对  |
| [第9章：获取数据](chapters/Chapter_09_Getting_Data.md) |     |   待认领  |      |  待校对  |
| [第10章：处理数据](chapters/Chapter_10_Working_with_Data.md) |       |   待认领  |      |  待校对  |
| [第11章：机器学习](chapters/Chapter_11_Machine_Learning.md) |     |  待认领  |      |  待校对  |
| [第12章：k近邻算法](chapters/Chapter_12_k_Nearest_Neighbors.md) |       |   待认领  |     |   待校对  |
| [第13章：朴素贝叶斯](chapters/Chapter_13_Naive_Bayes.md) |       |   待认领  |      |  待校对  |
| [第14章：简单线性回归](chapters/Chapter_14_Simple_Linear_Regression.md) |       |   待认领  |      |  待校对  |
| [第15章：多元回归](chapters/Chapter_15_Multiple_Regression.md) |       |   待认领  |      |  待校对  |
| [第16章：逻辑回归](chapters/Chapter_16_Logistic_Regression.md) |       |   待认领  |   　  |   待校对  |
| [第17章：决策树](chapters/Chapter_17_Decision_Trees.md) |       |   待认领  |       | 待校对  |
| [第18章：神经网络](chapters/Chapter_18_Neural_Networks.md) |       |   待认领  |      |      | 待校对  |
| [第19章：集群](chapters/Chapter_19_Clustering.md) |       |   待认领  |      |  待校对  |
| [第20章：自然语言处理](chapters/Chapter_20_Natural_Language_Processing.md)|       |   待认领  |      |  待校对  |
| [第21章：网络分析](chapters/Chapter_21_Network_Analysis.md) |       |   待认领  |      |  待校对  |
| [第22章：推荐系统](chapters/Chapter_22_Recommender_Systems) |       |   待认领  |      |  待校对  |
| [第23章：数据库与SQL](chapters/Chapter_23_Database_and_SQL.md) |       |   待认领  |      |  待校对  |
| [第24章：MapReduce](chapters/Chapter_24_MapReduce.md) |       |   待认领  |      |  待校对  |
| [第25章：前进吧！继续你的数据科学之路](chapters/Chapter_25_Go_Forth_and_Do_Data_Science.md) |       |   待认领  |      |  待校对 |

全书目前的翻译进度：


|状态  |已完成    |正在进行  |等待认领  |校对完成 |校对完成 |
| ------|------- |:-------------:| -----:|-----:|-----:|
| 数量  | 2 章     | 7 章     | 16 章      |0 章      |25 章      |

欢迎大家参与进来！


