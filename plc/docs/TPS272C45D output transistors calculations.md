# TPS272C45D Output Transistors

Used for outputting power to channels 1-4.

Variant 'D' has dual fault FLT1/FLT2 to provide detailed fault diagnosis.
[Product Link](https://www.ti.com/product/TPS272C45/part-details/TPS272C45DRHFR)

## Current limit

The current limit for each channel is measured using the following formula:
`I_CL = K_CL / R_ILIM`,

with the constant `K_CL` being 20.5 A.kΩ. `R_ILIM` is limited between 5 kΩ and 28.2 kΩ.
Using 5.1 kΩ resistors this will put the output current at a maximum of 4.02 A.

## Current sense
The `SNS` pin outputs a current that is proportional to the load current through either channel, depending on the state of the `SEL` pin.
When the `SEL` is low, `SNS` outputs load current proportional to channel 1, and if `SEL` is high, channel 2.

`I_SNSI = I_OUT / K_SNS`,

with the constant `K_SNS` being 1200.
There is also a low-pass RC filter to improve the current sense value.
Values for `R_PROT`, `C_SNS` are 10 kΩ and 100 pF, and are the recommended ones by TI for common functionality.

`R_SNS` is 620 Ω.

How the `R_SNS` value was chosen:
- the biggest measurable value is 4 A, which is also the limit
- the external ADC, ADS1115 range is +- 4.096 V, but we can use +-2.048 V range, and get finer measurements
- since `V_SNS = I_OUT × R_SNS / K_SNS`, with `I_OUT` variable from 0 to 4 A, `R_SNS` is close to 620 Ω
- this will clip the voltage just under 4 A, but it's reasonable

## Fault indication

`FLT` is active low.

There are 4 types of faults indicated on the `FLT` pins:
- FET thermal shutdown
- Active current regulation
- Thermal shutdown caused by current limitation
- Open-load (FET OFF state only)