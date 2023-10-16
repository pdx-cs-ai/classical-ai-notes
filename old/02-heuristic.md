## Problem and Instance

* Basic idea from algorithms

* An *instance* is

    * Some specific description of a situation

    * Some description of what is wanted in that situation

* A *problem* is a collection of related instances

* A *class* is a collection of related problems

## Example: Sorting

* Instance of natural-number sorting

        Given: 1 3 2
        Produce: The three numbers arranged in increasing order

* Natural Number Sorting Problem

        Given: A sequence of natural numbers
        Produce: The sequence arranged in increasing order

* Class of sorting problems includes natural-number sorting,
  floating-point number sorting, string sorting, 2D sorting,
  nD sorting, etc

## Computational Complexity

* Nearly all sorting problems have algorithms with
  worst-case asymptotic running time *O(n log n)* where *n*
  is the length of the sequence

* If the previous sentence looks unfamiliar or confusing to
  you, you probably aren't ready for this course yet. Get
  out, go take a good Algorithms class (our CS 350), and
  then come back in a future quarter

## AI Problems

* In AI, a problem is likely to be

    * Fuzzily specified: want a "smart answer" that is "good enough"

    * Hard: No efficient algorithm is known to exist for
      large / hard instances

    * Human-tractable: Humans demonstrably do a reasonable job
      on real-world instances

* "AI Complete" problems are those for which a good solution
  will require general intelligence

* (Conversely, a general intelligence would handle standard
  algorithms problems)

## Problem: Pathfinding

* *Instance:* A map

* *Solution:* A good route through that map

* Issues:

    * How much detail is in the map? Like a Google map? A
      treasure map? A photo?

    * Similar: How is the map represented? A graph? An
      image? Something else?

    * What is a "good" route? Short? Low-effort? Safe?

* Dijkstra's Algorithm or similar search is good for small
  instances of simple problems

* Super-fancy AI techniques are used on some kinds of
  real-world problem

## Abstraction

* Abstract away "irrelevant" details

* For example, take image to Google Map (fancy graph),
  Google Map to simple graph

* Hard to tell what is irrelevant
