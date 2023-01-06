#astro
# pre recorded lecture

angular rotation, $\omega$ is a vector quantity. Angular momentum, $H$ is also a vector. For rotation along a given axis, $I_{xx}$ is the moment of inertia along that axis

The change in the angular momentum of a system is the sum of external torques on the system. This is just $F=ma$ for rotation


## inertia matrix
In 3 dimensions, angular velocity is $\omega = \left( \begin{align} \omega_x \\ \omega_y \\ \omega_z \end{align}\right)$. Angular momentum is also still a vector, but now the moment of inertia is a matrix.
Because mass can be distributed weirdly, $H$ doesn't have to align with $\omega$

the matrix for inertia is given by $$I = \begin{pmatrix} I_{xx} & -I_{xy} & -I_{xz}\\
-I_{xy} & I_{yy} & - I_{yz}\\
-I_{xz} & -I_{yz} & I_{zz}
\end{pmatrix}$$
the components along the diagonal are the moments of inertia. The other values are the *products of inertia*, and these cause cross coupling, when a change in one axis of rotation affects another axis of rotation. They measure unbalance

Imagine a cylinder with one bit of mass offset on the outside, like sticking a magnet to a water bottle. When it spins on its long axis, the other axes with wobble a bit , and this is the cross coupling.

![[Pasted image 20221011101652.png]]

In something like a formula 1 car, the heavy parts are as close to the centre of mass as possible to minimise $I$, allowing it to go round a corner as fast as possible.

for a plane, the inertia matrix is important, because it is useful in finding out how big control surfaces need to be

## precession

![[Drawing 2022-10-11 10.22.53.excalidraw]]
This wheel is rotating anticlockwise, supported by a pivot behind it. If it were static, it would just fall forwards, with a maximum acceleration at the top and a minimum acceleration at the bottom. Because it is rotating instead, the acceleration builds up from the points in line with the support. 
The easiest way to remember this is the axis of rotation of the body rotates 90° in the direction of rotation compared to the static case
This is gyroscopic precession.


## momentum bias

The more angular momentum there is in a system, the more resistant it is to torque. This is called gyroscopic rigidity.
In a spacecraft, something onboard can be spun, or even the whole spacecraft can be spun, to increase the momentum bias

The attitude control system has to transfer angular momentum around a spacecraft, ie slowing the spin of the whole spacecraft by changing the angular momentum in reaction wheels. In this case, the sum of external torques is 0
It can also use external torquers to change the torque of the whole system. The sum of external torques is not zero.

Because of external influences, such as variations of gravity and atmospheric drag, there are always external torques on the spacecraft. this means that external torquers are necessary.
the environmental influences depend on the mission profile.

momentum bias can be used to give inherent stability, but it does have downsides. It only works along one axis, and that axis HAS to remain constant throughout the lifetime of the mission, otherwise there is no point to it.
It usually spins normal to the orbit plane.
momentum biases have to deal with nutation nodes, where external torques are applied, and because of the products of inertia, the wheel can oscillate in the two other axes. This will need dampeners to stop this.
a system with bias will have different torque responses. ![[Pasted image 20221011105058.png]] This is because of the nutation nodes



# live lecture 1

attitude control drives a lot of the design of the spacecraft
![[Pasted image 20221023114650.png]]
in orbit, a spacecraft won't naturally follow the prograde direction. This can be a good or bad thing depending on the objectives of the mission
in addition to the payload, other things need to point in specific directions, for example:
>communications need to face earth
>solar panels need to face the sun
>radiators need to face away from the sun
>thrusters need to point in the right direction

## there are 4 kinds of spacecraft stabilisation
![[Pasted image 20221011121811.png]]
### spinner spacecraft

They stiffen one axis, and this doesn't move. typically this axis is normal to the orbital plane.
The whole body of the spacecraft spins at around $10-60 rpm$. It has a large amount of mass spinning slowly to provide the stiffening
It wants minimum/zero products of inertia, maximum moment of inertia for the axis the spacecraft is spinning on ($I_{zz}$ for example), the other moments of inertia should be smaller than $I_{zz}$, but the same as each other. They should be the same for symmetry reasons.

Solar panels may be an issue for this kind of spacecraft, because they will be spinning with the rest of the body. 
Communications will be affected in the same way
Thermal subsystems will be affected, because rather than one side constantly getting sunlight, making big thermal gradients, the whole body gets heated up. It does mean that big radiators cant be used.

The nutation nodes will need to be dealt with, either by using passive dampers or active damping with control torquers


# live lecture 2
### dual spinner spacecraft
These have the top section despun, so the payload can still point in a fixed direction. The lower section is still spinning to provide gyroscopic rigidity

One of the issues that arises is the mechanical interface between the parts. Friction isn't too hard to deal with, but power and communications can be difficult to design
Even with the despun section, large solar panels can't be used because this will still impact the inertia matrix. This means the spacecraft is still power limited

Small deployable subsystems can still be on the craft, for example directional antennas

the spinning subsection still needs to have equal inertias on the axes that aren't spinning
nutations modes still exist



### Hybrid type spacecraft
These try to take the advantages of the last two and make it better
They use a small mass spinning fast (thousands of rpm), rather than a large mass spinning slow

the main disadvantage is there is essentially a dead mass onboard that is also taking up space.

the main advantage is that large solar arrays can be deployed now. This means the spacecraft is less power limited
the spin rate of the wheel can also be altered, so this can be used to control the spacecraft to some degree

