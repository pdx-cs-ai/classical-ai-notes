## Sliding Tile Puzzles: Heuristic Search

* Prefer moves that make progress toward the goal

* Wat? Well, humans try to solve one tile at a time from
  first to last as much as possible. *Heuristic:* Number of
  in-place tiles at the front, larger is better

* Maybe computers can do better? *Heuristic:* add up Manhattan
  distance from each tile to its goal position, smaller is better

* Heuristic search doesn't really help the unsat problem

## Sliding Tile Puzzles: Dijkstra's Algorithm

* Blind (no heuristic) *best-first* search

* For this problem, exactly the same as BFS!

* If the *costs* of moves are different (in some other
  problem), this can do better

## A✶ Search

* Maybe adding a heuristic to Dijkstra would help

* But want to preserve shortest-path

* A✶ ("*a-star*") idea: use an "admissible"
  heuristic — one that is always "optimistic"

* The heuristic guides us toward the goal: for example,
  Euclidean distance from the goal on a map

* Basic idea is Dijkstra, but instead of expanding nodes in
  order of least distance from the origin, expand in order
  of least distance from origin *plus* heuristic distance to goal

* *g(s)* is the distance of state *s* from the origin

* *h(s)* is the heuristic distance of state *s* from the goal

* "0" is an admissible heuristic, but boring

* A perfect heuristic eliminates all missteps

## Correctness Of A✶ Search

* Does A✶ preserve the shortest-path property? It does!

* The proof is tricky and relies on the heuristic being
  admissible 

  * Assume A✶ found a longer "bad" path first

  * That means at some state on the bad path a "correct"
    next state was not chosen, but instead some worse next
    state

  * At some state *sc* (maybe the goal), the paths converged again

  * But at *sc* the bad path and the good path now have the
    same heuristic value, but the bad path is longer
    
  * We must thus proceed by expanding the good path until it
    reaches *sc*

* [Original Paper](https://web.archive.org/web/20160322055823/http://ai.stanford.edu/~nilsson/OnlinePubs-Nils/PublishedPapers/astar.pdf)

* Textbook also discusses. Also CLRS

## Sliding Tile Puzzles: A✶

* Fairly simple modification to Dijkstra

* Use a priority queue (min-heap), but keyed on
  *g(s) + h(s)* instead of just *g(s)*

* No separate stop list is needed

* Expands minimum number of states to goal (theorem)

* Complete search algorithm: will stop when all states
  have been examined

* Will actually stop when out of memory
