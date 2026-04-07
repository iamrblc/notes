# 1. The Golem of Prague

## 1.1. Statistical Golems

The purpose of this book is to challenge the way researchers look at statistics in their everyday work. Very often they use statistical models mechanically, trying to find the best ready-made model to the given problem. Instead of looking at statistics as a field of mathematics or science, it can be beneficial to use an engineering approach. 

Surely, =="plumbers can do a lot withouth understanding fluid dynamics"==, but if we look under the hood, we can get more out of it.

For example, you may be told that the plain old linear regression is quite a useful tool in many scenarios. But it has its shortcomings (eg. cannot handle measurement errors on prediction variables, it's prone to overfitting, etc.) and it's almost always better to ditch it for a custom model. 

Richard consistently call statistical models **"Golems"**, because just like the clay robot from jewish folklore, they can also do whatever they are told to do. But neither models nor the golem are wise. They just follow instructions. And if you don't know how to tell them what to do or you can't interpret what they do, they are pretty useless (or may even be harmful). While I will just call statistical models statistical models, I think this concept is really powerful.

Statistical inference is not the use of a set of pre-made tools. ==Statistical inference is a set of strategies.==

# 1.2. Statistical Rethinking

Another reason why a different approach to statistics may be necessary in everyday scientific work is rooted in science philosophy and how we gather information about the world around us, how we make scientific discoveries. 

A very common misconception is that the proper objective of statistical inference is to test (falsify) a given null hypothesis. There are a few issues with this.

While science could "work" better if all questions would be falsifiable, **falsification is not an absolute requirement**. Think of the classic example of the black swan. If our null hypothesis is that all swans are white, as soon as you show just a single specimen of a black swan, it is enough to *reject the null*. But most science questions are not like this. They are more like "What percentage of dogs bark in the presence of strangers?" You might say, that oh, we can just do some statistical tests, and if the p0 is lower than 0.05, we just reject the null hypothesis, so we indeed falsified it. 

But **scientific hypotheses are not the same as statistical models**. We will go much deeper into this later, but a scientific model (the hypothesis) and the statistical model should go hand in hand. It is very important that ==rejecting a null hypothesis that was derived from a hypothesis doesn't mean that we can deduce that the hypothesis itself is false==. 

There is also a methodological paradox: improvement in measurement makes it easier to reject the null. If your research hypothesis includes a quantitative prediction then it's fine. But it's rarely the case. Imagine you have a hypothesis about dogs barking just as much in the present of a stranger as if they only have their owner with them. This is your null. You gather 30 dogs and count the barks with each dog twice (once with a stranger and once without). You run a paired t-test and your p value is around 0.8. You couldn't reject this null, put this in your thesis, and sit back. Yes, we know, that we can can reject the null but we cannot *accept* the null. But we all *know* what this means in practice. 

Now you gather 100 more dogs. You refine the way you count barks. Maybe you improve the measurement as well and reconsider how you count single woofs, yelps or continuous series of barks. And now you can reject the null. With the same hypothesis, same statistical model. 


