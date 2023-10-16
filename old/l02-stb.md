## Games

* We study games because they are

    * Hard: seem to require some intelligence

    * Pre-abstracted: "simple" models, clear rules, "win
      condition"

* "Game" is a bit ill-defined: certainly includes
  single-agent and multiple-agent things

* Games range from competitive to cooperative

## Shut The Box

* [Shut The Box](https://en.wikipedia.org/wiki/Shut_the_Box)
  is a simple multi-player probabilistic dice
  [game](http://www.shut-the-box.net)
  vaguely related to Yahtzee

* We will use the single-player 9-digit game with "digital"
  ("say what you see") scoring

* I have built a single-player
  [solver](http://github.com/BartMassey/digitgame) for this
  game. We will learn how it works. Today is not that
  day

* (rules, demo)

* I've also built a weaker
  [heuristic AI](http://github.com/pdx-cs-ai/shut-the-box)
  for this game. That is what we'll talk about today

## Shut The Box: Setup

* "Obvious": Represent a *state* as a set of remaining
  digits and a dice roll

* Apparently a state is an instance to be solved

* Solution? A "better" state

  * Can be greedy: pick the next state with lowest score

  * Greed is not necessarily good: actual scoring is at the end

  * Now we're balancing two things: lower score / "better" numbers

## Shut The Box: Code

* AI code is a lot of setup per unit intelligence

* I've done this setup for you here

* Let's look at the code

## Shut The Box: Player

* Just choosing randomly from the legal moves is not AI (or
  is it)?

* But it's a good place to start

* I then built stronger heuristic rules and evaluated via
  play

## Shut The Box: Evaluating the Player

* Could try to do a full analytic evaluation

* Much easier to play a bunch of games and see how it does

* What is the success measure? Mean? Number of perfect
  scores? Something else?

* Will the AI vary depending on what success measure is
  chosen? (yes)
