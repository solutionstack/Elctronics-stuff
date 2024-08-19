## NE555 Oscilator

The 555 timer IC is a popular integrated circuit that can be used as a timer an oscillator or in delay circuits.


When used as an oscillator it is known as an astable multivibrator circuit and it provides a continuous square wave output without further external action


### Basic astable schematic
ne5551.gif

![](./ne5551.gif?raw=true "NE555 astable")

In the 555 Oscillator circuit above, pin 2 and pin 6 are connected together allowing the circuit to re-trigger itself on each and every cycle allowing it to operate as a free running oscillator. During each cycle capacitor, C charges up through both timing resistors, R1 and R2 but discharges itself only through resistor, R2 as the other side of R2 is connected to the discharge terminal, pin 7.

The capacitor charges up to 2/3Vcc (the upper comparator limit) through both resistors R1 and R2 which is determined by the **0.693(R1+R2)C** combination. It then discharges itself down to 1/3Vcc (the lower comparator limit) through resistor R2 only which is determined by the **0.693(R2*C)** combination.


## Example
#### In our exammple we're going to use a variable (4K) resistor for R2 a 1k resistor for R1 and a 4.7nf (nano farads) capacitor as the Charging capacitor C<sub >1</sub>. C<sub >2</sub> and C<sub >3</sub> are filter capacitors

#### Giving us the following characteristics

#### Time on T<sub>on</sub><br/> = 0.693 * (1,000 + 4,000) * (4.7 * 10<sup>-9</sup>) = 16ms
#### Time of T<sub>off</sub><br/> = 0.693 * (4,000) * (4.7 * 10<sup>-9</sup>) = 13ms
#### Period P <br/>
#### Frequency _f_<br/>
At minimum position the variable resistor R2 is approximately 1ohm, so,
frequency  = 1/T or 1.44/(R1 + 2R2) * C <br/>
= 1.44/ (1,000 + (2*(1))) * (4.7 * 10<sup>-9</sup>)
= 305.7714Khz

At maximum position the variable resistor R2 is approximately 4Kohm, so,
/T or 1.44/(R1 + 2R2) * C <br/>
= 1.44/ (1,000 + (2*(4000))) * (4.7 * 10<sup>-9</sup>)
= 34.0426 Khz

#### Duty cycle<br/>
T<sub>on</sub> /T<sub>off</sub> + T<sub>on</sub>(%)<br/>
(16/16+13) * 100
Approximately 55%

![](./ne555_example.png?raw=true "Example")
