
# DataSheet

**Motivation**: 

This data set was created to inform the reader about the structure of the data used in the Capstone project. This information is valuable to support the reader in understanding the data structure and limitations around it.

**Composition**: 

The data set contains values between 0 and 1 as datapoints for each function from 1 until 8. Each function has different dimensions. The values have a 6 digit float format. Plase see example below:

Function 5 (4-dimensions): 0.123456 - 0.123456 - 0.123456 - 0.123456

**Collection process**: 

The queries (datapoints) were generated each week over a period of 15 weeks. They were generated using mainly the Gaussian Process as a surrogate function with an acquisition function (UCB - Upper Confidence Bound or EI - Expected Improvement). Each week's generate datapoint was then used in the next week's round to better shape the surrogate function and influence the acquisition's function next best suggested data point.

**Preprocessing and uses**: 

I have applied some manual transaformation of the data where the acquisition function was suggesting a value of 1. In this case, to adhere to the guideline format (6 digit float format) I opted to use instead 0.900000. 

**Distribution and maintenance**:

The initial data set can be found in the initial_data folder for start. The weekly data generated for the queries can be found under weekly_data_queries folder. The historical data from previous week is already integrated in the input file for the latest week. In order to access it, use the code methods to read the file in the worksheet and display it.

The author of this GitHub repositary is the maintainer of this data set.
