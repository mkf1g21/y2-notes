#astro
# lecture 1
if adequate control of power isn't there, the spacecraft could lose pointing accuracy, reach a thermal limit etc. 

solar arrays, batteries, fuel cells, solar dynamic devices, RTGs and nuclear reactors can all be used for power

## primary and secondary power
**primary power systems** are the main source of power for the vast majority of the time (solar arrays, RTGs)
**secondary power systems** are energy storage devices for when the primary power can't provide power. They act as backups. These are usually batteries, but other things can be used

## kinds of primary power sources
![[Pasted image 20221115122749.png]]
### solar arrays
these convert solar radiation $(\approx 1370Wm^{-2})$ into electiacl energy. These are usually $10-20\%$ efficient.
These are good for earth orbiting spacecraft, but further out from the sun, as the sun's light fades away, they become useful.

### primary batteries
This are which batteries, whih are used for short duration missions. This is for example in first stages

### fuel cells
This combine hydrogen and oxygen to make water and power

### solar dynamic divices
This uses something like a parabolic mirror to heat up a working fluid to turn a turbine
This is a lot more efficient than a solar cell, but also a lot heavier

### RTGs
These use the heat of a radioactive decay to generate a voltage across a thermocouple. 
The power they make will go on for a long period of time
Because of the radiation, there will have to be design accommodations
It can make the thermal control systems harder because it will be making heat no matter what
One of the main reasons the voyager missions are still active is because the RTGs are still making heat

RTGs are heavily regulated and cant be launched in the EU. In the US, they need presidential approval. They can be launched in russia

## power bus
![[Pasted image 20221115123206.png]]
This applies to all power sources

# lecture 2

Decibels show the ratio in power levels. it is an exponential system

# pre recorded lecture

## solar arrays
### things to take into accound
one of the reasons that solar cells have a relatively low efficiency is that the p and n type semiconductors have to be optimised for one wavelength of light, for example $1.1eV$. If light with $1.0eV$ falls on the cell, no energy will be made. if light of $1.6eV$ hits the cell, $0.5eV$ will be wasted as heat. 
the power of a solar cell is $\eta  = \frac{ P_{out}}{P_{in}}$ and it is typically $0.1-0.3$. $P_{out}$ is the electrical power output and $P_{in}$ is the power in the sunlight, typically around $1370Wm^{-2}$ near earth
![[Pasted image 20221122112039.png]]
hot solar cells tend to give high current but low voltage, and a cold cell gives high voltage but low current. low temperatures increase power.
this can cause problems, because solar panels need to be in the sun. This means that there needs to be a way to get rid of this excess energy.
This means that solar cells work well as "wings", they can easily have radiators on the backside of them. body mounted solar panels can be difficult, because the radiated energy goes into the spacecraft.
high power at low temperature can also lead to power issues when the satellite exits eclipse, when the solar panels are cold and producing a lot of power

for every degree the cell is off from pointing at the sun, the power drops. this is approximately equal to a cosine law

as the satellite spends time in orbit, solar radiation will affect the solar array, meaning that at the end of life, the solar array's current and voltage will drop.
different n and p type semiconductors have different resistances to radiation damage, but they also have different efficiencies

### sizing up an array
putting cells in series increases voltage
putting cells in parallel increases current
this is like batteries

Each solar panel will have some area that is used in wiring up cells to eachother, not generating power. This is known as the packing efficiency

## batteries

### battery chemistries
nickel cadmium is an older chemistry, usually used in older spacecraft
nickel hydrogen is being phased out, but is still used in some spacecraft
lithium ion is the current choice of battery
lithium polymer is undergoing ESA approval

lithium ion has a significantly higher energy density and discharge voltage.