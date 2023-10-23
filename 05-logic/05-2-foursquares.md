## The Four Squares Puzzle

* Given these four pieces

        +-----+  +-----+  +-----+  +-----+
        |  3  |  |  3  |  |  2  |  |  1  |
        |4   1|  |2   4|  |4   1|  |2   4|
        |  2  |  |  1  |  |  3  |  |  3  |
        +-----+  +-----+  +-----+  +-----+

  we can rearrange and rotate them arbitrarily and assemble
  them into a square

        +-----+-----+
        |  4  |  3  |
        |3   1|1   4|
        |  2  |  2  |
        +-----+-----+
        |  2  |  4  |
        |3   1|2   3|
        |  4  |  1  |
        +-----+-----+

  Can we make a square such that all the edges match?

* Obvious approach: Plain ol' state space search. Pain to
  code, but should run very fast: 3! × 4^4 = 1536 states
  
* Ah, but 3×3, 4×4, etc…

## Four Squares using QPROP

* Let's solve this puzzle by

  * Writing a QPROP formula whose models are solutions

  * Converting the formula to a big PROP formula

  * Looking for SAT model

  * Translating the model back to a puzzle solution

* PROP SAT solvers are scary fast, incorporating piles of
  clever search techniques we don't want to rewrite from
  scratch

## Modeling Four Squares: Setup

* Number the pieces 1..4, the positions in the square
  1..4. We will number the square positions clockwise
  starting from the upper left. We will number the edges of
  the piece counterclockwise starting from the right edge.

        l(s, p) iff piece p is in square s  (location)

* Number the coordinates of the edges of each square 1..4

        m(s, e, n) iff piece in square s at edge e is n (match)

* Number the edges of each piece 1..4

        v(p, e, n) iff piece p at edge e is n (value)

* Number the rotations of each piece 0..3. Rotations will be
  counterclockwise.

        r(p, k) iff piece p has rotation k


## Modeling Four Squares: Basic Constraints

* Every piece is at some location

        forall s . exists p . l(s, p)

* No location contains more than one piece

        forall s . forall p1, p2 | p1 =/= p2 . not l(s, p1) or not l(s, p2)

* First piece is in first corner (remove rotational
  symmetry)
  
        l(1, 1)

* Every location has a piece

        forall p . exists s . l(s, p)

* No piece is at more than one location

        forall p . forall s1, s2 | s1 =/= s2 . not l(s1, p) or not l(s2, p)

* Every piece is at some rotation

        forall p . exists k . r(p, k)

* No piece has more than one rotation

        forall p . forall k1, k2 | k1 =/= k2 . not r(p, k1) or not r(p, k2)

## Modeling Four Squares: Fancy Constraints

* Square coordinates are a function of piece location and rotation

        forall s, p, k, e, n .
            m(s, e, n) if l(p, s) and r(p, k) and v(p, (4 - k + e) mod 4, n)

* No square edge can have more than one value

        forall s, e . forall n1, n2 | n1 =/= n2 .
            not m(s, e, n1) or not m(s, e, n2)

* Edges must match

        forall s1, e1, s2, e2 |
           s1 = 1 and e1 = 1 and s2 = 2 and e2 = 3 or … .
               forall n . m(s1, e1, n) iff m(s2, e2, n)

## "Grounding" As PROP

* Treat predicates as subscripted atoms: `l(s, p)` → `L#s#p`

* Build a numbering function so that atoms run `A1`…`An`

* Write for loops that generate CNF clauses

* Basic constraints are already CNF; fancy constraints need
  some work

* Fancy constraint first clause count 256, total clause
  count less than 10× that

* Number of atoms for `m` predicate 64, total variable count
  less than 10× that

## Solving An Instance of Four Squares

* Add in clauses describing the instance pieces

        v(1, 1, 1)
        v(1, 2, 3)
        …

* Run the SAT solver

* Take model (yes, this problem is solvable) and find the
  `l` and `r` atoms that are true. This gives the location
  and rotation of each piece!

## Extending To Nine Squares And Beyond

* Extend the piece and square numbering

* Modify the fancy matching constraint

* That's it!

## Sudoku Example

* Sudoku SAT generator / solver in Haskell
  [sudoku-sat-hs](http://git@github.com/pdx-cs-ai/sudoku-sat-hs)
