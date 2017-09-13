# CarND-Controls-MPC Project Reflection
Self-Driving Car Engineer Nanodegree Program

---

## The Model

* The state of the model has 5 parameters :
	* The position of the vehicle (x & y)
	* The velocity of the vehicle (v)
	* The cross track error which signifies how far the vehicle is from the desired path
	* The vehicle orientation error which signifies how much the vehicle is oriented away from the desired heading


## Timestep Length and Elapsed Duration (N & dt)

* Manual tuning using trial and error was used to arrive at the final hyperparameters
* By observing the car in a straight lane, it was evident that the car did not have any systemic bias.  Hence the I component was set to 0.
* As high P value caused too much overshooting, used a low P value with high D value to achieve smooth convergence.

## Polynomial Fitting and MPC Preprocessing

*

## Dealing with latency

*