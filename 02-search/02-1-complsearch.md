## Intelligence and the Future

* Intelligence is partly about "thinking ahead"

* A complicated problem is solved a piece at a time, or an
  action at a time. Steps interact

* Looking ahead gets complicated fast

* AI has spent a long time thinking about this problem,
  and has found some fairly fancy techniques

* Ultimately P ≠ NP (probably), so must abstract or approximate

## Computers Search Good

* A computer can construct future states from current states
  quickly and perfectly

* Humans are bad at this; "easy" AI might want to
  leverage this

* Problems like route-finding, scheduling, planning,
  puzzle-solving, games, robotics have gone there

* Pattern-matching, machine learning, etc can be *augmented*
  with search

## State Spaces

* A *state* is a situation. It is static in time

* A *state space* is a graph of situations.

* The *neighbors* of a state *s* in a state space are the graph
  edges — states that can be reached from *s* by some atomic
  action

## Road Maps and State Spaces
  
* In a fancy road map, the states are junctions on the
  map. The state space is literally the graph of roads
  and junctions

* An AI could proceed heuristically toward the goal by
  always choosing the route that gets closer to it

* Dead-ends and side-trips are a big problem, though

## Search The Map

* To find a short route, it's probably better to look at
  least a little ahead: traverse the graph a bit and see
  where you end up

* Watch out for backtracking and loops: use a *stop list*

* Ultimately, this is BFS / DFS / Dijkstra search

* Problem is usually boring for modern computers
