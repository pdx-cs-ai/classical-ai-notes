## The Game of "15"

* Game I found in some old Martin Gardner book

* Rules:

    * Start with tiles labeled 1-9 in the center
    
    * Players take turns choosing a tile from the pile
    
    * Any time a player holds 3 tiles whose total is 15,
      they win

* Perfect information, alternating, terminating, zero-sum: check

* (There's a fantastic trick to playing this game)

## Solving "15"

* Build a negamax search <http://github.com/pdx-cs-ai/nkt>

* Can cheaply calculate value of any position in practice

* Or can calculate the value of all possible positions and
  record them
  
    * (How many possible positions are there?)

## "NKT": Generalizing "15"

* We will generalize to "NKT": N tiles, exactly K tiles in a
  win, winning total is T

* Next natural size is N=15, K=4, T=28, so we'll call this
  game "28"

* Calculating the value of the starting position is going to
  take a *long* time
