# 1. What is probability?

## Summary

> Probability is a rational degree of belief. Probability is the engine of our statistical approach. We use it to update our belief when new data arrives.

## 1.1. Randomness is in the world. Uncertainty is in your head.

Imagine you want to know if a dog barks in the presence of a stranger. The dog will either bark or not. But you don't know it for sure before the stranger enters the room.

- The outcome is unknown.
- The world will produce one outcome.
- Probability is your uncertainty before the outcome happens. It ranges between 0 and 1.

P = 0 -> impossible: The dog will not bark!
P = 1 -> certain: The dog will definitely bark!

Are you completely clueless about the outcome? Probably not. Probably you already have some preliminary knowledge (eg. You know how the dog usually reacts to strangers). So you rank your probability as:

P = 0.7 -> fairly confident: I'm sure the dog will bark, but maybe not. 

> Probability is a degree of belief. 

But not *any* kind of degree of belief...

## 1.2. Probability is a rational degree of belief. 

This is key. It's not based on gut feeling. It's a belief constrained by logic. In other words, probability indicates how strongly you should believe something, **given what you know.** 

If you know that dogs typically bark at strangers. This puts your confidence to a P = 0.7. But the owner tells you before the experiment that his dog is very well behaving, and hardly ever barks at anyone. Okay, then maybe you adjust your belief to P = 0.2. But it's a laboratory setting that stresses out dogs... so maybe P = 0.4. 

> Probability updates with information.

And because probability is constrained by logic, it also means that we need to stay in the logical framework...

## 1.3. Your beliefs must obey rules.

If probability is rational belief, then your beliefs must obey rules to maintain mathematical consistency. This is what we call **logical coherence.** 

Eg.
if P(A) = 0.7, 
then 
P(not A) = 0.3. 

> All probabilities lie between 0 and 1.

In our case "A" and "not A" are mutually exclusive, discrete outcomes.

However, outcomes can also range on a continuous scale. In this case we assign probability to ranges. 

Eg. if you have a continuous parameter (let's call it δ):

P(0 < δ < 0.5) = 0.7.

In this case, if you want to define the probability of a single value in that continuous scale, it will always be 0. 

P(δ = 0.3) = 0

If this seems counterintuitive at first glance, don't worry, we'll make this clear later when we talk about Probability Density Functions (PDFs). For now, just imagine the exact value being a point on that continuous line. A point is merely an abstract concept, it's width is 0. It takes up no space on the line itself.

## 1.4. Events can be observed. Parameter values are truly unknown. 

There are two uncertain things in the context of statistics:
**EVENTS**: The single outcomes. (Eg. if a dog barks, if training has an effect, if a kid has ADHD, etc). These are instances.
**PARAMETERS:** They describe the stable structure of the world. These are underlying structural quantities that generate events.

We mostly care about the latter, because parameters let us generalize. 

> Ideally, we look at data from past events, so we can reduce our uncertainty about the parameter, and then we can predict future events.

## 1.5. Probability distribution is a snapshot of what you currently know.

Distributions play a crucial role in Bayesian statistics. Distributions change as we gain more information about the world. 

Our *a priori* belief has a distribution. So does the updated *a posteriori* belief. (We will use this concept a lot in the future.)

The distribution is the structure of the belief. Eg. you know that in the training intervention study, muscle gain will surely be more than zero grams in the given period, but very unlikely to be over 200 grams. Most likely somewhere between 50 and 150 grams. 

The distribution encodes what values are plausible (those between 50 and 150 grams), what values are unlikely (200 grams and above), and how uncertain you are (reflected in how spread out the distribution is).

In another example study we compare zero crossing rate (ZCR) values of motion sensor data from two groups: one with people with ADHD, the other one with neurotypical development. We are not sure what the actual measurements will bring. Do ADHD people have higher ZCR than the "normies"? Or the other way around? Most probability mass will be around 0 (no effect), but it can be positive and negative as well. Our **prior distribution** will be a nice "bell curve". Once we do the measurements, we can update this shape. This will be our **posterior distribution**. (Note, we will talk a lot later about situations when "we have no clue", or when we need to use *uninformed* or *weakly informed* priors.)

> Distribution is not "noise". It's structured uncertainty.


