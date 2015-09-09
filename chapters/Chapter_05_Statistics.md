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

```

### Central Tendencies
### Dispersion

## Correlation
## Simpson's Paradox
## Some Other Correlational Caveats
## Correlation and Causation
## For Further Exploration
