# AI and Computational Complexity

* For some problem "size" parameter *n* we measure some
  growth in some problem "difficulty" feature via a function
  *f(n)*. *O(f(n))* approximates a bunch of *f*'s as
  equivalent.

* Strong Church-Turing Thesis: In practice, all "polynomial"
  difficulty problems are easy, all "exponential" difficulty
  problems are intractable. But to talk about that, need to
  talk about "problem difficulty"

  * "Problem" is a collection of instances, "class" is a
    collection of problems. Class "NP" contains all problems
    such that you can check a solution in polytime;
    therefore you could in principle "guess" the solution
    and verify in polytime

  * NP is a class of "decision problems": "Is there a
    solution to this sliding tile instance in less than *k* moves?"
    Optimal sliding tile is thus in NP.
    
  * NP hardness is proved by "reduction": can reduce a
    problem known to be as hard as any problem in NP to this
    problem
    
  * NP-hard + in NP = NP complete

* Many (all?) problems that are "AI hard" lie in the region
  of NP-complete and PSPACE-complete problems. Therefore in
  general even humans are going to fail

* Trick: Every problem with a finite number of finite size
  instances has complexity *O(1)*. So limit ourselves to
  "small" numbers of "small" instances: solve the instances
  we care about efficiently

* Complexity theory is a good guide for what's going to be
  "hard", but not a limit on what you can do
