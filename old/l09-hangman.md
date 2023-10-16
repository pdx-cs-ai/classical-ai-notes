## The Game of Hangman

* "Defendant" picks a word, writes blanks for
  its letters, draws a gallows


        ----
        |  |
        |
        |
        |
        |       _ _ _ _ _ _ _ _


* "Prosecution" guesses letters of the word in turn.
  Guessing a letter not in the word causes a body part
  to be added to the gallows. Guessing a letter in the word
  fills in all occurrences

        ----   z w
        |  |
        |
        |  O
        |  |
        |      _ _ _ _ _ _ i _



* "Trial" is over when word is completed or def is hanged

        ----   z w e a o u
        |  |
        |
        |  O
        | /|\
        | / \  _ _ _ _ _ _ i c

## Hangman Prosecution and Utility

* What letter should pros guess first?

* Let's assume that def chose random 8-letter word
  from known dictionary

* Let's further assume that a found letter has a uniform
  value of 1

* Then find

        argmax [l in 'a'..'z'] (l in word) pr(word|dict)

* This is an easy calculation: 'e' occurs in 2/3 of the
  8-letter words (see `bestguess.py`)

## Hangman: My Assumptions Are Weak

* Problem: because 'e' is so common, hitting it doesn't
  necessarily narrow things down *so* much
  
* Value function should be based on expected chance of
  winning after hitting *or missing* the letter

* Problem: Def isn't choosing uniformly — will pick "hard"
  words

* Need to know probability given defense strategy
  *pr(word|ds(dict))*

* So

        argmax [l in 'a'..'z'] v(win with word) pr(word|ds(dict))

## Hangman: Nash Equilibrium

* Ugh. *ds(dict)* will depend on guessing strategy

    * "Good old rock. Can always count on rock"

* Adversary games are hard. But Nash Equilibrium exists and
  can *in principle* be calculated

* Current research for me

## Information Theory

* Consider these strings of bits

        0111111111111111

        0101100010011011

    * `x` is boring and easy to describe. You could predict
      the "next value" pretty reliably

    * `y` is complicated

* Shannon *et al*: `x` has "less information" than `y`

* Information content can be viewed as a utility
  function. The *entropy* of a set is given as

        u(S) = sum [i in S] pr(i) lg 1/pr(i)
             = sum [i in S] - pr(i) lg pr(i)

  For our sets (strings)

        u(x) = - pr(0) lg pr(0) - pr(1) lg pr(1)
             = - (1/16) lg (1/16) - (15/16) lg (15/16)
            ~= 0.337

        u(y) = - pr(0) lg pr(0) - pr(1) lg pr(1)
             = - 2 (8/16) lg (8/16)
             = -2 × 0.5 × -1 = 1

## Hangman: Entropy-Based Prosecution

* Pros wants to get to a state where there is only one
  choice

* Standard trick: pick the letter that has the greatest
  expected chance of reducing the entropy the most

        argmax [l in 'a'..'z']
            (1 - sum [p in part(l, dict)] u(l))) pr(l)

* Does this still produce 'e' as the initial guess? It does

* We have taken into account the "cost of gathering
  information" as part of the utility: we don't want to make
  a guess that costs us a body part unless we get a lot
  of information from it

## Demonic Hangman

* Consider "Demonic Hangman": Def cheats as desired by
  changing the word in a way consistent with the guesses so
  far

* Now we almost *have* to use entropy to narrow Def down to
  only one choice quickly
