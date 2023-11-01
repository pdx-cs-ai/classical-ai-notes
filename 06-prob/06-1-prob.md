## AI, Decision Making, and Probability

* About decision-making

* Uncertainty, likelihood, and probability

* Decision-theoretic methods

## Probability

* Idea: *chance* and *likelihood* are important concepts for real
reasoning

* Method: assign probabilities to events and combinations of events

* Reason from model using calculation

* This is a general plan:

            Evidence -----------------> Conclusions
               |                            ^
               |                            |
               v                            |
             Model   -----------------> Extrapolation

## Probability of Events

* Domain: events

    * *pr(E)* is probability that event *E* happens

    * *pr(E) = #E / (#E + #¬E)*

    * For a coin *pr(H) = #H / (#H + #T) = 1 / 2*

    * For a pair of dice:

         * *pr(R7) = #R7 / #R*
         
         * *#R7 = #{(1, 6), (2, 5), (3, 4), …} = 6*

         * *#R = #{D×D} = 36*
         
         * *pr(R7) = 6 / 36 = 1/6*

         * Check with computer program
           [prob7](http://github.com/pdx-cs-ai/prob7)

## Probability of Logical Situations

* Domain: propositional formula

    * *pr(p)* is probability of logical combination of events

    * *p* is a prop formula

* Priors and conditionals

    * *pr(p|q)* is prob of *p* given *q* (easy to get backward)

## Axioms Of Probability

  * equivalence: if *p ≡ q* then *pr(p) = pr(q)*

  * range: *0 ≤ pr(p) ≤ 1*

  * negation: *pr(¬p) = 1 - pr(p)*

  * conjunction: *pr(p and q) = pr(p) pr(q|p) = pr(q) pr(p|q)*

## Derived Probability Rules

* disjunction: *pr(p or q) = pr(¬(¬p and ¬q)) = 1 - pr(¬p and ¬q)*

* Bayes's Rule: 

          pr(q) pr(p|q) = pr(p and q) = pr(p) pr(q|p)
          pr(q) pr(p|q) = pr(q|p) pr(p)
          pr(p|q) = pr(q|p) pr(p) / pr(q)

## Independence

* When *p* and *q* are conditionally independent *pr(p|q) = pr(p)*

    * By Bayes's Rule

            pr(q|p) = pr(p|q) pr(q) / pr(p)
                    = pr(p) pr(q) / pr(p)
                    = pr(q)

    * In this case, conjunction gets easier

        * *pr(p and q) = pr(p|q) pr(q) = pr(p) pr(q)*

* When *p* and *q* are strictly independent *pr(p and q) = 0*

    * In this case, disjunction gets easier

            pr(p or q)
            = 1 - pr(¬p and ¬q)
            = 1 - pr(¬p) pr(¬q)
            = 1 - (1 - pr(p))(1 - pr(q))
            = 1 - (1 - pr(p) - pr(q) - pr(p) pr(q))
            = pr(p) + pr(q) + pr(p) pr(q)
            = pr(p) + pr(q)

