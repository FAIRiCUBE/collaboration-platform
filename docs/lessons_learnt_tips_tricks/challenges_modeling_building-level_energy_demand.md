# Challenges in modeling building-level energy demand


## Reference Use case

UC4


## Problem statement

 The goal of UC4 is to create a model which estimates energy demand per building applicable to any European city. 
 
 UC4 has basically had negative results:
- EPISCOPE out of the box does not work well to predict building energy demand
- EPISCOPE augmented with new variables likewise had low predictive power
- Using image processing to get building heights and from there volume, and from there energy demand, seemed promising, but needs considerably more work: with the time invested so far we basically did not get to a model which works satisfactorily.

It must also be noted that a big problem is represented by the fact that this model was not taking into account the user behaviour (which can be taken into account only if energy consumption data are available, and this is quite difficult to obtain), without which the energy demand (needed to properly drive retrofitting projects) could not be estimated with the required accuracy. 


## Proposed solution

With further investment in modeling - either conventional or ML - it is likely we could get a better-performing model.


## Expected benefits

Even without data on usage patterns. the results of a model could be quite useful to provide “relative” (and not “absolute”) energy demand estimations.

As an example of a potential benefit (Key Exploitable Result for UC4): identifying that in a specific district there is a predominant presence of buildings with certain classes of energy performances, could represent an interesting result for a retrofitting company.
