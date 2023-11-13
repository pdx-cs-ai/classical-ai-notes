## Evolution

* Another biological model "inspiring" computation

* Idea: Nature fits populations to environments

    * "Natural Selection" causes fittest elements of
       population to be preserved
    
    * Genes act as a "memory" of good features

    * Combining the genes of two individuals gives
      a combination of their features — big search space

## Genetic Algorithm

* Specify "genes" representing features to be learned

* Construct a random "population" of *n* "genomes"

* Repeatedly

    * Remove genomes scoring lower on training set

    * Repopulate to size *n* by combining pairs from
      remainder of population

    * Optional: randomly "mutate" elements of population
      by changing genes

## Removal Of Less-Fit Instances

* Could just sort by score and remove lowest scorers

* Problem: "genetic diversity" — all the high scorers tend
  to look alike

* Better diversity through "tournament selection": take
  pairs of instances and remove the one with the lower score

## Repopulation

* Typically select pairs randomly

* Methods for combining p1, p2:

  * "Crossover" selects some (random?) number of genes
     at start of p1, then fills in with genes from end
     of p2 — preserves positionally-related structures

  * "Shuffling" selects each gene randomly from p1 or p2 —
    mixes well

## Loss Of Diversity

* Big problem: After a while, population can start to look
  all alike; then combining doesn't do anything

* Increase the population: Easy mode, but slows things down

* Adjust amount of depopulation: Remove too many = loss of
  diversity. Remove too few = slow convergence

* Adjust mutation rate: For largeish populations mutation is
  rarely necessary. Adjust rate for fastest convergence

* Use similarity for depopulation: Cluster similar instances
  and remove the worst ones in each cluster

* Choose a better genome: Feature engineering can reduce the
  search space size

## Fancy GAs

* "Predator / Prey" and other ecosystem approaches

* "Biome" for covering different parts of the search space
  with different populations

## Evaluation Of GA Approach

* Advantages

    * Simple to do, understand
    * Requires little understanding of problem

* Disadvantages

    * Evolution can be slow
    * Tuning still matters

## Local Search As a Special Case

* Note that if your population size *n=1*, this looks a lot
  like local search, for which

    * No memory / recombination, so much faster and cheaper
      but more sensitive to local conditions

    * Typically requires state-space engineering to work
      well
    
    * Doesn't accomodate continuous features well

    * Really scary faster

* Interesting to compare the two approaches on real problems
