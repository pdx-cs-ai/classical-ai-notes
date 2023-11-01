## Decision theory

* The utility equation

* Measuring information

* Cost of gathering information

* A Bayesian method

## Expected Value

* The *expected value* of a uniformly distributed set of
  numbers is the average of its values
  
        E(S) = sum S / |S|

* More generally, the expected value is the centroid

        E(S) = sum [e in S] e pr(e in S)

  This reduces to the average when elements are equally
  probable

## The Utility Equation

* Sometimes you need to pick a best action *a* from a set
  of choices *A*

* When you know what effect *e(a)* each action will have, and
  you know the value *v(e)* of each effect, this is easy:
  just pick

        argmax [a in A] v(e(a))

* But the world is uncertain. Sometimes all you know is
  the probability of various action effects *pr(e|a)*

* You might evaluate the utility *U* of an action in terms
  of *expected* effect value

        U(a) = E(v(a)) = sum [e in e(a)] v(e) pr(e|a)

* You can now just maximize again

        argmax [a in A] U(a)

## Bayes's Rule

* Given

    * evidence *E* with *prior probability* *pr(E)*

    * hypothesis *H* with pp *pr(H)*

    * probability *pr(E|H)* of the evidence given that the
      hypothesis holds

* We want

    * probability *pr(H|E)* that the hypothesis holds given
      the evidence

* By Bayes's Rule

    * *pr(H|E) = pr(E|H) pr(H) / pr(E)*

## The Medical Example

* H = "You have Glaubner's Disease"  
  E = "Reaper's Test is positive"

* Rare disease: *pr(H) = 1e-6*

* Low false positive rate: *pr(E|¬H) = 1e-4*

* Perfect false negative rate: *pr(E|H) = 1*

        pr(H|E) = pr(H) pr(E|H) / pr(E)
                = pr(H) / pr(E and H or E and ¬H)
                = pr(H) / (pr(E|¬H) pr(¬H) + pr(E|H) pr(H))
                = 1e-6 / (1e-4 × (1-1e-6) + 1e-6)
                ~= 1e-6 / 1e-4 = 1e-2 = 0.01

* IRL the false negative rate will be nonzero too, so you
  will not learn a ton from the test either way

* Been there

## Bayesian Belief Networks

* Bayes Net (BBN, influence diagram) : indicate which priors and
  conditionals have significant influence in practice

                        Cloudy
                       /      \
                  Sprinkler   Rain
                       \      /
                      Wet Grass

* Usually reason one of two ways:

    * causal/top-down: 
    
             p(W|C) = p(W|S or R)
                    = 1 - p(W|¬S) p(¬S|C) p(C) ×
                          p(W|¬R) p(¬R|C) p(C)

    * diagnostic/bottom-up: *p(C|W)*

* Polytrees: special case for easy computation

* Problem: everything depends on everything else

    * Need to know impossible number of prior and conditional
      probabilities to conclude anything

    * Maybe *learn* probabilities?

## Is Your Probabilistic Model Meaningful?

* Difference between 0.5 and "don't know" and "don't care"

* MYCIN and probabilities *vs* "likelihoods"

* Consequence of Cox's Theorem: under reasonable
  assumptions, any labeling of logical sentences with real
  numbers will be consistent with probability

* Measurement issues; numeric issues

