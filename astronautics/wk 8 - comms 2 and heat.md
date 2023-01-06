#astro
# lecture 1 - more communications

## frequency bands
There is more loss at $15°$ elevation because the signal travels further through the atmosphere
![[Pasted image 20221122120656.png]]
the bit between $0.1-30 GHz$ is the frequency band that is usable
![[Pasted image 20221122120753.png]]

satellite bands are allocated by the ITU (international telecommunications union), because there are only so many frequency bands.
![[Pasted image 20221122121010.png]]

## encoding

space comms are usually digital
the bit error rate is a measure of link quality
It is the number of bits that are acceptable to be lost

### pulse code modulation
pulse code modulation is commonly used for encoding
it samples the analog voltage and encodes it as a series of bits
it is sampled every $t_s$ seconds, meaning the sampling frequency is $f_s = t_s ^{-1}$
the sampling frequency needs to be at least double the maximum frequency in the signal

for a human voice, if there are 256 levels, this needs 8 bits to transmit this.
the maximum important frequency is $3400Hz$, so the sampling frequency rate should be around $8kHz$ so the data rate is the frequency times the number of bits, $R_b = 8000 \times 8 = 64kbps$.

### digital modulation techniques:
Amplitude shift keying
Frequency shit keying
Phase skift keying - every time there is a change between a 0 and a 1 the phase of the wave inverts
![[Pasted image 20221122122301.png]]
the most commonly used is PSK, but all of them are used.
#### ASK
This changes the power of the system, which can be problematic
#### FSK
the frequency bands are already very tight, so changing frequencies can be problematic
#### PSK
This doesn't have those two downsides
each bit takes the same amount of time, so the higher the frequency, the higher the maximum data rate/bandwidth

### maximum data rate
$R_{max} = B \log_2 \left( 1+\frac{S}{N} \right)$
where $B$ is the bandwidth in $Hz$ and $R_{max}$ is the maximum data rate in bits per second. $\frac{S}{N}$ is the signal to noise ratio
the effectiveness of a link is characterised by the signal to noise ratio

sources of noise include:
the atmosphere
the sun, earth and galactic sources
lightning
artificial sources (cars etc)
internal electronic devices

the sources are characterised by an equivalent noise temperature ($T$, measured in kelvin) so the noise power is given by $N = kTB$, where $k$ is the boltzmann constant

## antennas
an **isotropic radiator** gives equal intensity in all directions
gain is $0dB$
It can be thought of like a lightbulb

a **high gain antenna** concentrates power in one direction
it can be though of like a torch

The power is concentrated down the boresight.
the half power point is where the power of the antenna is $3dB$ lower than at the maximum power point

The beamwidth is an angle and it is at what angle the power drops to $3dB$. it is given by $\theta = 72 \frac{\lambda}{D}$

The gain is $G = \frac{\text{maximum power flux}}{\text{power flux of an isotropic radiator}}$
$G = \eta \left(\frac{\pi D}{\lambda}\right) ^2$ and $\eta = 0.65$ typically
As $D$, the antenna diameter increases, the gain will increase at $D^2$ but the beamwidth will reduce at a rate of $\frac{1}{D}$

### example
for an antenna working in the C-band ($4GHz$):
wavelength = $c=f\lambda$ so $\lambda = 0.075m$
using a 1 meter dish:
$\theta = 72 \frac{0.075}{1} = 5.4°$
$G = \frac{\pi \times 1 }{0.075} ^2=1140.5 = 30.6dB$
at a 6m dish:
$\theta = 0.9$
$G = 46.1dB$

# lecture 2 - thermal control

because components are built primarily on earth, the spacecraft cant be too far from earth temperature for longevity and reliability
![[Pasted image 20221124130436.png]]

payloads may also need a specific thermal environment
IR cameras may need cooler temperatures


## heat transfer mechanisms
**conduction** works for moving heat from one part of the spacecraft to another part

**convection** doesn't work because the mean free path of particles is large, so there aren't enough particles to transfer the heat

**radiation** is the dominant transfer mechanism between the spacecraft and its environment
This goes from the spacecraft to the environment as well as from the environment to the spacecraft

## heat sources

the sun gives off energy at about $1.4kW/m^2$ 
the earth radiates energy at about $0.24kW/m^2$
the earth reflects energy from the sun onto the spacecraft. this is the albedo and it is typically about $34\%$
electronic devices, batteries and engines give off heat too

## heat emitters
the spacecraft will radiate IR radiation from all of its surfaces

## heat balance

any incident radiaton at wavelength $\lambda$ with intensity $q_i (\lambda)$ 
spectral absorptance $\alpha_\lambda = {q_a (\lambda) \over q_i (\lambda)}$
spectral reflectance $\rho_\lambda = \frac{q_r (\lambda)}{q_i (\lambda)}$ 
spectral transmittance $\tau_\lambda = \frac{q_t (\lambda)}{q_i (\lambda)}$

these add to 1
most spacecraft materials have 0 transmittance, so a black body can be used to model the spacecraft

### black bodies
absorbtance $\alpha_\lambda$ is 1 for all wavelengths

## spacecraft equilibrium temperature
environmental inputs + internally generated power balances with the radiation loss of the spacecraft

