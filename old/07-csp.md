## States Of Variables

* State is assignment of *values* to *variables* under *constraints*

* Three kinds:

    * Constraint Satisfaction Problem: Find an assignment
      that satisfies constraints

    * Optimization Problem: Find an assignment that
      optimizes some *objective function*

    * Constraint Optimization Problem: Find assignment that
      optimizes under constraints

## CNF 3-SAT

* Variables are "atoms" in logical formula; values are
  *true* or *false*

* Formula is in *Conjunctive Normal Form* with at most 3
  variables per clause: e.g.

        (A or not B or C) and (not A and B or C) and (A or B or C)

* Constraint is that the formula be true: every clause must
  have at least 1 true literal

     * For this formula take A=f, B=f, C=t

* In general, problem is NP-complete

## Complete Search For CSPs (3-SAT)

* Let's add a third "unassigned" state for variables. This
  extends the state space to include *partial assignments*

* Algorithm (DPLL):

    * Try assigning A=t. If the formula has no
      false clauses, try recursively solving the remaining
      variables

    * Try assigning A=f. If the formula has no false clauses,
      try recursively solving the remaining variables

    * If no solution has been found, return unsat

* This is breadth-first search to a fixed depth (number of
  variables)

## Variable Ordering

* Free choice at each state of which variable to solve for next

* Heuristics are probably helpful here:

    * Branch on variables that have large number of
      occurrences (to fail quickly)

    * Branch on variables in short clauses (to fail quickly)

* Generally "most constrained first"

## Value Ordering

* Free choice at each state of what order to try values for
  chosen variable

* Heuristics are probably helpful here:

  * Try value that satisfies most clauses (to succeed quickly)

  * Try value that produces most short clauses (to make
    problem easy to solve) [Crawford *et al*]

* Generally "least constraining first"

## Optimization for CSPs

* Same basic search framework

* Complete search can find an optimal solution — in principle

* Heuristics will involve the scoring of a partial or total
  solution — greed is good
