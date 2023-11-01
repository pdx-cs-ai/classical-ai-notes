## First-Order Logic: A Review

* First-order Formula:

    * "Predicates": Atoms that can take arguments (other
      predicates, variables)

    * "Variables": Value is predicate

    * "Quantifiers": "exists" and "forall" "bind" variables

    exists z . forall x . plus(x, z, z)
    exists z . forall x . plus(z, x, z)
    forall x, y, z . plus(succ(x), y, z) -> plus(x, y, succ(z))
    forall x, y, z . plus(x, succ(y), z) -> plus(x, y, succ(z))

* Things to do: Normalization (polytime), checking
  (polytime), sat (undecidable), tautology (undecidable)

    not F is unsat => F is "valid"

    search for F, search not F

* Common to extend with theories: "Satisfiability Modulo
  Theory" (SMT) solver. In particular, arithmetic

* Tools: Theorem prover / model checker, e.g. `Z3`

## Quantified Propositional Logic

* Quantified Propositional Formula ("QPROP"): First-order
  logic, but all variables are bound and have a given set of
  discrete values they could take on

* Can turn (small) QPF into (large) PROP:

  * forall → and, exists → or

  * predicates are replaced by subscripted atoms

* Compact notation for PROP, reduces mistakes

