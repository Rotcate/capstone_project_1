# Capstone Project

**Project Overview
Black-Box-Optimisation BBO capstone project constitutes an optimisation problem where you evaluate an unknown function. There is no context about the function’s shape, gradients etc.

The goal of a BBO is to optimise and fine tune certain parameters without knowing the internal structures. This mimics the real-world scenarios where you do not have access to the internal workings of a system.

This BBO capstone project gives me an opportunity to experiment certain machines learning concepts such as parameter fine tuning and using surrogate and acquisition functions. Additionally, it also offers me a playground to apply different machine learning techniques to gain more insight of the function by making use of the data. 

**Inputs and Outputs
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

**Challenge Objectives
The target is to predict the next best data point which will give me the maximum value from the unknown functions.

The goal is to maximise the functions. I need to consider high dimensionality, the limited number of queries (only once per week) and the unknown function structure.
Worth noting that 10 input and output data points were given at the beginning of the BBO as a starting point.

**Technical Approach
My strategy for the first three query submissions has been on exploration. I am using a Gaussian Process with UCB for which I have used different values of kappa to target different exploration areas.
Week 1: Exploration for the Lower Bound - all functions had kappa set to 8.0
Week 2: Exploration for the Upper Bound - all functions had kappa set to 20.0
Week 3: Exploration for the Mid Area - I had to adjust kappa for each function to obtain some mid area points from the acquisition function:
	Function 1- kappa 10.0
	Function 2- kappa 12.0
	Function 3 - kappa 2.0
	Function 4 - kappa 2.0
	Function 5 - kappa 2.0
	Function 6 - kappa 4.0
	Function 7 - kappa 4.0
	Function 8 - kappa 3.0

I am using Gaussian Process with UCB (Upper Confidence Bound) for the acquisition function. I am considering using SVMs and regressions for detecting the high-interest regions which I can conduct more exploitation. 

My strategy is to first conduct exploration in a structured way (lower, mid, upper bounds). Next step is to discover if there are still areas worth exploring or exploit visible regions.

