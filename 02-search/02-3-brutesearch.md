## Sliding Tile Puzzles: Breadth-First Search

* Examine states in increasing order of distance from start

* Guaranteed to eventually hit the goal state if exists

* Will not terminate if no solution because "looping"

    * Use a stop list as before

    * The alternative is to organize the states in some DAG
  
    * Note that the stop list could be used as a priority queue
      for Dijkstra's Algorithm: This is arguably the way to
      proceed here

## Sliding Tile Puzzles: Depth-First Search

* We could use depth-first search in an attempt to save
  memory. From start state

    * Try each possible first move

    * Recursively solve the resulting state

    * Never revisit a state *along the current path*

* Will construct long paths for no reason

* Still need a stop list (even more)

##  Sliding Tile Puzzles: Depth-First Iterative Deepening

* Could use *depth-first iterative deepening* (DFID): artficially
  cut off search at depth 1, 2, 3, …

* DFID advantage: uses memory proportional to depth, finds
  shortest path

* Complete but not *systematic*: "redoing" search is not
  that expensive because branching factor
