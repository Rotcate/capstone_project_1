
***Model overview***

**Model name**: Black-Box Optimisation using Gaussian Process surrogate

**Type**: Bayesiam optimisation

**Task**: Sequential selection of data points which globally maximises the function

**Deployment**: process optimisation and hyperparametr tuning

**Intended use**

**Primary tasks**: identify the value which maximises the function

**Target users**: systems that require expesive function to be evaluated

**Use case**: financial modelling

**Limitations**: function evaluationn cost is a bottleneck as it has been limited to only once a weekf or a fixed number of weeks

**Details**

**Size**: initial data given - for each function you are given 10 datapoints and each week you are proposing a new set of datapoints. You will use the accumulation of the data points from previous weeks. Towards the end of the capstone, it is expected to have around 25 datapoints (initial 10 + 15 weeks of evaluations)

**Methods**: You will be using the Gaussian Process surrogate which will model the real function and one of the acquisition functions (UCB - Upper Confidence Bound or EI - Expected Improvement) to suggest the next best available data point.

**Sources**: The initial datapoints have been provided. The subsequest data points have been suggested by the acquisition function used.

**Performance**

The best values observed per function are the following:

Function 1 (2D): 0.00000000000003924213 
Function 2 (2D): 0.61448195055115628627
Function 3 (3D): -0.01567891799467148808
Function 4 (4D): 0.46654522988047064658
Function 5 (4D): 3378.23128317871532999561
Function 6 (5D): -0.27914755272875113601
Function 7 (6D): 1.87573521311492763530
Function 8 (8D): 9.90440809034400082567


**Assumptions and limitations**

**Assumptions**: Given each week you are evaluating a new data point and re-use that in your data set, the assumtpion here is that the newly generated points will help the surrogate function to improve its accuracy.
**Constraints**: Function evaluation constraint (once a week for 15 weeks)
**Limitations**: Curse of dimensionality for high degree functions. It will be difficult to evaluate whether you have covered uniformily the search space given the high dimensionality.


**Ethical considerations**

**Bias risks**: There is a potential value bias when chosing the next best point for evaluation. (sometimes you are not aware that you are sampling only from one region in high dimensional space)

**Transparency**: All the techniques used throughout the evaluation weeks have been documented. Acquisition function with kappa values + any pre-set noise assumptions

**Reproducibility**: Additional documentation will be addded containing week-by-week parameter values used for all variables. This can be used for further simulations. Please note, it is not expected to exctly reproduce the exact data point used during evaluations.




