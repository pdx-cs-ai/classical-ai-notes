## Maybe We Should Just Build A Brain

* Always kind of the dream anyhow

* Start by "understanding how the brain works" (air quotes
  are deliberate)

* Basic architecture: neurons form a directed graph through
  dendrites (inputs) and axon (output)

* Maybe should start with a simplification by ignoring

  * Graph structure, static and dynamic — just use fixed DAG
  * How the signalling works — just use analog levels
  * How the neuron works — assume adjustable simple combination
  * That the brain is more than neurons, with chemical and
    biological elements

## Perceptron

* "Artificial Neuron" (Papert *et al*): basis of neural nets

* Handles continuous inputs and outputs well: we will
  binarize anyway for now because binary

* Idea: predict the class as a thresholded weighted sum of
  the features

        c = sum[i] w[i] x[i] + b > 0

  (we will use unitish weights and features: `x[i], w[i] in [-1..1]`

## Training A Perceptron

Training consists of learning appropriate weights *w*

1. Assign some initial weights (random?)

2. Feed each training instance through the perceptron

3. For each instrance, adjust the weights "toward the true
   classification"

        w[i] += a (c - y) x[i]
        b += a (c - y)

  where *y* is the unthresholded output. Remember that
  *c* and *x* are 0 or 1. *a* is the "learning rate":
  smalller (a < 0.1) means more reliable convergence,
  larger can mean faster learning or divergence

* Run all the training instances repeatedly until the
  average accuracy isn't getting better
