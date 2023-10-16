## Problem Representation

* Solving a problem with a computer: 

    * Accurately describe the problem
    * Choose an instance representation in the computer
    * Select an algorithm to manipulate the representation
    * Execute

## Properties of Representations

* What properties of representations are important?

    * compactness: must be able to represent big instances efficiently

    * utility: must be compatible with good solution algorithms

    * soundness: should not report untruths

    * completeness: should not lose information

    * generality: should be able to represent all or most
      instances of interesting problems

    * transparency: reasoning about/with representation is efficient, easy

## Standard Representations

* What instance representations do people choose?

    * database: collection of facts
    * neural net: collection of "neuron weights"
    * functional: collection of functions
    * **logical: collection of sentences**

## Prop Logic: A Review

* Propositional Formula ("PROP"):

    * "Atoms" that can be either true or false. Names are
      commonly subscripted

    * "Connectives": *and*, *or*, *not* + parentheses

* Things to do:

    * Normalization: transform a formula into some
      standard form (polytime)

    * Checking: for a given assignment, is a formula true
      or false? (polytime)

    * Satisfiability ("SAT"): is there an assignment that
      makes the formula true? (NP-complete)

    * Tautology: does every assignment make the formula true?
      (NP-complete, extra variables) AKA theorem-proving

## First-Order Logic: A Review

* First-order Formula:

    * "Predicates": Atoms that can take arguments (other
      predicates, variables)

    * "Variables": Value is predicate

    * "Quantifiers": "exists" and "forall" "bind" variables

* Things to do: Normalization (polytime), checking
  (polytime), sat (undecidable), tautology (undecidable)

## Quantified Propositional Logic

* Quantified Propositional Formula ("QPROP"): First-order
  logic, but all variables are bound and have a given set of
  discrete values they could take on

* Can turn (small) QPF into (large) PROP:

  * forall → and, exists → or

  * predicates are replaced by subscripted atoms

* Compact notation for PROP, reduces mistakes

