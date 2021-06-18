# Estimation of GOFAST speed

This is a simple model for estimating the speed of object in the GOFAST video.
It uses a short period of time between seconds 12 and 17 when the plane
travels approximately along a straight line, i.e. does not turn. Using simple
trigonometry, we can compute the apparent coordinates of the object, that is,
the coordinates and speed of object in the *rest* frame of the plane (=
relative to plane). One can then try and estimate the ground speed of object,
i.e. speed in the frame of ground, by subtracting the ground speed of plane.
We do not know what is the ground speed of plane, but given the data, one can
play with different values.

We also perform the calculations where the object is at different altitudes,
starting from sea level (Case 0: 0 m above ground, then increase altitude by
1000 m up to Case 4: 4000 m above ground). In the latter case, the distance
between the plane and object is about 4 nm, the range value shown in the
video. The range value is not the true value; it is just an estimate. Again,
this is to show that the speed of object depends on the assumptions made about
its altitude.


## Data

Data is taken from youtube video between seconds 12 and 17. The calculation
uses the downward angle and left angle as follows:

Down angle (deg)   : (-26) - (-28)

Left angle (deg)   : 43 - 48


## Model

Using altitude of plane (alt) and the down angle (d) we calculate the
horizontal distance d2 of the object,

d2 = alt / tan(d).

We next calculate the x and y coordinates of the object in the frame of plane
using the left angle (l),

x = cos(l) * d2,  y = sin(l) * d2.

We calculate the (x, y) coordinates for 6 points of time (12 - 17 sec in the
video), so the time interval between (x, y) points is 1 second. Results are
shown in `results.md`.


## Estimate speed of object

We also print the velocity (x, y) components, e.g.

velocity components [m / s] [v_x, v_y] = [[-384, 8], [-375, 3], [-367, -1], [-359, -6], [-351, -10]]

which shows that the x-component is largest, meaning the object and plane move
along straight line towards each other. This makes it is easy to compute the
ground speed of object: just subtract the ground speed of plane from the
x-component since that comprises more than 97% of the speed.


## Conclusions

All in all the speed of object crucially depends on (1) speed of plane in the
ground frame (ground speed), (2) altitude of the object.
