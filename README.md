# Keras Tuning Hyperparams
#### Using Basic Model on MNIST Digits 2 & 7

## Requirements


 * Python3
 * Keras  
 * Tensorflow
 * scikit-learn
 * numpy
 * IPython

## Goal & Methodology

**GOAL:** The goal was to show how to script automatic tuning of hyperparameters for a basic neural net. That is why I only use 2 digits and a simplified neural net.

**Methodology:** I thought about a few different methods. The challenge with doing a Search on hyperparameters is that it gets very expensive very quickly. I, however wanted to test a large set of parameters simultaneously. But so that it wouldn't be so expensive, I chose to do a [randomized search]( http://scikit-learn.org/stable/modules/generated/sklearn.model_selection.RandomizedSearchCV.html "Scikit-Learn Docs"). This is an obvious trade -- Losing some fidelity for speed.

## Results
After running twenty iterations out of a total possible 43,200 iterations, the model achieved .9944 accuracy on validation and .9913 on the test set. It took roughly one hour on one thread of my 2.7GHz Intel i5. 

## The Challenge
The challenge with neural nets is that tuning the hyperparameters is expensive. How do you know the best parameters for your data without running it? Doing a totally comprehensive search is computationally unrealistic without spending a lot of money on AWS. Even for this simple model, assuming the average epoch takes 6 seconds to complete, this is how long it would take to do a fully comprehensive grid search on only the parameters and values that I provided:

|Parameter | # of Values |
|---|---|
|Batch Size| 5|
|Optimizer| 4|
|Learning Rate| 4|
|# of Epochs| 3|
|Activator| 5|
|Dropout Rate 1| 3|
|Dropout Rate 2| 4|
|Neurons|3|
|**Total Possible Combinations**| 43,200|
|**Total Number of Epochs**| 345,600|
|**Estimated Time to Completion**|
|Seconds|2,073,600|
|Minutes|34,560|
|Hours|576|
|Days|24|

As you can see, it get's out of hand. I don't think its worth 24 days to determine a 2 from a 7. The randomized search is one method to reduce that time and still get really phenomenal results.

Others have been trying to address the same problem. My good friend [Joe Davison](https://github.com/joeddav "Github Link") and a team he worked with has a really interesting approach to this very same problem. They have used an evolutionary process (genetic algorithm) to solve the same challenge. If you follow the link to his github, you will see the repo devol.


## Other Resources
There are a lot of really awesome data scientists and aspiring data scientists that have posted a lot of really helpful material. For this project I followed a pattern published by Jason Brownlee [here](http://machinelearningmastery.com/grid-search-hyperparameters-deep-learning-models-python-keras/) as part of my effort during an internship with Ziff.ai, which repo can be found [here](https://github.com/ziff/internship2017).

I am going to continue posting new work, which should get more and more exciting over time. If you want to see more you can follow me here on Github, or find me at JaredHeywood.com