$$
q_s \alpha_s A_s^{\text{proj}} + a q_s\alpha_s A_E^{\text{proj}} \cos \phi \beta \left(\frac{R_E}{R_{orb}}\right)^2 + q_E \epsilon A_E^{\text{proj}}\left(\frac{R_E}{R_{orb}}\right)^2 + P = \epsilon\sigma T^4 A_{surf}
$$
$q_s$ is the energy from the sun, and is about $1350W/m^2$
$\alpha_s$ is the solar absorptance 
$A_s^{\text{proj}}$ is the projected area of the spacecraft relative to the sun

$a$ is earth's albedo, about 0.34
$A_E^{\text{proj}}$ is the projected area of the spacecraft relative to the sun
$\beta$ is $1$ when the spacecraft is on the daylight side, and $0$ when the spacecraft in on the nighttime side

$q_E$ is the energy from earth
$\epsilon$ is absorbtance

$\sigma$ is the stefan-boltzmann constant
$A_{surf}$ is the surface area of the spacecraft

# pre-recording

## finding the link budget equation
to find the limits of a communications system, the spacecraft is the transmitter with gain $G_T$ and the ground station is the receiver with gain $G_R$. The distance between them is the slant range $\rho$.

If the antenna were isotropic, the power flux at the antenna in $W/m^2$ would be given by $\phi = \frac{P_T}{4\pi \rho^2}$. Because a high gain antenna is being used instead, the gain also comes into affect. $\phi = \frac{G_T P_T}{4\pi \rho^2}$
$\phi$ is the power flux, so to find power is just $P_R = \phi A_{R, eff}$
$A_{R, eff}$ is the effective area of the receiving antenna

The effective area of the receiving antenna is $A_{eff} = \frac{G \lambda^2}{4\pi}$
putting this into the other equation gives $P_R = \frac{P_TG_T}{4\pi\rho^2} \frac{G_R \lambda^2}{4\pi}$. 
$\frac{1}{4\pi\rho^2}\frac{\lambda^2}{4\pi} = \left(\frac{\lambda}{4 \pi\rho}\right)^2$ is grouped together into the free space loss so the equation becomes $P_R = \frac{P_TG_TG_R}{L_{FS}}$
$L_A$ is additional losses due to atmosphere, depointing, etc. This gets added onto the denominator

Noise hasn't been included yet. It is given by $N_0 = kT_R$
carrier power is defined so $C = P_R$

With these two new terms, the equation becomes $\frac{C}{N_0} = \frac{P_TG_TG_R}{L_{FS}L_A} \frac{1}{kT_R}$. This is now an equation about signal to noise.

in decibels, this gives the link budget equation
$$
\begin{align}
10\log_{10}\left(\frac{C}{N_0}\right) = 10\log_{10}\left(P_TG_T\right) + 10\log_{10}\left(\frac{G_R}{T_R}\right) -20\log_{10}\left(\frac{4\pi\rho}{\lambda}\right)\\- 10\log_{10}\left(L_a\right) - 10\log_{10}\left(k\right)
\end{align}
$$
$$
\begin{align}
\text{power to noise density} = \text{EIRP} + \text{Ground station figure of merit} - \text{free space loss}\\ - \text{ atmospheric losses} - \text{constant}
\end{align}
$$
only the power to noise density and the EIRP can be controlled
The EIRP is the power of an isotropic radiator that would be needed to get the same power flux at the reciever

## finding required power to noise
the time to transmit one bit of information is $t_b = \frac{1}{R_b}$
so the power of a transmission is  $C=\frac{E_b}{t_b}$
This means that $\frac{C}{N_0} = \frac{E_b}{N_0}R_b$ 

![[Pasted image 20221125114407.png]]

## example
![[Pasted image 20221125115643.png]]
### part 1

write down known facts:
$f = 4GHz \to \lambda = 0.075m$
$\rho = 38400000m$
$D_R = 0.4m$
$T_R = 150K$
$L_A = 5dB$

do calculations:
$G_R = 182.48dB$
$FoM = 0.85dB$
$L_{FS}  = 196.17dB$
$\text{constant} = -228.60dB$

to find $\frac{C}{N_0}$ from the bit error rate and the bit transfer rate, the equation and graph from [[wk 8 - comms 2 and heat#finding required power to noise|| the power to noise section]] is used.
$\frac{C}{N_0}$ and $\frac{E_b}{N_0}$ are in decibels, but $R_b$ isn't

the graph shows $R_b$ to be about 10
to get everything in decibels, the right side becomes $10\log_{10}\left(10\right) \times 10\log_{10}\left(92\times 10^6\right)$, so $10 + 10\log_{10}\left(92\times 10^6\right)$ 
this shows that $\frac{C}{N_0} = 89.64dB$

$\text{EIRP} = \frac{C}{N_0} - FoM + L_{FS} + L_A + \text{constant}$
$\text{EIRP} = 61.36$
![[Pasted image 20221125121232.png|300]]

### part 2

$D_T = 2$
$G_T = 36.59dB$

the next equation only works when everything is in decibels
$P_T  = EIRP - G_T$

$P_T = 24.77dB$
$P_T = 299.47W$
![[Pasted image 20221125122658.png|300]]