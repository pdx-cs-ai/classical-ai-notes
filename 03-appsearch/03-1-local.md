## Local Search

* Maybe give up on all this fancy memory-intensive search?
  Our initial random-walk sliding-tile solver worked pretty
  good!

* Use the heuristic to guide the random walk?

* Problem: Local Minima. May get to a state *s* all of whose
  neighbors are worse than *s*

* Even if moving out randomly, may immediately return to *s*

* Solution: Mix greedy moves with random moves randomly, say
  50/50. The random moves are "noise moves" and might walk
  out of local minima

* Solution: After a while, just "restart" and hope the
  random walk goes better next time

* For satisfiable instances, this works *really well* in practice

* Optimality is generally terrible, though: long paths still

## Sliding Tile Puzzles: Local Search

* We have a couple of heuristics lying around from earlier

    * Total tile distance

    * Lexical out-of-place tiles

* Throw something together and tune:

    * Noise level

    * Restart rate

## Sliding Tile Puzzles: Find An Algorithm

* Humans who play with sliding tile puzzles for a while
  eventually find an efficient solution algorithm

    * Put each tile in place in order by moving it there

    * When this is not possible, use a "rotation macro"
      to make it possible

    * When the puzzle is unsat, this will be revealed at the
      end when the rotation macro doesn't work

* Produces "short" paths, but perhaps not shortest

* "Easy" to teach a computer this algorithm. Can it figure
  it out on its own? Don't know

## Local Search for CSPs (3-SAT)

* Start with a random assignment of values to variables

* Neighbors are change of value of some variable: "flips" in
  3-SAT

* Heuristic: Number of satisfied clauses (more is better)

* Use "noise moves" and "restarts" as usual to speed up
  search
