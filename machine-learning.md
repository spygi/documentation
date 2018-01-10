Notes from the Coursera course:

## Intro
* Machine Learning can be split into 2 branches: **supervised** and **unsupervised** learning. Supervised is when we know the "right answer" (the price of a house given its size) whereas unsupervised when we don't (we try to find some structure in the data e.g. clustering problems)
* Supervised learning is further divided into **regression problems** where the output is continuous values vs **classification** problems where the output is descrete values (yes/no).
* Linear Algebra primer: ```A*B!=B*A``` (not cummutative) but ```(A*B)*C=A*(B*C)``` (associative), ```A^(-1)*A^(T)=I```


## Linear Regression
* Linear regression problems are those where data fits a linear function. The cost function is the average of the squared errors. The goal of linear regression is to find the θs that minimize the cost function. 
* A way to do this is with **gradient decent**: you start from 2 values for θs and update them *simultaneously* until converging, using the gradient of the cost function - essentially a "backtracking" algo. 
* Another way to do this is by computing θs analytically but that has a complexity of O(n^3).


### Gradient Decent
* a is the learning rate: too big and there is no convergence. Too small and the convergence is too slow. Even with a fixed rate a due to the convex nature of linear regression cost function, you get a smaller gradient therefore a smaller step.
* Depending on the initial values you might end up in a local minimum instead of the global one. Once you find a minimum (where the slope of the cost function is 0) gradient descent converges there, regardless of whether it is global or local. Fortunately though linear regression problems have only 1 minimum (convex function)
* Instead of 1 feature you can have n.
* Slow convergence? How to find this out? Plot cost function across number of iterations. To fix try:
** feature scaling (dividing by the range) and
** mean normalization (substracting average) - goal is for the features to be -1<x<1.
** increase value of a


## Polynomial regression
* By looking at your data you may find a polynomial function might fit the data better than a linear one. 
** What can you do if you have only one feature? You can create a quadratic function as θ_0+θ_1*x_1+θ_2*x_2.
** And the opposite - you can reduce the number of features: let's say you have 2 features that you can combine in 1 (x1*x2). Then you can use a linear function with 1 feature instead 2.

Q: When you act on features I guess you have to adjust the values of θs at the end, right?


## Classification problems
Like a regression problem but the parameter to be predicted can take only a few, discrete values 
* Binary classification problem is a yes/no problem: "Is a mail spam or not?". We map one case (positive) as 1 and the other as 0.
* We use the **sigmoid** (or logistic) function: ```hθ(x)=g(θTx)``` where ```z=θ^T*x```. This function is capped between 0, 1. * hθ(x) will give us the probability that our output is 1, therefore 1 - hθ(x) gives us the probability of being 0.
* Solving the sigmoid or hypothesis function we can create the decision boundary: the line that separates the area where y = 0 and where y = 1.