Nutation still occurs so the ACS must stabilise it


### 3 axis stabilised spacecraft
There is no momentum bias, so anything can be deployed. There is no significant rotating component
This is used when motion on all axes is required by the mission
This is commonly used on space telescopes

They can have wheels, but not for bias.
Reaction wheels can be used, becuase usually they operate at very slow speeds, so produce insignificant inertia.

## Torques and Torquers
There are two kinds of torques on a spacecraft

### External torques
These are caused by interactions with the environment
There is a change in the overall angular momentum of the system
#### uncontrolled external torques
Examples include
- atmospheric drag ($< 500km$ mitigated by having an equal drag on the other side)
- gravity gradients ($30,000 - 40,000 km$)  [[wk 2 - momentum and attitude control#gravity gradients|explanation]]
- solar radiation (all heights)
- magnetic fields ($30,000 - 40,000 km$) [[wk 2 - momentum and attitude control#magnetic fields|explanation]]
- impacts
- misaligned thrusters (all heights) [[wk 2 - momentum and attitude control#misaligned thrust|more]]

##### gravity gradients
A long, thin satellite will tend to point towards the source of gravity, because it is a more stable configuration.

If the satellite starts parallel to the gravitational field, and is then rotated slightly, the end that is now slightly closer to the source of gravity will have a larger force on it. This unbalance in force continues until the spacecraft is pointing towards the earth

This mostly affects long, thin spacecraft, like telescopes or space stations

It can be used for passive stabilisation, like in seasat

##### magnetic fields
the electronics on board will interact with the earth's magnetic field, so will cause a torque. magnets can be placed on board to give the spacecraft more stability, so it can also be used as passive stabilisation. This is commonly done in cubesats

##### misaligned thrust
If there are many delta v manoeuvres over the lifetime of a spacecraft, this will dominate the external torques. In this case, spin stabilisation can be useful, because it distributes the torques fairly evenly, like for the case of the Galileo spacecraft

#### controlled external torques

Some external torques are controllable. For example
- control thrusters [[wk 2 - momentum and attitude control#gas thrusters|more]]
- magnetorquers [[wk 2 - momentum and attitude control#magentorquers|more]]
- adjustable spacecraft geometry [[wk 2 - momentum and attitude control#adjustable geometry|more]]

##### gas thrusters
easy to scale up to get the right amount of torque
only have on or off, fine control has to be achieved by pulsing them on and off
they need propellant

for control of all 3 axes, this can get complicated quickly, needing a minimum of 12 thrusters. This will complicate things further with the need for feed lines

##### magentorquers
Essentially an electromagnet.
One can be used on each axis to align with the earth's magnetic field

The magnetic fields onboard can interact with electronics onboard
It requires a lot of power
There is no rapid response. These are more of a long term thing.
You need to know the magnetic field around you

There are no moving parts, so this can make it more reliable
No propellant is needed

##### adjustable geometry
This changes the shape of the spacecraft to take advantage of solar or aerodynamic pressures

This needs an understanding of the torques needed to be overcome in the first place
It adds complexity

new area of research
no propellant burn


### Internal torques
These are caused by interactions between two parts of the spacecraft
angular momentum is conserved


# wk 2 lecture 1
### uncontrolled torques
Examples of this are things deploying, astronauts moving and fuel moving

### controlled torques
dual spin mechanisms, reaction wheel, momentum wheel

reaction wheels are used for slew manoeuvres, but momentum wheels are just used for the stiffening effect.
Reaction wheels tend to be spun slower, but they can go in both directions

#### reaction wheel demos
They just show $I_1 \omega_1 = I_2 \omega_2$, the videos are on blackboard

There is also a demo of using gyroscopic precession through gimbaling. This is also called a control moment gyro

reaction wheels can become saturated. To desaturate them, external torquers must be used.

### using momentum storage
if a satellite is in a circular orbit and it always needs to face earth, it is easy to do, it just needs a rotation rate that matches that of the earth

if it is in an elliptical orbit, it gets a lot more complicated. At apogee, it needs to rotate a lot slower than at perigee.
This can be achieved with a reaction wheel, spinning it up at apogee and spinning it down at perigee
To make it more complicated, large deployables may provide a continuous torque. This would mean the wheels would need to continuously increase/decrease forever, which will eventually overload the motors/wheel. Then, a momentum dump needs to be done with external torquers. This could also be controlled with spacecraft design, like magentorquers or adjustable geometry

## sensors
**attitude control is always less accurate than the measurements**
there are 2 kinds of sensors, reference and inertial

### reference sensors
these look at external objects to find position, such as stars.
It isn't guaranteed that they will always be visible 

potential accuracy is limited by the object used as reference
![[Pasted image 20221018124524.png]]
\*gps is dependant on reciever baseline


### inertial sensors
these measure accelerations in the spacecraft, such as gyroscopes
They don't stay constant, and they can drift. Despite the advances, they still drift so they need to be recalibrated with a reference sensor.
MEMS has made IMUs a lot better

## on board vs ground control
historically, the lack of compute made ground processing more useful
recently, computers are a lot more powerful so the on board computer can do more

typically, there is an initial acquisition mode, to first figure out where the sun, earth and other celestial obects are. This is typically also the safe mode
once the craft knows where it is, thruster control mode can be used. This can also be used for momentum dumps
normal mode is used after thruster control mode
