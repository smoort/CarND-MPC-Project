# CarND-Controls-MPC Project Reflection
Self-Driving Car Engineer Nanodegree Program

---

## The Model

* The state of the model has 5 parameters :
	* The position of the vehicle (x & y)
	* The velocity of the vehicle (v)
	* The cross track error which signifies how far the vehicle is from the desired path
	* The vehicle orientation error which signifies how much the vehicle is oriented away from the desired heading
* The actuator considered for this model are :
	* Steering angle which indicates the amount by which the vehicle has to be turned to reach the desired location & orientation
	* Acceleration which indicates the amoutn by which the vehicle should move to get to the desired velocity


## Timestep Length and Elapsed Duration (N & dt)

*  A value of 10 has been used for N.  Higher values were not chosen keeping performance in mind. Also higher values led to greater approximation leading the vehicle to go off track especially around curves.  A lower value did not give enough time steps for the model.
*  A value of 0.1 has been used for dt. Higher dt values provided quicker convergence to line but the vehicle velocity was not smooth.  A lower dt (below latency value) caused the vehicle to oscillate quite a bit.


## Polynomial Fitting and MPC Preprocessing

*  The vehicle position is subtracted from the way points to transform the vehicle position to 0,0.
*  The vehicle is rotated along the new position (0,0) to make vehicle orientation as 0 as well.  This is done to simplify the trajectory prediction.
*  The transformed way points are fit into a third degree polynomial and its coeffecients are obtained.
*  The y value at x = 0 for the calculated coeffecitents provides the cross track error.
*  The orientation error is calculated using the coffecients as well.

## Dealing with latency

*  The project as a 100ms (0.1 s) latency.
*  New x, y, psi and v values are calculated using the initial values from the simulator and coeffecients.
*  The waypoints are transformed using the updated position, velocity and orientation of the vehicle.
*  The polynomial is fit using the transformed waypoints.