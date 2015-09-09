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

```
P(E|F) = P(E,F)/P(F)
```

You should think of this as the probability that *E* happens, given that we know that *F* happens.
We often rewrite this as:
```
P(E,F) = P(E)
```
When E and F are independent, you can check that this gives:
```
P(E|F) = P(E)
```
which is the mathematical way of expressing that knowing F occurred gives us no
additional information about whether E occurred.
One common tricky example involves a family with two (unknown) children. If we assume that:
1. Each child is equally likely to be a boy or a girl
2. The gender of the second child is independent of the gender of the first child

then the event “no girls” has probability 1/4, the event “one girl, one boy” has proba‐ bility 1/2, and the event “two girls” has probability 1/4.
Now we can ask what is the probability of the event “both children are girls” (B) con‐ ditional on the event “the older child is a girl” (G)? Using the definition of conditional probability:
```
P(B|G) = P(B,G)/P(G) = P(B)/P(G) = 1/2
```
since the event B and G (“both children are girls and the older child is a girl”) is just the event B. (Once you know that both children are girls, it’s necessarily true that the older child is a girl.)
Most likely this result accords with your intuition.
We could also ask about the probability of the event “both children are girls” condi‐ tional on the event “at least one of the children is a girl” (L). Surprisingly, the answer is different from before!
As before, the event B and L (“both children are girls and at least one of the children is a girl”) is just the event B. This means we have:
```
P(B|L)=P(B,L)/P(L) = P(B)/P(L)=1/3
```

How can this be the case? Well, if all you know is that at least one of the children is a girl, then it is twice as likely that the family has one boy and one girl than that it has both girls.
We can check this by “generating” a lot of families:

```python
def random_kid():
return random.choice(["boy", "girl"])
    both_girls = 0
    older_girl = 0
    either_girl = 0
random.seed(0)
for _ in range(10000):
younger = random_kid() older = random_kid() if older == "girl":
older_girl += 1
if older == "girl" and younger == "girl":
both_girls += 1
if older == "girl" or younger == "girl":
            either_girl += 1

print "P(both | older):", both_girls / older_girl # 0.514 ~ 1/2 print "P(both | either): ", both_girls / either_girl # 0.342 ~ 1/3
```
## Bayes's Theorem
## Random Variables
## Continuous Distributions
## The Normal Distribution
## The Central Limit Theorem
## For Further Exploration