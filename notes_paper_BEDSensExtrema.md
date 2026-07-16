# NOTES: Paper - Bayesian Sensor Placement for Extrema

## QUESTIONS:
- We go discrete to make the maths easier and make the number of possibilities finite - i.e. it is possible to do a grid search of all possible sensor locations
- How do we tune N - the number of simulation draws we need?
- How do we tune R - the number of sensor readings?
    - We also need to pick a simulation - this couples the simulation realisation and the sensor noise as nested.
- Why is the outer loop over R (sensor readings) but we draw a random simulation in here. Why not draw a simulation then generate R sensor readings?
- How do we pick candidate designs d? Do we sweep all possible cell/bin combinations?
    - Do we start randomly and then move sensors with an optimiser?

- So B_safe is (Are we unsafe? true/false, bin of the max val, cell location of the max val)

- Choosing discretisations for cell() and bin()?

- Ok so up to section 6 we use our full-fidelity simulator, section 6 we switch to a GP surrogate?
    - Does that mean we can use some properties of GPs to help the maths?

*THERE IS NO FREE LUNCH*
- No parametric version has problems (mainly the expensive front end)
- GP emulator also has problems

- Can you walk me through the problems/limitatiosn with both of these


## KEY POINTS
- Some of the first sensors should be placed to fix the state/simulation we are working with i.e. the geometry, material model or BCs. Then we can find the maximum more easily.
- 

## Notation: Section 3
- d is the candidate sensor design
- T the field to be observed on the domain mapping a spatial location to a real value
- Y_d - observations and sensor locations
- H_d - ideal observation operator = vector of sensor observations (T(s1),T(s2)...T(s_m)) where s is the point sensor location for 'm' sensors.
- eps_d - sensor noise

- Risk field: R(x;T) = h(T(x),x)
    - Risk is a function of the field value and the position in the field
    - For fixed T we have a risk based on position x

- M(T) - the maximum value of the field
- x_*(T) - the location of the max value
- Target Z_ext = (M,x_*)

- Ideal sensor design 
- d^* = arg max I(Y_d;Zext)
    - The maximum information gain given a sensor setup with fixed maximum value and its location
- I(Y_d;Zext) = H(Z_ext) - E_Yd[H(Zext|Y_d)]

Discrete / Finite Partitioning:
- cell(x) with C_L partitions
  cell(x_*) = l
- bin(T) with J_K partitions
  bin(M) = k 

We choose K and L as engineering design inputs based on the tolerance of the required prediction

 Tolerance aware target is now (discrete analogue of Zext)
 Bext = (bin(M),cell(x_8))

 Now the optimal sensor design d^* is
- d^* = arg max I(Y_d;Bext)

## Notation: Section 4
- Uncertain model/simulation parameters become nuisance variables we need to marginalise (integrate over)

- zeta = (theta,beta) where theta is the material and geometry and beta is the boundary/initial conditions.
- T = G(theta,beta) - our field is given by our simulation G and its parameters 

- Define a near boundary event if safety relevant cases are rare:
- A_eps = {M_safe > -eps}
- Where eps > 0 is an engineering tolerance (safety factor)
OR define a weighting function
- Both parts of the weighting function are only triggered when we are unsafe otherwise the multiplier is 1 and has no effect

*NOTE*: M_safe = sup[G(theta,beta)(x) - T_safety(x))], therefore if M_safe > 0 we are unsafe, M_safe < 0 we are safe. Maximum of M_safe is the most unsafe part 

*DECISION RISK*: C_FN = cost of false negative, C_FP cost of false positive
R(d) = ExpValue(C_FN 1{} + C_FN 1{})
- Risk given a sensor placement is the cost of a false 

## Notes:
- Sensor placement for extremal quantities and extremal location
- Formulated on a discrete set of spatial locations `cell()` and discrete bins of value `bin()`

# Notes section 5
The ESS represents the number of independent, un-correlated samples that would provide the exact same statistical precision as your autocorrelated MCMC samples.
