## Iterative Deepening

* Search incrementally 2, 3, 4, 5… until running out of time

* Use the best move (and value) from last completed depth

* Use a heuristic to decide whether to start the next search

## Transposition Table

* Transposition: two different move sequences take you to
  the same state
  
* Transpositions waste work: will re-search

* Idea: keep a "stop list" of position values —
  "transposition table"

* But exponential memory!

* Treat ttable as a *cache*: do random replacement or
  something
  
## TTable Move Ordering

* Use ttable from shallower depth for alpha-beta move
  ordering
  
* Works very well in practice
