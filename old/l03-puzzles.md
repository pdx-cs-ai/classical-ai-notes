## Solving Shut The Box

* What does it mean to solve a probabilistic game?

* Suppose we had a table that told us the *expected value*
  of every possible position

* Then "perfect" play would mean always choosing the move
  that minimized EV (STB is upside-down)

* How many entries does such a table have? 2^9 = 512

* Build the table using *dynamic programming*

     * EV of a shut box is 0

     * EV of a box with one digit open is computable from EV
       of all successor states

     * Same for 2…9 digit boxes

## Let's Solve STB!

* http://github.com/pdx-cs-ai/stb

* EV of starting position is about 14762

* Maybe want to maximize shut boxes? Minimize EV(log(*s*))?

* Could calculate a fancier table useful for competitive play

## Search In Sliding Tile Puzzles

* See the course notes on Sliding Tile Puzzles

* http://github.com/pdx-cs-ai/slider

* Can solve 8-puzzle (3×3) instances reasonably quickly

* 15-puzzle (4×4) is pretty hopeless
