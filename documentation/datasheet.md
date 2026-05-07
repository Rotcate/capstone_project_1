
# DataSheet

**Motivation**: 

This data set was created to support sequential evaluations for a black-box optimisations problem. 
Some initial data sets were provided to support our initial evalution and starting to accumulate weekly data points to discover the maximum value from 8 unknown functions having different dimensionality. 

**Composition**: 

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

**Collection process**: 

The queries (datapoints) were generated each week over a period of 15 weeks. They were generated using mainly the Gaussian Process as a surrogate function with an acquisition function (UCB - Upper Confidence Bound or EI - Expected Improvement). Each week's generate datapoint was then used in the next week's round to better shape the surrogate function and influence the acquisition's function next best suggested data point.

**Preprocessing and uses**: 

I have applied some manual transaformation of the data where the acquisition function was suggesting a value of 1. In this case, to adhere to the guideline format (6 digit float format) I opted to use instead 0.900000. 

This adjustment may slightly influence results near the boundary values, so it should be considered when reviewing the optimisation results.

**Assumptions**

The input data is between 0 and 1 and has a 6 digit format float format.

The initial data provided is limited to 10 datapoints per function.

The evaluation budget is limited to 15 datapoints per function.

The evaluation data points are sampled sequentially.


**Distribution and maintenance**:

The initial data set can be found in the initial_data/ folder for start. The weekly data generated for the queries can be found under weekly_data_queries/ folder. The historical data from previous week is already integrated in the input file for the latest week. In order to access it, use the code methods under code/ will be available to read the file in the worksheet and display its content.


The author of this GitHub repositary is the maintainer of this data set.
