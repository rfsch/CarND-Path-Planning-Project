# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program
   
### Model Documentation

#### Reflection

In order to generate the path for the egocar I used the following approach:

1. I first checked if the provided highway_map.csv file (which contains sparse set of waypoints of the high-way)
   could be used to interpolate/generate a path for the egocar.
 
2. Since the waypoints are spaced too far apart (30 meters) it is not feasible to interpolate them since a zigzag line would be created. 
   Making the egocar follow this zigzag line would result in sudden lateral (jerk) and longitudinal (accelareration) changes which we try to avoid 
   in order to provide comfort for the passengers. 

3. To generate a smooth path I created a spline passing through the next three waypoints (30,60,90 meters) of the egocar. 

4. I then used this spline for the path planning of the egocars. Since this line is nice and smooth the egocar does not violate max acceleration 
   or jerk restrictions that were experiences before. 

5. Next the spline was evenly split into waypoints such that the egocar could travel at a desired speed by following it.  
