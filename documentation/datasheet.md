

Motivation: why did you create this data set? What task does it support?
This data set was created to inform the reader about the structure of the data used in this Capstone project. The information in this file are valuable to support the reader understand the data structure and limitations around it.

Composition: what does it contain? What is the size and format and are there any gaps?
The data set contains values between 0 and 1 as datapoints for each function from 1 until 8. Each function has different dimensions. The values have a 6 digit float format. Plase see example below:

Function 5 (5-dimensions): 0.123456 - 0.123456 - 0.123456 - 0.123456

Collection process: how were the queries generated? What strategy did you use? Over what time frame?
The queries (datappints) were generated each week over a period of 15 weeks. They were generated using mainly the Gaussian Process as a surrogate function with an acquisition function (UCB or EI). 

Preprocessing and uses: have you applied any transformations? What are the intended and inappropriate uses?
I have applied some manual transaformation of the data where acquisition function was suggesting me the point 1. In this case, to respect the format I opted to use 0.900000. 

Distribution and maintenance: where is the data set available? What are the terms of use? Who maintains it?
The initial data set can be found in the initial_data folder for start. The weekly data generated for the queries cna be found under weekly_data_queries folder. The historical data from previous week is already integrated in the input file for the latest week. In order to access it, use the code methods to read the file in worksheet and display it.
The author of this GitHub repositary is the maintainer of this data set.