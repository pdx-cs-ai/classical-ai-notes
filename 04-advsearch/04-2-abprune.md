## Depth-limited Negamax Search

* We want an *approximate* value for a position, and will
  tolerate an *approximately* best move

* For chess, we use "piece value" as a heuristic
  approximation.

* Heuristic should look at both sides, so subtract on-move
  value from opponent (zero-sum)

* But just doing this right away might not be the best
  plan. Let's look ahead some fixed depth and use negamax to
  combine heuristic values

## Chess In n Moves

* Imagine chess but after n moves whoever is "ahead on
  points" (material value) is the winner

* Chess in one move: always take the queen if possible

* But as n gets larger, game looks more and more like chess

* Depth-limited heuristic search converges on true value of
  position (theorem, with caveats)

## Alpha-Beta Pruning

* Generalization of Win Pruning. Hard to explain:

    * Imagine you find a forced score of 3 for some state *s* in the
      middle of the search

    * Imagine further that in some earlier state *t* at the same
      level you had found a score of 2

    * Then your opponent (parent) would never let you get to
      *s*: they would avoid it

    * So there's no point in searching *s* any further

[alpha-beta search tree](http://wiki.cs.pdx.edu/mc-howto/tree-2.png)

## Alpha-Beta Implementation

* "Alpha-Beta window" keeps track of best score for
  side not on move (alpha) and side on move (beta)

* Prune when computed score exceeds beta

* Game is zero-sum. On recursion, flip and negate the
  window: (alpha, beta) → (-beta, -alpha)

* Window starts with (-max, max). When searching, keep
  bumping alpha up as better moves are found

## Effectiveness of Alpha-Beta

* Depends on move ordering: a good move for the side on move
  will "close the window" a lot, so want to try good moves first

* With optimal move ordering, will effectively *double the
  depth* of the search by pruning; runtime of depth-4
  without = runtime of depth-8 with

* Note that alpha-beta *never changes the answer*: it only
  prunes states that provably don't matter
