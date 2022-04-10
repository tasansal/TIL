# Does Weight Initialization Matter?

## Summary

* Depends on the problem, shocker!
* Always run some tests with different initializers.
* Compare: accuracy, convergence plots, stability (to randomness), and train/test performance gap
* CIFAR-10 tests show He pefrormed better. [#1](#1-weight-initialization-for-neural-networks--does-it-matter)
  * Very stable and smooth training progression
  * Fast to converge to a desirable validation accuracy
  * The constant increase of validation accuracy from very fast epoch
  * Multiple runs are similar, and less randomness in the training process
  * Clear convergence and very thin generalization gap(training vs testing) compared to others.


### Useful Links:
#### 1. Weight Initialization for Neural Networks — Does it matter?
[Source](https://towardsdatascience.com/weight-initialization-for-neural-networks-does-it-matter-e2fd99b3e91)  
Compares the following with normal and uniform distribution:
* Glorot
* He
* Random