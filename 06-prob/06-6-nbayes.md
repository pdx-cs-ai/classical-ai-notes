## Bayesian Classification

* A form of machine learning

* Given a bunch of evidence for and against a thing, decide
  whether the thing

* Formulate as a classic probability problem

         pr(H|E1=v1, E2=v2, ... En=vn)

* We can use Bayes Rule to turn this around

           pr(E1=v1, E2=v2, ... En=vn|H) pr(H)
         = -----------------------------------
             pr(E1=v1, E2=v2, ... En=vn)

* Now we "just" need the probabilities: perhaps we can examine
  a bunch of classified examples and compute them

## Binary Naïve Bayes

* Problem: There's a huge space of possible values here;
  likely no way we'll get enough examples to accurately
  estimate probabilities

* Let's reduce the state space:

    * Binarize the hypothesis and evidence. Now the state
      space size is *2^(n+1)* for *n* features

    * Naively assume that all the features are independent
      (they aren't). Then we can just replace the
      conjunction with a product

                        pr(E1=v1|H) pr(E2=v2|H) ... pr(En=vn|H) pr(H)
             pr*(H|E) = ---------------------------------------------
                        pr(E1=v1) pr(E2=v2) ... pr(En=vn)

* Sadly, the naive assumption means that the probabilities
  will be too low, since interactions won't be counted: but
  comparable for H true and false. So

        H iff pr*(H|E) > pr*(not H|E)

* Note that this comparison drops the denominator, which is nice

* Games might be played to make the computation more tractable

## m-Estimation

* What we have so far:

                             pr(E1=v1|H) ... pr(En=vn|H) pr(H)
         pr*(H|E1=v1, ...) = ---------------------------------
                               pr(E1=v1) ... pr(En=vn)


* Consider the case where `pr(Ei=vi|H)=0`. If we try to
  classify an instance of this form, this will make the
  whole product 0, regardless of what the other terms tell
  us

* (Worse yet, consider `pr(Ei=vi)=0`. Oops. We drop the
  denominator in the comparison, but…)

* The training instances are *sampled* from a notionally
  large space. If we see no count in *n* training
  instances, that means either that the frequency is less
  than *1/n* or we got unlucky

* Assume that there is some fraction *m* associated with the
  undersampling — usually use ½

* Now adjust the probabilities:

                      |S[Ei=vi|H]+m|
        pr(Ei=vi|H) = --------------
                         |S[H]+m|

* Zeros are gone, calculation *may* be more accurate

## Numerics

* We are asked to compute a product of potentially many terms:

        pr(E1=v1|H) ... pr(En=vn|H) pr(H)

* All terms are ≤ 1

* When *n* is large, this product will be *small*. Maybe
  too small. Floating point underflow could happen

* We are comparing

        pr(E1=v1|H) ... pr(En=vn|H) pr(H) >
        pr(E1=v1|not H) ... pr(En=vn|not H) pr(not H) ?

* Take *log* on both sides:

        log(pr(E1=v1|H) ... pr(En=vn|H) pr(H)) >
        log(pr(E1=v1|not H) ... pr(En=vn|not H) pr(not H)) ?

        log(pr(E1=v1|H)) +  ... + log(pr(En=vn|H) + log(pr(H))) >
        log(pr(E1=v1|not H)) +  ... + log(pr(En=vn|not H) + log(pr(not H))) ?

* These sums should not underflow
