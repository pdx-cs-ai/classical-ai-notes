## Information Gain

* Select features that best split the instances by class

* Given \\(N\_-\\) negative values, and \\(N\_+\\) positive values,
  the probabilities of positive and negative instances are
  given by

  \begin{eqnarray\*}
  \mathrm{Pr}(+) &=& \frac{N\_+}{N\_+ + N\_-} \\\\
  \mathrm{Pr}(-) &=& \frac{N\_-}{N\_+ + N\_-}
  \end{eqnarray\*}

  and the entropy of the distribution is given by

  $$ U = -(\mathrm{Pr}(+) \lg \mathrm{Pr}(+) + \mathrm{Pr}(-) \lg \mathrm{Pr}(-) $$
  
  where \\(\lg\\) is the logarithm base 2. (Note that for
  comparison purposes the base doesn't really matter.)

* The gain of a split on a feature \\(f\\) is the negation
  of the weighted entropy of the two sides of the split

  $$ \begin{eqnarray\*}
  \mathrm{Pr}(f\_+) &=& \frac{N\_{f\_+}}{N} \\\\
  \mathrm{Pr}(f\_-) &=& \frac{N\_{f\_-}}{N} \\\\
  G &=& -(\mathrm{Pr}(f\_+) U(f\_+) + \mathrm{Pr}(f\_-) U(f\_-)
  \end{eqnarray\*} $$

## Information Gain Example: Class Entropy

* Here's five instances:

        1,0,1,1
        0,0,1,0
        1,1,1,0
        1,1,0,0
        0,1,1,1

* Let's calculate the class entropy of the whole mess.

  $$ U = -0.6 \lg 0.6 - 0.4 \lg 0.4 \approx 0.97 $$

* Note that for *comparing* features, we always start
  with the same class entropy, so we can leave that
  term out if we like, in which case the "gain" will
  be negative but still perfectly good for comparison.

# Information Gain Example: Feature 1 Gain

* Split instances on the feature

        1,0,1,1
        0,0,1,0

        1,1,1,0
        1,1,0,0
        0,1,1,1

* For each split, calculate the class entropy for
  for that split

    * Entropy for first (0) feature split: probability
      of class 0 = 0.5, probability of class 1 = 0.5

      $$ U = -0.5 \lg 0.5 - 0.5 \lg 0.5 = 1 $$

    * Entropy for second (1) feature split: \\(\mathrm{Pr}(\mathrm{cl}=0) =
      1/3\\), \\(\mathrm{Pr}(\mathrm{cl}=1) = 2/3\\)

      $$ U \approx -0.33 \lg 0.33 - 0.66 \lg 0.66 \approx 0.92 $$

* Now weight each entropy by the probability of being in
  that set

  $$ U' \approx 0.4 \cdot 1 + 0.6 \cdot 0.92 = 0.95 $$

* Gain is initial entropy \\(U\\) minus the final
  entropy \\(U'\\), so

  $$ G \approx 0.97 - 0.95 = 0.02 $$

# Information Gain Example: Feature 2 Gain

* Split instances on the feature

        1,1,0,0

        1,0,1,1
        0,0,1,0
        1,1,1,0
        0,1,1,1

* Same calculation as before:

  $$ \begin{eqnarray\*}
  U(0) &=& 0 \\
  U(1) &=& 1 \\
  G &\approx& 0.97 - 0.2 \cdot 0 - 0.8 \cdot 1 = 0.17
  \end{eqnarray\*} $$

# Information Gain Example: Feature 3 Gain

* Split instances on the feature

        1,1,0,0
        0,0,1,0
        1,1,1,0

        1,0,1,1
        0,1,1,1

* Same calculation as before:

  $$ \begin{eqnarray\*}
  U(0) &\approx& 0.92 \\\\
  U(1) &=& 1 \\\\
  G &\approx& 0.97 - 0.6 \cdot 0.92 - 0.4 \cdot 1 = 0.02
  \end{eqnarray\*} $$

* Our gains are 0.02, 0.17, 0.02, so the best feature to
  split on is feature 2.
