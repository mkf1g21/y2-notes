#astro
# pre recording
## kepler's laws
kepler's first law is that orbits are an ellipse, with the body they orbit at one focus 
the second law says that an equal amount of time will have a triangle with equal area
the square of the orbit is proportional to the mean distance(semi major axis)

## ellipse equation
![[Pasted image 20221025110915.png]]
the semimajor axis is just the longest length divided by 2

the equation of an ellipse in polar coordinates is $r= \frac{a (1-e^2)}{1-e\cos(180-\theta)}$, or $r= \frac{a (1-e^2)}{1+e\cos(\theta)}$. $180-\theta$ is there because it is commonly used in orbits. This is derived from replacing $x$ and $y$ in the cartesian equation with their relevant equivalents in polar coordinates

area of an ellipse is $A=\pi ab = \pi a^2 \sqrt{1-e^2}$

# orbital motion
kepler got his laws from observations. Newton proved it mathematically

for a small time interval, the change in radial and tangential vecolities are $\Delta \dot r + r \dot \theta\Delta \theta$ and $\dot r \Delta \theta + r \Delta \dot \theta + \Delta r \dot \theta$
the acceleration in the radial direction is given by $\ddot r - r\dot \theta^2$ and in the tangential direction it is given by $2\dot r \theta + r \ddot \theta$ 

balancing the accelerations with gravitational force in the different directions gives $-\frac{GMm}{r^2}\frac{\bf r}{r} = m(\ddot \bf r  -\bf r\dot \theta^2 )$ in the radial direction and $0=m(2 \bf \dot r \dot \theta +\bf r \ddot \theta  )$ tangentially.
in the radial equation, $\frac{\bf r}{r}$ just means the unit vector in the direction of $\bf r$

looking at the tangential direction, the orbital moment of momentum can be found. This is given by $r^2 \dot \theta$ and it can be shown to be constant
![[Pasted image 20221026153746.png]]
**it basically says that angular momentum per unit mass($h$) is constant.**

in the radial direction, $GM$ can be replaced with $\mu$

after a lot of chain ruling, the radial acceleration gives $\frac 1r =\frac {\mu}{h^2}(1+e\cos\theta)$
This becomes $r = \frac{h^2}{\mu(1+e\cos \theta)}$, when $a(1-e^2) = \frac{h^2}{\mu}$ this looks a lot like the ellipse equation in polar coordinates.
This shows that orbital motions follow orbital paths

as $\Delta t \rightarrow 0,\ \dot A = \frac 12 r^2 \dot \theta = \frac 12 h\text{ constant}$

orbital period is given by $\tau = \frac{\pi a^2 \sqrt{1-e^2}}{\frac 12 h} = \frac{A}{\dot A}$
$\tau = \frac{\pi a^2 \sqrt{1-e^2}}{\frac 12 \sqrt{\mu a (1-e^2)}}$
$\tau = 2\pi \sqrt{\frac{a^3}{\mu}}$
$\tau = \frac{4\pi^2}{\mu}a^3$
the **mean motion** is $n=\frac{2\pi}{\tau}$. it describes the rate that the body moves around the auxiliary circle

## orbital elements
if eccentricity is bigger than $1$, orbits can be para- or hyperbolic. these arent considered for now. if $e=0$ the orbit is circular.

there are 6 keplerian orbital elements

### semi major axis (a)
this is how big the orbit is

### eccentricity (e)
this is how far from a circle an orbit is
$e=\frac{r_a}{a}-1$
$e = -\frac{r_p}{a} +1$

### true anomaly ($\theta$)
this is how far along the orbit a spacecraft is. it is measured as an angle from the periapsis, for example $0$ at the periapsis and $180$ at the apoapsis

### orbital inclination ($i$)
this is how out of plane the orbit is with respect to the equator. it can be between 0 and 180 degrees

### right ascension of the ascending node ($\Omega$)
this is where on the surface the spacecraft goes from the southern to the northern hemisphere. it is measured with respect to a [[wk 4 - orbital mechanics#datum point for the orbital elements|a reference point]].
this won't be defined if $i=0$ because the spacecraft is always orbiting over the equator

### argument of perigee ($\omega$)
this defines where in the orbit the spacecraft comes closest to the planet. it is measures from the ascending node.
if $e=0$, there is no perigee


### datum point for the orbital elements
to specify the right ascension of the ascending node, there needs to be a fixed point in space.
The 'first point of aries' is used, and it is the direction of the sun when the earth is at the spring equinox, and it lies in earth's equatorial plane.
The right ascension of the ascending node is  defined by how far from the first point of aries it is.

## using the orbital elements
perigee is when $\theta = 0$, so the radius at perigee is $r_p = a(1-e)$, and similarly the radius at apogee is $r_a = a(1+e)$ 


## orbital energy

$\text{KE} + \text{PE} = \text{constant}$
after some algebra, $\frac{V^2}{2} - \frac{\mu}{r} = -\frac{\mu}{2a}$ so 
for a circular orbit this simplifies to $V = \sqrt{\frac{\mu}{r}}$

## orbital transfers
$\Delta V$ is normally minimised
It is assumed that transfers are impulsive
$\Delta V = V_{ex} \ln \left(\frac{M_o}{M_b}\right)$ where $M_o$ is the original mass before the burn and $M_b$ is the mass of propellent burned during the maneouver

### assumptions
the orbit before and after the burn intersect. This means that the point of the burn is on both of the orbits
transfers between non intersecting orbits need at least 2 burns
$\Delta V$ is the magnitude of the difference of velocities between the two orbits

### hohmann transfers
This is a transfer between two coplanar circular orbits

at the smaller orbit $r_1$, speed is given by $V_1 = \sqrt{\frac{\mu}{r_1}}$
there is then a burn of $\Delta V_{TP}$.
this puts the craft on an elliptical orbit with a semimajor axis of $2a_T = r_1 + r_2$
Using the full energy equation, the speed at the perigee of the transfer orbit can be calculated, $V^2_{TP} = \mu \left( \frac{2}{r_1} - \frac{1}{a_T}\right)$ and then $\Delta V_{TP}  = V_{TP} - V_1$
$V^2_{Ta} = \mu \left( \frac{2}{r_2} - \frac{1}{a_t}\right)$ and $V_2 = \sqrt{\frac{\mu}{r_2}}$, so $\Delta V_{Ta}  = V_{Ta} - V_2$
this means that the full $\Delta V$ for the whole transfer is $\Delta V = \Delta V_{TP} + \Delta V_{Ta}$ 

time on the transfer can be found with $\tau = 2\pi \sqrt{\frac{a^3}{\mu}}$. *note that this gives the time for the full orbit*

fuel burn is found through $\frac{x-1}{x}$, where $x = e^{\frac{\Delta V}{V_{ex}}}$

$[\frac{\hat{\theta}(1-\hat{\theta})}{n}]^\frac{1}{2} = [\frac{\bar{x}(1-\bar{x})}{n}]^\frac{1}{2}$
