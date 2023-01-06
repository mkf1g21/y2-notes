#astro
## assessment info
science mission to fly to Jupiter to find information, split into numerical answers and presentation 

exam hopefully online but not sure yet

---
# lecture 2 - systems engineering

for a spacecraft, you cant just chance one subsystem, because it will lead to knock on consequences for the other subsystems
you cant just go for the best of each of the subsystems, sometimes you have to make tradeoffs to have the most effective spacecraft overall. This may mean compromising on the detectors, attitude control or power etc. This is the role of a systems engineer.

the support systems for the detectors, such as the attitude control system, power systems, data handling and so on are called the **spacecraft bus**, because they only exist to transport and allow the detectors to operate

### design process
1) generally mission objectives should be quantitative. These will come from the customer
2) experts in the field of the payload will define the payload and how it operates
3) top level requirements will then be generated to decide things like flyby geometry
4) design parameters can then be made, these include things like $\Delta V$, field of view, slew rates etc

The customer should be kept in the loop the whole time during the design to make sure the spacecraft actually meets the requirements

in ECSS-E-ST-10C, phase C, D, E are very expensive

one example of a trade-off is chemical vs electric propulsion. Electric is significantly more efficient, but the thrust is a LOT smaller.