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
    younger = random_kid() 
    older = random_kid() 
    if older == "girl":
        older_girl += 1
    if older == "girl" and younger == "girl":
        both_girls += 1
    if older == "girl" or younger == "girl":
        either_girl += 1

print "P(both | older):", both_girls / older_girl # 0.514 ~ 1/2 
print "P(both | either): ", both_girls / either_girl # 0.342 ~ 1/3
```
## Bayes's Theorem
One of the data scientist’s best friends is Bayes’s Theorem, which is a way of “revers‐ ing” conditional probabilities. Let’s say we need to know the probability of some event E conditional on some other event F occurring. But we only have information about the probability of F conditional on E occurring. Using the definition of conditional probability twice tells us that:
```
P(E|F)=P(E,F)|P(F)=P(E|F)P(E)/P(F)
```
The event F can be split into the two mutually exclusive events “F and E” and “F and
not E.” If we write ¬E for “not E” (i.e., “E doesn’t happen”), then:
```
P(F)=P(F,E)+P(F,-E)
```
so that:
```
P(E|F) = P(F|E)P(E)/[P(F|E)P(E) + P(F|-E)P(-E)]
```
which is how Bayes’s Theorem is often stated.
This theorem often gets used to demonstrate why data scientists are smarter than doctors. Imagine a certain disease that affects 1 in every 10,000 people. And imagine that there is a test for this disease that gives the correct result (“diseased” if you have the disease, “nondiseased” if you don’t) 99% of the time.
What does a positive test mean? Let’s use T for the event “your test is positive” and D for the event “you have the disease.” Then Bayes’s Theorem says that the probability that you have the disease, conditional on testing positive, is:

```
P(D|T) = P(T|D)P(D)/[P(T|D)P(D) + P(T|-D)P(-D)]
```
Here we know that P T D , the probability that someone with the disease tests posi‐ tive, is 0.99. P(D) , the probability that any given person has the disease, is 1/10,000 = 0.0001. P(T|¬D) , the probability that someone without the disease tests positive, is 0.01. And P(¬D) , the probability that any given person doesn’t have the disease, is 0.9999. If you substitute these numbers into Bayes’s Theorem you find
```
P(D|T) = 0.98%
```
That is, less than 1% of the people who test positive actually have the disease.

> This assumes that people take the test more or less at random. If only people with certain symptoms take the test we would instead have to condition on the event “positive test and symptoms” and the number would likely be a lot higher.

While this is a simple calculation for a data scientist, most doctors will guess that P(D|T) is approximately 2.
A more intuitive way to see this is to imagine a population of 1 million people. You’d expect 100 of them to have the disease, and 99 of those 100 to test positive. On the other hand, you’d expect 999,900 of them not to have the disease, and 9,999 of those to test positive. Which means that you’d expect only 99 out of (99 + 9999) positive testers to actually have the disease.
## Random Variables
A random variable is a variable whose possible values have an associated probability distribution. A very simple random variable equals 1 if a coin flip turns up heads and 0 if the flip turns up tails. A more complicated one might measure the number of heads observed when flipping a coin 10 times or a value picked from range(10) where each number is equally likely.

The associated distribution gives the probabilities that the variable realizes each of its possible values. The coin flip variable equals 0 with probability 0.5 and 1 with proba‐ bility 0.5. The range(10) variable has a distribution that assigns probability 0.1 to each of the numbers from 0 to 9.

We will sometimes talk about the expected value of a random variable, which is the average of its values weighted by their probabilities. The coin flip variable has an expected value of 1/2 (= 0 * 1/2 + 1 * 1/2), and the range(10) variable has an expected value of 4.5.

Random variables can be conditioned on events just as other events can. Going back to the two-child example from [“Conditional Probability”]() on page 70, if X is the ran‐ dom variable representing the number of girls, X equals 0 with probability 1/4, 1 with probability 1/2, and 2 with probability 1/4.

We can define a new random variable Y that gives the number of girls conditional on at least one of the children being a girl. Then Y equals 1 with probability 2/3 and 2 with probability 1/3. And a variable Z that’s the number of girls conditional on the older child being a girl equals 1 with probability 1/2 and 2 with probability 1/2.

For the most part, we will be using random variables implicitly in what we do without calling special attention to them. But if you look deeply you’ll see them.

## Continuous Distributions
A coin flip corresponds to a discrete distribution—one that associates positive proba‐ bility with discrete outcomes. Often we’ll want to model distributions across a contin‐ uum of outcomes. (For our purposes, these outcomes will always be real numbers, although that’s not always the case in real life.) For example, the uniform distribution puts equal weight on all the numbers between 0 and 1.
Because there are infinitely many numbers between 0 and 1, this means that the weight it assigns to individual points must necessarily be zero. For this reason, we represent a continuous distribution with a probability density function (pdf) such that the probability of seeing a value in a certain interval equals the integral of the density function over the interval.

> If your integral calculus is rusty, a simpler way of understanding this is that if a distribution has density function f , then the proba‐ bility of seeing a value between x and x+h is approximately h * f ￼ x ￼ if h is small.


The density function for the uniform distribution is just:
```python
def uniform_pdf(x):
    return 1 if x >= 0 and x < 1 else 0
```
The probability that a random variable following that distribution is between 0.2 and 0.3 is 1/10, as you’d expect. Python’s random.random() is a [pseudo]random variable with a uniform density.
We will often be more interested in the cumulative distribution function (cdf), which gives the probability that a random variable is less than or equal to a certain value. It’s not hard to create the cumulative distribution function for the uniform distribution (Figure 6-1):

```python

def uniform_cdf(x):
"returns the probability that a uniform random variable is <= x"
￼if x < 0: return 0 elif x < 1: return x else: return 1
# uniform random is never less than 0
# e.g. P(X <= 0.4) = 0.4
# uniform random is always less than 1
```
## The Normal Distribution
## The Central Limit Theorem
## For Further Exploration