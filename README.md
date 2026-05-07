# Capstone Project

## OVERWIEW

Black-Box-Optimisation BBO capstone project constitutes an optimisation problem where you evaluate an unknown function. There is no context about the function’s shape, gradients etc.

The goal of a BBO is to optimise and fine tune certain parameters without knowing the internal structures. This mimics the real-world scenarios where you do not have access to the internal workings of a system.

This BBO capstone project gives me an opportunity to experiment certain machines learning concepts such as hyperparameter fine tuning and using surrogate and acquisition functions. Additionally, it also offers me a playground to apply different machine learning techniques to gain more insight of the function by making use of the data. 

A surrogate function such as Gaussian Process (GP) acts as a build out simulation of the real function. An acquisition function suggest the bext next point that will maximises your output based on the data seen so far. 
Please find below the Model and Hyperparameter tuning for additional information.

## DATA

The model receives different dimensional features with values between 0 and 1 for 8 functions listed below. The return is a single decimal value which does not have a set upper or lower bound.

Function 1 - 2D

Function 2 - 2D

Function 3 - 3D

Function 4 - 4D

Function 5 - 4D

Function 6 - 5D

Function 7 - 6D

Function 8 - 8D

The inputs are values between 0 and 1 up to 6 decimal places. Each function expects the same number of values as per dimension. Example: 2D - input 0.100000 - 0.900000
The output is the response value which does not have a fixed expectation. It can vary from negative to positive values in decimal format. Example: 9.06758

**Challenge Objectives**

The target is to predict the next best data point which will give me the maximum value from the unknown functions.

The goal is to maximise the functions. I need to consider high dimensionality, the limited number of queries (only once per week) and the unknown function structure.
Worth noting that 10 input and output data points were given at the beginning of the BBO as a starting point.

## MODEL 

I have chosen to use Gaussian Process (GP) as a surrogate model for most of my evaluations. The only exception was in Week 5, where I have used Neural Networks acting as a surrogate function. For GP I have used RBF (0.3 moderate sensitivity) as a kernel with alpha = 1e-6 for low noise assumption. I have alternated between the use of Upper Confidence Bound (UCB) and expected improvement (EI) as acquisition funcitons which helped suggest which are the best next points to reach a maximum output in the evaluation. The UCB type of acquisition function helped me have a better control over exploration. The EI type of acquisition function is better for faster convergence. 

The strategy was to first conduct exploration in a structured way (lower, mid, upper bounds), followed by exploiting visible high-potential regions for discvering the maximum.

## HYPERPARAMETER OPTIMSATION

The hyperparameters which have been optimised are:
- the kappa value for the acquisition function (UCB or EI);
- number of iterations applied in the bayesian optimisation (Gaussian Process was used as surrogate function)
- The surrogate function used;

**All functions followed the same settings for the following weeks:**

| Week Number| Hyperparameters |
| -----------| --------------- |
| Week 1 | GP + UCB (iterations = 10) kappa = 8.0 |
| Week 2 | GP + UCB (iterations = 10) kappa = 20.0 |
| Week 5 | Neural Networks (kappa 2.0 - iterations 10) | 
| Week 6 | GP + EI (iterations = 10) kappa = 0.05 |
| Week 7 | GP + EI (iterations = 15) kappa = 5.0 |
| Week 8| GP + EI (iterations = 15) kappa = 10.0 |

**Function 1**

| Week Number| Hyperparameters |
| -----------| --------------- |
| Week 3 | GP + UCB (iterations = 10) kappa = 10.0 |
| Week 4 | GP + UCB (iterations = 10) kappa = 9.0 |
| Week 9 | GP + UCB (iterations = 10) kappa = 9.5 | 
| Week 10 | GP + UCB (iterations = 10) kappa = 5.0 |
| Week 11 | GP + UCB (iterations = 10) kappa = 6.0 |
| Week 12| GP + UCB (iterations = 10) kappa = 0.2 |
| Week 13| GP + UCB (iterations = 10) kappa = 0.1 |


**Function 2**

| Week Number| Hyperparameters |
| -----------| --------------- |
| Week 3 | GP + UCB (iterations = 10) kappa = 12.0 |
| Week 4 | GP + UCB (iterations = 10) kappa = 2.0 |
| Week 9 | GP + EI (iterations = 15) kappa = 4.5 | 
| Week 10 | GP + EI (iterations = 10) kappa = 3.0 |
| Week 11 | GP + EI (iterations = 10) kappa = 4.0 |
| Week 12| GP + UCB (iterations = 10) kappa = 0.2 |
| Week 13| GP + UCB (iterations = 10) kappa = 0.1 |


**Function 3**

