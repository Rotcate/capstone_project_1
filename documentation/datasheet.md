
# DataSheet

**Motivation**

This data set was created to support sequential evaluations for a black-box optimisations problem. 
Some initial data sets were provided to support our initial evalution and starting to accumulate weekly data points to discover the maximum value from 8 unknown functions having different dimensionality. 
The aim is to obtain a value for each function that represents the maximum.

**Composition**

The data set contains values between 0 and 1 as datapoints for each function from 1 until 8. Each function has different dimensions. The values have a 6 digit float format. Plase see example below:

Function 5 (4-dimensions): 0.123456 - 0.123456 - 0.123456 - 0.123456

The full list of function dimensions can be found below:

Function 1 - 2D

Function 2 - 2D

Function 3 - 3D

Function 4 - 4D

Function 5 - 4D

Function 6 - 5D

Function 7 - 6D

Function 8 - 8D


**Initial data**

There were provided 10 initial data sets (inputs and outputs) for each function. The inputs were represented as a list of lists, where each list portrays the dimensional value-datapoints. For example: 

Function 5 (4-dimensions): 0.123456 - 0.123456 - 0.123456 - 0.123456 will be represeted as [[0.123456, 0.123456, 0.123456, 0.123456]]

The output represents a list of values, for example Function 1: [ 1.32267704e-079  1.03307824e-046  7.71087511e-016  3.34177101e-124 -3.60606264e-003 -2.15924904e-054 -2.08909327e-091  2.53500115e-040
3.60677119e-081  6.22985647e-048]


**Collection process**

The queries (datapoints) were generated each week over a period of 13 weeks. They were generated using mainly the Gaussian Process as a surrogate function with an acquisition function (UCB - Upper Confidence Bound or EI - Expected Improvement). Each week's generate datapoint was then used in the next week's round to better shape the surrogate function and influence the acquisition's function next best suggested data point. 
The generated datapoints were essentially appended to the already existing lists for each function's input and output.
The expectation is that the input and output lists for each functions are expected to grow to a length of 23 data points at the end of the optimisation project (10 initial data points + 13 weekly evaluation datapoints).

**Optimisation Stategy**

The first strategy that led me to some strong results was to explore and experiment in the first 5-7 weeks. I have used mainly Gaussian Process as a surrogate function with an acquisition function (UCB - Upper Confidence Bound or EI - Expected Improvement) by tuning with different kappa value. Another strategy I adopted during these first weeks was to pick values from different regions (lower, mid, high). These helped me in collecting data points from different regions to reduce the unknown. I continued to pick recommended next best points based on the previous submissions which provided a maximum value output. A good example is function 8, where from the exploration phase, the lower bound showed potential. I chose to exploit it further in the last 5 evaluations to reach convergence. My result ended in top 3 out of 66 for this function.

The most significant trade-offs I have faced was between applying new methods (for example: neural networks Week 5) and continuing with Gaussian Processes as a surrogate function with acquisition function (UCB or EI). Due to the fact that there were only 13 weeks of evaluation, I have chosen only one evaluation to experiment with neural networks (Week 5) and the final week to apply PCA for dimensionality reduction (Week 13). For all other weeks, I have made a trade-off between exploration or exploitation and the choice of acquisition function. I have focused in the first few weeks to only explore and try out different values of kappa. (Picking data points from beginning, mid, top regions) The short-term strategy which I have applied it towards the last weeks of the capstone project was to reuse the acquisition function and slightly adjusting kappa value for which it has been previously identified a maximum output. 

Additionally, I have applied PCA for dimensionality reduction during Week 13 to functions 3 until 8. The best consideration here is to use PCA to reduce dimensionality, so plotting (visualisation) will become easier in 2D.


**Preprocessing and uses**

I have applied some manual transaformation of the data where the acquisition function was suggesting a value of 1. In this case, to adhere to the guideline format (6 digit float format) I opted to use instead 0.900000. 

This adjustment may slightly influence results near the boundary values, so it should be considered when reviewing the optimisation results.

Note: For Week 13, I have applied a standard Scaler to the data before applying PCA.

**Assumptions**

The input data is between 0 and 1 and has a 6 digit format float format.

The initial data provided is limited to 10 datapoints per function.

The evaluation budget is limited to 13 datapoints per function.

The evaluation data points are sampled sequentially.

**Performance and results**

A leaderboard was announced at the end of the 13 weeks evaluations to see the rank of who has managed to get closer to the maximum value. More details are included, such as my inputs and outputs that were the closest to the maximum together to which position they took among the 66 participants.

| Function Number | Rank out of 66 participants | Maximum value reached | Input datapoints| Week number when maximum value was reached | Hyperparameters used |
| ----------- | ----------- | ------------| ---------| -----------| --------|
| Function 1  | 40 | 3.68899881390221E-12 | [0.339981, 0.323487]| Week 12 | GP + UCB (iterations =10)  kappa = 0.2|
| Function 2  | 7  | 0.777000459903961 | [0.510208, 0.529779]| Week 13 | GP + UCB (iterations =10) kappa = 0.1 |
| Function 3  | 32 | -0.0156789179946715 | [0.418978, 0.452988, 0.516531] | Week 4 | GP + UCB (iterations =10) kappa = 1 |
| Function 4  | 26 | 0.466545229880471 | [0.405673, 0.390640, 0.346566, 0.428138] | Week 3 | GP + UCB (iterations =10) kappa = 2 |
| Function 5  | 43 | 3378.23128317872| [0.988643, 0.690716, 0.985391, 0.856409] | Week 6| GP + EI (iterations =10 ) kappa = 0.05 |
| Function 6  | 28 | -0.279147552728751 | [0.445702, 0.249091, 0.570676, 0.789337, 0.143917] | Week 6 | GP + EI (iterations =10 ) kappa = 0.05 |
| Function 7  | 8  | 3.02915681360642| [0.097177, 0.221951, 0.410126, 0.256124, 0.300504, 0.618146] | Week 11 | GP + UCB (iterations =10) kappa = 0.5 |
| Function 8  | 3  | 9.9959433020615 | [0.134207, 0.173346, 0.133126, 0.150276, 0.757313, 0.500828, 0.208864, 0.572960] | Week 12 | GP + UCB (iterations =10 ) kappa = 0.2 |


**Ethical, practical and general considerations**

The black-box optimisation tasks relates to the real-world applications, from a perpsective of not knowing the insight of a problem, or showing an expensive evaluation or high complexity. As a real-world application, let's take financial modelling and drug discovery. These can be conducted by fine tuning hyperparameters for these models. 

There are limitations of the synthetic nature of these functions. The main one being, the inability to fully capture noise or changing conditions which are often experienced in the real-world.

There is also a consideration around the risk in overfitting the optimisation strategy rather than developing one which will generalise on new functions or problems.
Another note is around the limited evaluation budget. There is a risk in reaching a local optima, instead of obtaining the global maximum value. It can be observed that this has been the case for function 5.


**Distribution and maintenance**

The initial data set can be found in the initial_data/ folder for start. The weekly data generated for the queries can be found under weekly_data_queries/ folder. The historical data from previous week is already integrated in the input file for the latest week. In order to access it, use the code methods under code/ will be available to read the file in the worksheet and display its content.


The author of this GitHub repositary is the maintainer of this data set.
