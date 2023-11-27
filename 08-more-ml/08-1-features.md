## ML Metatechniques: Feature Selection

* Worth talking more about the stuff that is common across
  ML apps

* So far we've talked about

  * Controlling overfitting through dataset splits
  * Evaluating with limited data through cross-validation

* There's worlds more: we'll look at feature selection today

## Feature Selection

* So you have a bunch of features. This sounds great. Surely
  more information moar better?
  
* Here's the thing: "noise" features

  * Slow down learners
  * More importantly, *confuse* learners

* Consider a system with a couple of "good" features and a
  bunch of uniform random ones… <https://github.com/pdx-cs-ai/noisefeatures>

## Feature Selection

* So get rid of "noise" features… but how to tell?

  * *A priori:* be careful what you throw in the bag
  * Use quality criterion, but be careful of dependence

* Watch out: this is a kind of ML, so you need to worry
  about overfitting and bias. Do cross-validation or
  validation set holdouts

* My favorite quality criterion: just straight up min
  entropy features
