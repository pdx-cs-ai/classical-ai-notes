## Overfitting

* Can classify the training data perfectly

  * Never test against the training data

* So need to not undergeneralize (overfit)

* Often hard to tell when you are overfitting

## Splitting Labeled Data

* Pick a split:

  * Less training data = worse results
  * Less test data = worse ability to evaluate
  * May need to worry about properties of split:
    * Statisticaly homogenous = random sampling, but of what?
    * Bad data

## Cross-Validation

* Break data up in to n chunks
* Test each chunk against a learner trained on the others
* Extreme case: Leave-one-out cross-validation

## Still Overfitting

* Still need to adjust our generalization
* Now we need a validation set

