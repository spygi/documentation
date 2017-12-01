Notes from the Coursera course:

## Week 1
* Machine Learning has 2 branches: supervised and unsupervised learning. Supervised is when we know the "right answer" 
(price of a house given its size) whereas unsupervised we don't (we try to find some structure in the data eg. clustering problems)
* Supervised learning is further divided into regression where the output is continuous values vs classification problems 
where the output is descrete values.
* Linear regression where data fits a linear function. Cost function is the average of the squared errors. 
The goal is to find the θs that minimize the cost function. 
* A way to do this is with gradient decent: you start from 2 values for θs and update them until converging
using the gradient of the cost function - a "back-tracking" algo. Important is to update θs simultaneously.
* a is the learning rate: too big and there is no convergence. Too small and the convergence is too slow. Even with fixed rate
due to the convex nature of linear regression cost function, you get a smaller gradient therefore a smaller step.
* Depending on the initial values you might end up in a local minimum instead of the global one. Once you find a minimum (where the slope of the cost function is 0) gradient descent 
converges there, regardless of whether it is global or local. Fortunately though linear regression problems have only 1 minimum (convex function)
* Linear Algebra basics: A*B!=B*A (not cummutative) but (A*B)*C=A*(B*C) (associative), A^(-1)*A^(T)=I

## Week 2 
