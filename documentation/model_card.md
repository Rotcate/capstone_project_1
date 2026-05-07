
# Model Card

## Model description

**Model name**: Black-Box Optimisation using Gaussian Process surrogate

**Type**: Bayesiam optimisation

**Task**: Sequential selection of data points which globally maximises the function

**Deployment**: Process optimisation and hyperparametr tuning

**Input:** There are 8 function in different dimensions ranging from 2D - 8D. Each value in teh dimension is between 0 and 1, decimal format.

**Output:** For each of the 8 functions, there is produced a value which is not bounded by any limitations. It can be positive or negative.

**Model Architecture:** I have opted to use Gaussian Process (GP) as a surrogate function with a variation of Upper Confidence Bound (UCB) and Expected Improvement (EI) as acquisition functions. I have fine tune the hyperparameter kappa for these acquisition functions. I have chosen to use RBF as a kernal for GP.

## Intended use

**Primary tasks**: Identify the value which maximises the function.

**Target users**: Systems that require expesive function to be evaluated.

**Use case**: Financial Modelling

**Limitations**: Function evaluation cost is a bottleneck as it has been limited to only once a week for a fixed number of weeks (13 weeks).

## Details

**Size**: Initial data given - for each function you are given 10 datapoints and each week you are proposing a new set of datapoints. You will use the accumulation of the data points from previous weeks. Towards the end of the capstone, it is expected to have around 23 datapoints (initial 10 + 13 weeks of evaluations)

**Methods**: You will be using the Gaussian Process surrogate which will model the real function and one of the acquisition functions (UCB - Upper Confidence Bound or EI - Expected Improvement) to suggest the next best available data point.

**Sources**: The initial datapoints have been provided. The subsequest data points have been suggested by the acquisition function used.

## Performance

The performance is measured of how close your outputs are to to the maximum value. A leaderboard was announced at the end of the 13 weeks evaluations to see the rank of who has managed to get closer to the maximum value. 

| Function Number | Rank out of 66 participants | Maximum value reached | Week number when maximum value was reached | Hyperparameters used |
| ----------- | ----------- | ------------| -----------| --------|
| Function 1  | 40 | 3.68899881390221E-12| Week 12 | GP + UCB (iterations =10)  kappa = 0.2|
| Function 2  | 7  | 0.777000459903961 | Week 13 | GP + UCB (iterations =10) kappa = 0.1 |
| Function 3  | 32 | -0.0156789179946715 | Week 4 | GP + UCB (iterations =10) kappa = 1 |
| Function 4  | 26 | 0.466545229880471 | Week 3 | GP + UCB (iterations =10) kappa = 2 |
| Function 5  | 43 | 3378.23128317872 | Week 6| GP + EI (iterations =10 ) kappa = 0.05 |
| Function 6  | 28 | -0.279147552728751 | Week 6 | GP + EI (iterations =10 ) kappa = 0.05 |
| Function 7  | 8  | 3.02915681360642 | Week 11 | GP + UCB (iterations =10) kappa = 0.5 |
| Function 8  | 3  | 9.9959433020615 | Week 12 | GP + UCB (iterations =10 ) kappa = 0.2 |


## Assumptions and limitations

**Assumptions**: Given each week you are evaluating a new data point and re-use that in your data set, the assumtpion here is that the newly generated points will help the surrogate function to improve its accuracy.
**Constraints**: Function evaluation constraint (once a week for 13 weeks)
**Limitations**: Curse of dimensionality for high degree functions. It will be difficult to evaluate whether you have covered uniformily the search space given the high dimensionality.


## Trade-offs

Some of the functions outputs have been ranked lower compared to the cohort. The reason being is that some of them were noisy and further tuning was required.

## Ethical considerations

**Bias risks**: There is a potential value bias when chosing the next best point for evaluation. (sometimes you are not aware that you are sampling only from one region in high dimensional space)

**Transparency**: All the techniques used throughout the evaluation weeks have been documented. Acquisition function with kappa values + any pre-set noise assumptions

**Reproducibility**: Additional documentation will be addded containing week-by-week parameter values used for all variables. This can be used for further simulations. Please note, it is not expected to exctly reproduce the exact data point used during evaluations.




