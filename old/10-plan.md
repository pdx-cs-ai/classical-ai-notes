## Planning

* Planning is related to scheduling, but:

    * Operators may (often will) have zero duration

    * Can perform an operation as many times as needed

    * Operations have preconditions and postconditions

## Blocks World

* Standard planning environment:

    * Consider blocks A, B, ... in stacks on a table in some way

    * Want to rearrange them some different way

    * Operations:

        * Move a top block to (infinite) table to start a
          new stack

        * Pick up the top block of some stack and place it
          on top of a different stack

* There is an *easy* algorithm that takes at most *2n*
  operations for *n* blocks…

## General Purpose Planning

* Describe operators and environment in some generic way

* Have a GP planner try to find a plan

* Blocks World instances are *hard* for GP planners (!?)

## Optimal Blocks World

* Want a *shortest* restacking plan

* Turns out this problem is NP-hard (PSPACE-complete!?)

* Worse yet, finding an *approximately* shortest plan is
  NP-hard (?!?)

* But can solve reasonable-sized instances by… A✶ search!

* Best planners do big state-space change to reduce search

## Advanced Planning

* Logical formulation of planning problems for GP planners

* Optimal-cost planning

* Planning under uncertainty — what if:

    * Environment isn't really known for sure in the future

    * Operators might not do what they're supposed to
