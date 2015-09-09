# Chapter 6 概率
> The lays of probability, so true in general, so fallacious in particular

> -- Edward Gibbon

It is hard to do data science without some sort of understanding of probability and its mathematics. As with our treatment of statistics in [Chapter 5](), we’ll wave our hands a lot and elide many of the technicalities.
For our purposes you should think of probability as a way of quantifying the uncer‐ tainty associated with events chosen from a some universe of events. Rather than get‐ ting technical about what these terms mean, think of rolling a die. The universe consists of all possible outcomes. And any subset of these outcomes is an event; for example, “the die rolls a one” or “the die rolls an even number.”
Notationally, we write P E ￼ to mean “the probability of the event E.”
We’ll use probability theory to build models. We’ll use probability theory to evaluate
models. We’ll use probability theory all over the place.
One could, were one so inclined, get really deep into the philosophy of what probabil‐
ity theory means. (This is best done over beers.) We won’t be doing that.

## Dependence and Independence
Roughly speaking, we say that two events E and F are dependent if knowing some‐ thing about whether E happens gives us information about whether F happens (and vice versa). Otherwise they are independent.
For instance, if we flip a fair coin twice, knowing whether the first flip is Heads gives us no information about whether the second flip is Heads. These events are inde‐ pendent. On the other hand, knowing whether the first flip is Heads certainly gives us information about whether both flips are Tails. (If the first flip is Heads, then defi‐ nitely it’s not the case that both flips are Tails.) These two events are dependent.
Mathematically, we say that two events E and F are independent if the probability that they both happen is the product of the probabilities that each one happens:
```
P(E,F) =P(E)P(F)
```
In the example above, the probability of “first flip Heads” is 1/2, and the probability of “both flips Tails” is 1/4, but the probability of “first flip Heads and both flips Tails” is 0.


## Conditional Probability
When two events E and F are independent, then by definition we have:
```
P(E,F) = P(E)P(F)
```
If they are not necessarily independent (and if the probability of F is not zero), then we define the probability of E “conditional on F” as:

## Bayes's Theorem
## Random Variables
## Continuous Distributions
## The Normal Distribution
## The Central Limit Theorem
## For Further Exploration