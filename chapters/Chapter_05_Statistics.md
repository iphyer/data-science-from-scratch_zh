# Chapter 5 统计

> Facts are stubborn, but statistics are more pliable.

> Mark Twain

Statistics refers to the mathematics and techniques with which we understand data. It is a rich, enormous field, more suited to a shelf (or room) in a library rather than a chapter in a book, and so our discussion will necessarily not be a deep one. Instead, I’ll try to teach you just enough to be dangerous, and pique your interest just enough that you’ll go off and learn more.


## 描述单个数据集合
Through a combination of word-of-mouth and luck, DataSciencester has grown to dozens of members, and the VP of Fundraising asks you for some sort of description of how many friends your members have that he can include in his elevator pitches.
Using techniques from Chapter 1, you are easily able to produce this data. But now you are faced with the problem of how to describe it.
One obvious description of any data set is simply the data itself:

```python
num_friends = [100, 49, 41, 40, 25,
               # ... and lots more
               ]
```
For a small enough data set this might even be the best description. But for a larger data set, this is unwieldy and probably opaque. (Imagine staring at a list of 1 million numbers.) For that reason we use statistics to distill and communicate relevant fea‐ tures of our data.
As a first approach you put the friend counts into a histogram using Counter and plt.bar() (Figure 5-1):

```python
friend_counts = Counter(num_friends) xs = range(101)
ys = [friend_counts[x] for x in xs] plt.bar(xs, ys)
plt.axis([0, 101, 0, 25])
plt.title("Histogram of Friend Counts")
plt.xlabel("# of friends")
plt.ylabel("# of people")
plt.show()
```

Unfortunately, this chart is still too difficult to slip into conversations. So you start generating some statistics. Probably the simplest statistic is simply the number of data points:
```python
num_points = len(num_friends) # 204
```
You’re probably also interested in the largest and smallest values:
```python
largest_value = max(num_friends) # 100 
smallest_value = min(num_friends) # 1
```
which are just special cases of wanting to know the values in specific positions:
```python
sorted_values = sorted(num_friends)
    smallest_value = sorted_values[0]           # 1
    second_smallest_value = sorted_values[1]    # 1
    second_largest_value = sorted_values[-2]    # 49
```
But we’re only getting started.

### Central Tendencies
Usually, we’ll want some notion of where our data is centered. Most commonly we’ll use the mean (or average), which is just the sum of the data divided by its count:
```python
 # this isn't right if you don't from __future__ import division
def mean(x):
return sum(x) / len(x)
mean(num_friends) # 7.333333
```
If you have two data points, the mean is simply the point halfway between them. As you add more points, the mean shifts around, but it always depends on the value of every point.
We’ll also sometimes be interested in the median, which is the middle-most value (if the number of data points is odd) or the average of the two middle-most values (if the number of data points is even).
For instance, if we have five data points in a sorted vector x, the median is x[5 // 2] or x[2]. If we have six data points, we want the average of x[2] (the third point) and x[3] (the fourth point).
Notice that—unlike the mean—the median doesn’t depend on every value in your data. For example, if you make the largest point larger (or the smallest point smaller), the middle points remain unchanged, which means so does the median.
The median function is slightly more complicated than you might expect, mostly because of the “even” case:
```python
def median(v):
"""finds the 'middle-most' value of v""" n = len(v)
sorted_v = sorted(v)
midpoint = n // 2
if n % 2 == 1:
    # if odd, return the middle value return sorted_v[midpoint]
else:
    # if even, return the average of the middle values lo = midpoint - 1
    hi = midpoint
    return (sorted_v[lo] + sorted_v[hi]) / 2
median(num_friends) # 6.0
```

Clearly, the mean is simpler to compute, and it varies smoothly as our data changes. If we have n data points and one of them increases by some small amount e, then neces‐ sarily the mean will increase by e / n. (This makes the mean amenable to all sorts of calculus tricks.) Whereas in order to find the median, we have to sort our data. And changing one of our data points by a small amount e might increase the median by e, by some number less than e, or not at all (depending on the rest of the data).

> There are, in fact, nonobvious tricks to efficiently compute medians without sorting the data. However, they are beyond the scope of this book, so we have to sort the data.

At the same time, the mean is very sensitive to outliers in our data. If our friendliest user had 200 friends (instead of 100), then the mean would rise to 7.82, while the median would stay the same. If outliers are likely to be bad data (or otherwise unrep‐ resentative of whatever phenomenon we’re trying to understand), then the mean can sometimes give us a misleading picture. For example, the story is often told that in the mid-1980s, the major at the University of North Carolina with the highest average starting salary was geography, mostly on account of NBA star (and outlier) Michael Jordan.
A generalization of the median is the quantile, which represents the value less than which a certain percentile of the data lies. (The median represents the value less than which 50% of the data lies.)

```python
def quantile(x, p):
    """returns the pth-percentile value in x""" 
    p_index = int(p * len(x))
    return sorted(x)[p_index]
quantile(num_friends, 0.10) # 1 
quantile(num_friends, 0.25) # 3 
quantile(num_friends, 0.75) # 9 quantile(num_friends, 0.90) # 13
```

### Dispersion

## Correlation
## Simpson's Paradox
## Some Other Correlational Caveats
## Correlation and Causation
## For Further Exploration
