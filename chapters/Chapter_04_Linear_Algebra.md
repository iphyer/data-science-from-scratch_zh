# Chapter4 线性代数

> 还是有什么比代数更加没用或用处不大的么？
>
> —— Billy Connolly

线性代数是数学上用来处理向量空间的一个分支。尽管我不指望在这么短的章节里教你，但它是很多数据科学概念和技术的基础，这意味着我有责任尝试（教会你）。

在本章我们所学到的内容在本书接下来的部分会用到很多。

## 向量

抽象来说， 向量是可以通过相加或乘以标量（比如数字）得到新的向量的对象 。对我们而言，它是在有限维度空间的点。尽管你可能并不把数据看作向量，但用向量表示数值型数据是很好的方式。

举例来说，你有一群人的身高，体重和年龄数据，你可以把这些数据看做三维向量（身高，体重，年龄）。如果你教一个有4门课的班级，你可以将学生的分数作为四维向量(成绩1，成绩2，成绩3，成绩4）

将向量用数值列表表示是最简单直接的方式，一个含有3个数的列表对应一个三维空间的向量，反之亦然：

```python
height_weight_age=[70,  # inches,
                   170, # pounds,
                   40]  # years

grades = [95, # exam1
          88, # exam2
          75, # exam3
          62] # exam4
```

用该方式需要面临一个问题就是需要处理向量的运算。由于Python的列表并非向量（因此也没有提供向量计算支持），我们需要自己实现这些计算工具，那我们就从这里开始吧。

我们会频繁使用向量相加，也就是向量的分量相加（Vectors add componentwise.），我们就从这里开始。
向量的分量相加的意思是，假设，有两个向量v和w，它们长度相同（列表中元素的个数相等），他们的和的第一个元素是 v[0] + w[0], 第二个元素是v[1] + w[1]， 以此类推。（如果它们的元素个数不等，则不允许相加），举例来说，[1,2] [2,1]相加的结果为[1 + 2, 2 + 1],或者[3, 3] 如图4-1所示

![](../assets/images/C04_001.png)


在python代码中，我们可以通过zip两个向量后，使用列表推导式(list comprehension) 相加对应的元素来实现：
> 译者注：[什么是列表推导式](http://www.cainiao8.com/python/basic/python_14_list_comprehension.html)

```python
def vector_add(v, w):
    """adds corresponding elements"""
    return [v_i + w_i
            for v_i, w_i in zip(v, w)]
```

同理，两个向量相减的运算，也就是列表对应元素进行相减：

```python
def vector_subtract(v, w):
    """subtracts corresponding elements"""
    return [v_i - w_i
            for v_i, w_i in zip(v,w)]
            
```

有时我们还需要获取一组向量的和，也就是有这样一个向量，它的第一个元素是所有向量的第一个元素之和，第二个元素是所有向量的第二个元素之和，以此类推。最简单的实现方法就是对一组向量进行逐个相加：

```python
def vector_sum(vectors):
    """sums all corresponding elements"""
    result = vectors[0]                     # start with the first vector
    for vector in vectors[1:]:              # then loop over the others
        result = vector_add(result, vector) # and add them to the result
    return result
```

稍微观察一下就会发现，我们是使用`vector_add`方法来减少列表中向量的总数，这意味着我们可以用高阶函数（更高级的函数）来简化该当前的函数。

```python
def vector_sum(vectors):
    return reduce(vector_add, vectors)
```

或者：

```python
vector_sum = partial(reduce, vector_add)
```

although this last one is probably more clever than helpful.


我们还要能支持向量乘以标量，也就是将向量中的每个元素与该标量相乘：

```python
def scalar_multiply(c, v):
    """c is a number, v is a vector"""
    return [c * v_i for v_i in v]

```

以下函数可以实现求一组长度相同的向量的分量的平均值：

```python
def vector_mean(vectors):
    """ compute the vector whose ith element is the mean of the
    ith elements of the input vectors"""
    n = len(vectors)
    return scalar_multiply(1/n, vector_sum(vectors))
```

比较少见的是点积(dot product)， 两个向量的点积也就是其分量积的总和

```python
def dot(v, w):
    """v_1 * w_1 + ... + v_n * w_n"""
    return sum(v_i * w_i
               for v_i, w_i in zip(v,w))
```

The dot product measures how far the vector v extends in the w direction. For example, if w = [1, 0] then dot(v, w) is just the first component of v. Another way of saying this is that it’s the length of the vector you’d get if you projected v onto w
(Figure 4-2).

在w方向上的
例如：假设 w = [1, 0]

![](../assets/images/C04_002.png)

使用如下的代码，可以很简单的算出向量的平方和

```python
def sum_of_squares(v):
"""v_1 * v_1 + ... + v_n * v_n"""
return dot(v, v)
```

其计算的结果我们可以用来计算向量的长度：

```python
import math
def magnitude(v):
    return math.sqrt(sum_of_squares(v)) # math.sqrt is square root function
```

现在，用于计算两个向量之间距离的所有组成部分都具备了：

![](../assets/images/C04_003.png)

```python
def squared_distance(v, w):
"""(v_1 - w_1) ** 2 + ... + (v_n - w_n) ** 2"""
    return sum_of_squares(vector_subtract(v, w))

def distance(v, w):
    return math.sqrt(squared_distance(v, w))
```

可能这样写更加清楚些（以上的代码等同于以下的代码）：

```python
def distance(v, w):
    return magnitude(vector_subtract(v, w))
```

知道这些足够们开始了，本书里我们会大量使用这些函数。

>用列表来阐述向量非常好，但性能却很糟糕，在实际应用中，我们会使用包含了高性能的数组类以及支持各种运算函数的NumPy库。


## 矩阵

矩阵是数值的二维集合。我们将用具有相同长度列表的列表来表示矩阵，列表中的每一个列表元素代表一行。 假设A是一个矩阵，那么A[i][j]表示第i行第j列的元素。根据数学约定，我盟将使用大写字母来表示矩阵，例如：

```python
A = [[1, 2, 3], # A has 2 rows and 3 columns
    [4, 5, 6]]
    
B = [[1, 2], # B has 3 rows and 2 columns
    [3, 4],
    [5, 6]]
```

> 在数学中，我们用 row 1 表示矩阵中的第一行，column 1 表示第一列，但由于我们使用Python 中的list来表示数组，list的索引是从0开始的，所以我们将矩阵的第一行成为row 0，第一列称为 column 0

鉴于我们用列表的列表的表示方法，根据其形状， 矩阵A有 len(A) 行，有len(A[0]) 列：

```python
def shape(A):
    num_rows = len(A)
    num_cols = len(A[0]) if A else 0 # number of elements in first row
    return num_rows, num_cols
```

假设一个矩阵有n行和k列，我们认为其是 n x k矩阵。我们可以认为 n x k 矩阵的每一行是一个长度为k的矩阵，每列是一个长度为n的向量：

```python
def get_row(A, i):
    return A[i] # A[i] is already the ith row
    
def get_column(A, j):
    return [A_i[j]      # jth element of row A_i
        for A_i in A]   # for each row A_i
```

We’ll also want to be able to create a matrix given its shape and a function for generating its elements. We can do this using a nested list comprehension:

我们需要一个可以根据给定其形状来创建一个矩阵及其元素的函数，可以通过嵌套列表来实现：



```python
def make_matrix(num_rows, num_cols, entry_fn):
    """returns a num_rows x num_cols matrix
    whose (i,j)th entry is entry_fn(i, j)"""
    return [[entry_fn(i, j) # given i, create a list
        for j in range(num_cols)] # [entry_fn(i, 0), ... ]
        for i in range(num_rows)] # create one list for each i
```


基于这个函数，你可以创建一个 5 x 5的单位矩阵（对角线值为1，其他是0）：
```python
def is_diagonal(i, j):
    """1's on the 'diagonal', 0's everywhere else"""
    return 1 if i == j else 0

identity_matrix = make_matrix(5, 5, is_diagonal)
# [[1, 0, 0, 0, 0],
# [0, 1, 0, 0, 0],
# [0, 0, 1, 0, 0],
# [0, 0, 0, 1, 0],
# [0, 0, 0, 0, 1]]
```

Matrices will be important to us for several reasons.
First, we can use a matrix to represent a data set consisting of multiple vectors, simply by considering each vector as a row of the matrix. For example, if you had the heights, weights, and ages of 1,000 people you could put them in a 1, 000 × 3 matrix:

矩阵对我们来说很重要有几个原因。

首先，我们可以用矩阵来表示 由多个向量组成的数据集，简单将每个向量当做一行。 例如，你又1000个人的身高，体重和年龄数据，你可以将它们表示为一个 1000 x 3的矩阵：

```python
data = [[70, 170, 40],
        [65, 120, 26],
        [77, 250, 19],
        # ....
        ]
```
Second, as we’ll see later, we can use an n × k matrix to represent a linear function that maps k-dimensional vectors to n-dimensional vectors. Several of our techniques and concepts will involve such functions.

其二，在后面后涉及到，我们可以用一个 n x k 矩阵来表示一个对应k维 向量到 n维向量的线性函数。一些技术和概念会需要这样的函数

Third, matrices can be used to represent binary relationships. In Chapter 1, we represented the edges of a network as a collection of pairs (i, j). An alternative representation would be to create a matrix A such that A[i][j] is 1 if nodes i and j are connected and 0 otherwise.
Recall that before we had:

第三，矩阵可以来表示二进制信息，在第一章中， 另外一种表示方法可以创造一个矩阵A，其中 A[i][j] 中如果节点i和j连接，其值是1，其他的都是0.

```python
friendships = [(0, 1), (0, 2), (1, 2), (1, 3), (2, 3), (3, 4),
(4, 5), (5, 6), (5, 7), (6, 8), (7, 8), (8, 9)]
```

我们也可以表示为：

```python
# user 0 1 2 3 4 5 6 7 8 9
#
friendships = [[0, 1, 1, 0, 0, 0, 0, 0, 0, 0], # user 0
[1, 0, 1, 1, 0, 0, 0, 0, 0, 0], # user 1
[1, 1, 0, 1, 0, 0, 0, 0, 0, 0], # user 2
[0, 1, 1, 0, 1, 0, 0, 0, 0, 0], # user 3
[0, 0, 0, 1, 0, 1, 0, 0, 0, 0], # user 4
[0, 0, 0, 0, 1, 0, 1, 1, 0, 0], # user 5
[0, 0, 0, 0, 0, 1, 0, 0, 1, 0], # user 6
[0, 0, 0, 0, 0, 1, 0, 0, 1, 0], # user 7
[0, 0, 0, 0, 0, 0, 1, 1, 0, 1], # user 8
[0, 0, 0, 0, 0, 0, 0, 0, 1, 0]] # user 9
```


If there are very few connections, this is a much more inefficient representation, since
you end up having to store a lot of zeroes. However, with the matrix representation it
is much quicker to check whether two nodes are connected—you just have to do a
matrix lookup instead of (potentially) inspecting every edge:

如果 关系比较少，由于需要存储大量的0， 该方法效率比较低，然而，检查两个节点是否有关联，

```python
friendships[0][2] == 1 # True, 0 and 2 are friends
friendships[0][8] == 1 # False, 0 and 8 are not friends
```


Similarly, to find the connections a node has, you only need to inspect the column (or the row) corresponding to that node:

类似的，查找一个节点的关系，仅仅需要查看该节点对应的列（或行）

```python
friends_of_five = [i # only need
    for i, is_friend in enumerate(friendships[5]) # to look at
    if is_friend] # one row
```

Previously we added a list of connections to each node object to speed up this process, but for a large, evolving graph that would probably be too expensive and difficult to maintain.
We’ll revisit matrices throughout the book.



## 进一步探索

* 线性代数在被据科学家们广泛使用（对于理解的人来说，频繁使用，只不过不明显，对于不理解线性代数的人说不频繁，frequently implicitly, and not infrequently by people who don’t understand it），阅读写相关的教材是很不错的想法，可以在网上找到不少免费的资料：

    - [UC Davis的线性代数](https://www.math.ucdavis.edu/~linear/)
    - [圣迈克尔学院的 线性代数](http://joshua.smcvt.edu/linearalgebra/)
    - 如果你喜欢探索，[Linear Algebra Done](http://www.math.brown.edu/~treil/papers/LADW/LADW.html)网站有更加高级的介绍

* 我们在本章所有创建的代码，在[NumPy](http://www.numpy.org)中都能找到（而且更多）。
