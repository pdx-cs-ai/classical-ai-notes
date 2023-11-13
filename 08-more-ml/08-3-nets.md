## Beyond Perceptrons

* One perceptron is kind of a poor learner

* Learning XOR is impossible

        x1 x2  y
         0  0  0
         0  1  1
         1  0  1
         1  1  0

* This is because we cannot choose *w1*, *w2* such that

        x1 * w1 + x2 * w2 > 0

  matches the sign: one 1 means output 1, zero *or* two 1s
  means output 0

## "Neural" Nets

* Idea: Glue perceptrons together into a DAG so that they
  can learn more complicated functions

        x1 ^ x2 = (x1 | x2) & !(x1 & x2)

          w21 (w111 x1 + w112 x2 + w10 > 0)
        + w22 (w121 x1 + w122 x2 + w20 > 0)
        + w0 > 0

  * *w111* and *w112* positive
  * *w121* and *w122* negative
  * *w21* positive
  * *w22* negative
  * *w10* and *w20* and *w0* zero

* *Note:* The inner nonlinearity is critical. Otherwise
  simple algebra gives

          (w21 w111 + w22 w121) x1
          + (w21 w112 + w22 w122) x2
          + (w21 w10 + w22 w20 + w0) > 0

        a1 x1 + a2 x2 + a0 > 0

  and we're back where we started.


## Training A Net

* Obvious plan: just adjust all weights in the
  system by the error

* This isn't a workable plan: it distributes
  error equally across all weights, including
  those that should go "the other way"

* More traditional plan: distribute error according to
  effect on the output using *∂y/∂h*

* Sadly, the derivative of `y = h > 0` is zero everywhere

## htan Squashing Function

* The hyperbolic tangent function is

        s(h) = (e**(2h) - 1) / (e**(2h) + 1)

* You can plot it with `gnuplot`

* You can adjust the constant to make it steeper or shallower,

        s(h) = (e**(ah) - 1) / (e**(ah) + 1)

  but customarily just pick 1
  
        s(h) = (e**h - 1) / (e**h + 1)

* `s(h)` has a reasonable derivative everywhere, so we can
  distribute error more fairly

## Leaky ReLU

* Our htan squashing function is OK, but slow to compute

* Saturation is an issue

* Here's the new hotness in squashing functions: "[Rectified
  Linear Unit](https://en.wikipedia.org/wiki/Rectifier_%28neural_networks%29)".
  We will use a "leaky" ReLU, which avoids the "stuck
  neuron" problem

          s(h) = 0.1 h (h < 0), h (otherwise)
          ds/dh = 0.1 (h < 0), 1 (otherwise)

* Inspired by biology; asymmetric; many clever variations

* Leads to sparsely-activated nets

* Avoids the *vanishing gradient* problem where a neuron
  gets "stuck"

## Weight Assignment

* We have a discriminator that can XOR, but how to
  pick the right weights?

* Use training (or reinforcement) to adjust the weights as with
  PCT

* Weight assignment by error *backpropagation*: gradient descent on
  error

* Assume

        E = c - y

  where *E* is error, *c* is target response, *y* is
  output response

* Change 

        E[j-1] = sum[k] (w[k][i] E[k])
        w[j][i] += a E[j] y[j-i][i] dy/dx
        w0[j][i] += a E[j] dy/dx

  (or thereabouts; subscripts get fiddly)

* Input layer is handled specially since there are
  no weights to adjust there

## Big Nets

* Typical architecture: "input layer" → hidden layers → output layer

    * Input layer is just the inputs, not actual neurons

    * More / wider (and fancier) hidden layers = more
      generalization ("deep learning")

    * Training gets slow quickly

* Use multicore CPUs, SIMD graphics cards, Tensor Processing
  Units to do weight adjustments on a whole layer in parallel

## ML Example: Neural Net Backgammon

* What is backgammon?

* Why is BG hard?

* Gerry Tesauro 199x: *TD(lambda)* NN reinforcement learning
  can learn to play good BG from rules alone!

* Add shallow search for tactics, tune: best BG player ever!

* Humans learn BG from *TD(lambda)*, close circle

* Recently Go, Chess, etc

## CS Ethics: Neural Net Actuarials?

* Can build a neural net that

    * Given: training data about time-on-job
    * Predicts: expected time-on-job

* Ethically, must use only socially sanctioned inputs,
  e.g. not race!

* *But*

    * Net can infer race from e.g. eye color, average salary, traffic
      stops by location, the MMPI (!)

    * Net is nondeclarative: *how does it use the inputs*?

* Net may inadvertantly "discriminate" based on hidden
  undesired variables

* Worse, malicious person may adjust input choice and
  training data (even weights?) to discriminate: Hidden
  Delta theorems say NPC to find intentionally-induced
  errors

* Conclusions?
