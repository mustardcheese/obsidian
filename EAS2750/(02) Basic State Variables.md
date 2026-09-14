**fill in older notes**

## Air Pressure

### Topography Map
![[Pasted image 20260831094036.png|600]]
- Zonal: east-west (x-axis)
- Meridional: north-south (y-axis)
- Vertical: up-down (z-axis)

### Units
- $1mb = 1hPa = 100Pa$
	1 milibar = 1 hectopascal = 100 pascals
- $1 Pa = 1 N m^{-2} = 1kg m^{-1} s^{-2}$
	pressure = force/area == pa
- $1\ in\ Hg = 33.86hb$
	1 inch of mercury = 33.86 milibar
Average mean sea level pressure ~ 1013.25hPa ~ 1 bar

Base SI unit is Pa, **use pascals in all calculations**

### Surface Pressure
![[Pasted image 20260831094628.png|600]]
- The air pressure at the surface
- Higher elevation, lower pressure
- Lower elevation, higher pressure
The difference in pressure is so much more drastic due to elevation than any other pressure changes, meaning every time we want to plot this it would almost always look the same.


![[Pasted image 20260831094926.png|600]]
Adjusted for mean sea level pressure, surface pressure adjusted to as if it were at sea level
$p = p_0 e^{-\frac{Z}{H}}$ is used to solve
	$p_0$ sea level pressure
	$Z$ height
	$H$ scale height

## Ideal Gas

The atmosphere is approximately an ideal gas, so their interaction can generally be descrbied as the Ideal Gas Law

$p = \rho R_d T$
- $\rho$ density
- $R_d$ dry air gas constant
- $T$ temperature

When we assume pressure is constant, then:
- $\rho \propto \frac{1}{T}$
- Density is inversely proportional to temperature
- Warmer air is less dense than cold air

When we assume temperature is constant, then:
- $p \propto \rho$
- Pressure and density are directly proportional

When we assume density is constant, then:
- $p \propto T$
- Pressure and temperature is directly proportional

## Wind

![[Pasted image 20260831100659.png|600]]

Wind is just air moving due to differences in temperature, pressure, and density

Results from differential heating, where differences in temperature of earth are caused by different parts of the earth getting different amounts of sun

### Units
mph, knots, m/s
- 1kt = 0.52m/s
- 1mph = 0.447m/s
- 1kt = 1.15mph

### Direction
Wind is a vector, has direction

The suffix "**ly**" is used to describe where wind is blowing **from**
- Westerly wind means blowing from west to east
The suffix "**ward**" is used to describe where the wind is blowing **towards**
- Eastward wind means blowing from west to east


zonal wind $u = \frac{dx}{dt} =\frac{\Delta x}{\Delta t}$
meridional wind $v = \frac{dy}{dy}=\frac{\Delta y}{\Delta t}$
vertical velocity $w = \frac{dz}{dt}=\frac{\Delta z}{\Delta t}$


From a wind vector, we're able to go backwards to derive zonal and meridional
$u = -Msin(\alpha)$
$v = -Mcos(\alpha)$
- M is the magnitude
- $\alpha$ is the direction in degrees, where it comes from
$M = \sqrt{u^2 + v^2}$
![[Pasted image 20260831101647.png|400]]


Southwesterly @ 20
u = -20sin(225) = 14.14

Westerly @ 13
u = 13

Southwesterly @ 20 is faster 

## Moisture
Relative Humidity
- A quantity or percentage expressed between 0 and 1 or 0% and 100%. How close you are to saturation, RH~100% means a cloud, fog, or percipitation

Dew Point
- Temperature at which if lowered to this value, the atmosphere saturates and due forms

Wet-Bulb
- Temperatured measured by a thermometer covered by a wet cloth. The greater the difference between the temperature and the wet bulb temperature, the lower the RH.
- When the wet bulb is swung around and the water evaporates, the temperature is checked and is used to measure moisture