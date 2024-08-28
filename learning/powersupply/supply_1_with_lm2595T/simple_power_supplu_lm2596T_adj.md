## LM2596T-ADJ based power supply

This is a simple circuit to provide dual DV output (5V and 12V), using the  LM2596-ADJ switching voltage regulator. 

The LM2956 integrated circuits  provide all the active functions
for a step-down (buck) switching regulator, capable
of driving a 3-A load with excellent line and load
regulation.

See datasheet: https://www.ti.com/lit/ds/symlink/lm2596.pdf?ts=1724714915348&ref_url=https%253A%252F%252Fwww.ti.com%252Fproduct%252FLM2596


## Circuit 
![](./puspply.png?raw=true "Dual 5V 9V Lm2596T power supply")

### Transformer
ne5551.gif

This example uses a 220 to 12V center-tap transformer to step down the voltage.
The transformer is rated 30VA, thus it can provide up to 2.5 A of current

### Rectification
This example uses 2 1N5404 diodes in a full-wave rectifier configuration
https://components101.com/diodes/1n5404-general-purpose-rectifier-diode


**See the below calculations for the rectified values**
```shell
RMS Voltage: Vrms (from transformer ) = 12V

Passing AC voltage through a diode would result in the peak value of that voltage
Peak Voltage Vpeak = Vrms * √2  = 16.97V

Diode voltage drop for the 1N5404 = 0.5V
Therefore the toal rectified voltage is 16.97 -.5 = 16.47

The avaerage DC (i.e what would be measured by a digital volt meter) = 
  2Vpeak/𝛑 or Vpeak * 0.637
  = 10.5V (approximately)
  
```

### The LM2596T
The two LM2596T switching voltage regulator IC's would be used to step regulate the voltage, to 5V and 9V output
The LM2596T has the following formula to determine the output voltage using the two resistors connected to PIN 4 (The feedback pin)

Formula
Vout = Vref(1 + (R2/R1)) ; where Vref = 1.23

If we use a fixed value for R1 say 1k ohm resistor, we can re-arrange the equation for R2:
R2 = R1((Vout/Vref) -1)

So example for a 20V regulated output we have
R2 = 1k((20/1.23)-1) = 15.260Ohms (15Kohms should suffice)



### Input and Output Capacitors
The input and output capacitors labelled with (c in, c out), must be high ESR and high frequency capacitors
and should be rated for at least 1.5 the voltage of the output voltage
So e.g for the 9V output at least a cap. rated at 13.5 volts should be used

### Output Inductors
The inductors should be either Toroid's or E-core and shielded to avoid parasitic inductance. 
They should be rated for the output current (3A)