| Week Number| Hyperparameters |
| -----------| --------------- |
| Week 3 | GP + UCB (iterations = 10) kappa = 12.0 |
| Week 4 | GP + UCB (iterations = 10) kappa = 1.0 |
| Week 9 | GP + UCB (iterations = 15) kappa = 0.5  | 
| Week 10 | GP + UCB (iterations = 10) kappa = 1.0 |
| Week 11 | GP + UCB (iterations = 10) kappa = 2.0 |
| Week 12| GP + EI (iterations = 10) kappa = 0.2 |
| Week 13| GP + UCB + PCA (iterations = 10) kappa = 0.1 |

**Function 4**

| Week Number| Hyperparameters |
| -----------| --------------- |
| Week 3 | GP + UCB (iterations = 10) kappa = 2.0 |
| Week 4 | GP + UCB (iterations = 10) kappa = 1.0 |
| Week 9 | GP + UCB (iterations = 15) kappa = 0.5 | 
| Week 10 | GP + UCB (iterations = 10) kappa = 4.0  |
| Week 11 | GP + EI (iterations = 10) kappa = 4.0 |
| Week 12| GP + EI (iterations = 10) kappa = 0.2 |
| Week 13| GP + UCB + PCA (iterations = 10) kappa = 0.1 |


**Function 5**

| Week Number| Hyperparameters |
| -----------| --------------- |
| Week 3 | GP + UCB (iterations = 10) kappa = 2.0 |
| Week 4 | GP + UCB (iterations = 10) kappa = 1.0 |
| Week 9 | GP + UCB (iterations = 15) kappa = 0.5 | 
| Week 10 | GP + UCB (iterations = 10) kappa = 4.0 |
| Week 11 | GP + UCB (iterations = 10) kappa = 5.0 |
| Week 12| GP + UCB (iterations = 10) kappa = 0.2  |
| Week 13| GP + UCB + PCA (iterations = 10) kappa = 0.1 |


**Function 6**

| Week Number| Hyperparameters |
| -----------| --------------- |
| Week 3 | GP + UCB (iterations = 10) kappa = 4.0 |
| Week 4 | GP + UCB (iterations = 10) kappa = 2.0 |
| Week 9 | GP + EI (iterations = 15) kappa = 0.5 | 
| Week 10 | GP + EI (iterations = 10) kappa = 3.0 |
| Week 11 | GP + EI (iterations = 10) kappa = 4.0 |
| Week 12| GP + UCB (iterations = 10) kappa = 0.2 |
| Week 13| GP + UCB + PCA (iterations = 10) kappa = 0.1 |


**Function 7**

| Week Number| Hyperparameters |
| -----------| --------------- |
| Week 3 | GP + UCB (iterations = 10) kappa = 4.0 |
| Week 4 | GP + UCB (iterations = 10) kappa = 2.0 |
| Week 9 | GP + UCB (iterations = 15) kappa = 1.0 | 
| Week 10 | GP + UCB (iterations = 10) kappa = 0.5 |
| Week 11 | GP + UCB (iterations = 10) kappa = 0.5 |
| Week 12| GP + UCB (iterations = 10) kappa = 0.2 |
| Week 13| GP + UCB + PCA (iterations = 10) kappa = 0.1 |


**Function 8**

| Week Number| Hyperparameters |
| -----------| --------------- |
| Week 3 | GP + UCB (iterations = 10) kappa = 3.0 |
| Week 4 | GP + UCB (iterations = 10) kappa = 2.0 |
| Week 9 | GP + UCB (iterations = 15) kappa = 2.5 | 
| Week 10 | GP + UCB (iterations = 10) kappa = 0.5 |
| Week 11 | GP + UCB (iterations = 10) kappa = 0.5 |
| Week 12| GP + UCB (iterations = 10) kappa = 0.2 |
| Week 13| GP + UCB + PCA (iterations = 10) kappa = 0.1 |


## RESULTS

The black-box optimisation project was conducted as part of the Imperial College London - Machine Learning and Artificial Intelligence certificate course. A leaderboard was announced at the end of the 13 weeks evaluations to see the rank of who has managed to get closer to the maximum value. 

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

**Model Card**

[documentation/model_card.md](https://github.com/Rotcate/capstone_project_1/blob/main/documentation/model_card.md)

**Datasheet**

[documentation/datasheet.md](https://github.com/Rotcate/capstone_project_1/blob/main/documentation/datasheet.md)


**Source Code**

[source_code/BBO.ipynb](https://github.com/Rotcate/capstone_project_1/blob/main/source_code/BBO.ipynb)

**Initial Provided Data**

[initial_data](https://github.com/Rotcate/capstone_project_1/tree/main/initial_data)

**Weekly Evaluations**

[weekly_data_queries](https://github.com/Rotcate/capstone_project_1/tree/main/weekly_data_queries)




