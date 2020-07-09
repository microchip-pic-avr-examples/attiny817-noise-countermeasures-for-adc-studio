<!-- Please do not change this html logo with link -->
<a href="https://www.microchip.com" rel="nofollow"><img src="images/microchip.png" alt="MCHP" width="300"/></a>

# Noise Countermeasures for ADC Applications

This repository will explain how and when to use the powerful noise suppression features available on the Microchip tinyAVR® 1-series and megaAVR® 0-series ADCs. In these ADCs, the input signal is fed through a sample-and-hold circuit which ensures that the input voltage to the ADC is held at a constant level during sampling. The ADC supports sampling in bursts where a configurable number of conversion results are accumulated into a single ADC result (sample accumulation). Further, a sample delay can be configured to tune the ADC sampling frequency associated with a single burst. This to tune the sampling frequency away from any harmonic noise aliased with the ADC sampling frequency (within the burst) from the sampled signal. An automatic sampling delay variation feature can be used to randomize this delay to slightly change the time between samples.

<br/>Topics covered include using the ADC hardware sample accumulator to filter out zero mean random noise and surpassing harmonic noise through tuned sampling delays or automatic sampling delay variation. The noise filtering is demonstrated by using an example source code and plotting a graph of ADC samples in Data Visualizer in Atmel Studio. This is explained in detail in the document [*AN2551 - Noise Countermeasures for ADC Applications*](https://www.microchip.com/DS00002551) by Microchip. The code is run on a ATtiny817 Xplained Pro board. 

## Related Documentation

- [AN2551 - Noise Countermeasures for ADC Applications](https://www.microchip.com/DS00002551)
- [ATtiny817 Xplained Pro User Guide](https://www.microchip.com/DS50002684)
- [ATtiny817 Data Sheet](https://www.microchip.com/DS40001901)
- [ATtiny817 Device Page](https://www.microchip.com/wwwproducts/en/ATtiny817)
- [Data Visualizer Software User's Guide](https://www.microchip.com/DS40001903)

## Software Used

- [Atmel Studio](https://www.microchip.com/mplab/avr-support/atmel-studio-7) 7.0.2397 or later
- [AVR/GNU C Compiler](http://packs.download.atmel.com/) 
- [Atmel Studio DFP](http://packs.download.atmel.com/) 1.4.308 or later

## Hardware Used

- [ATtiny817 Xplained Pro](https://www.microchip.com/DevelopmentTools/ProductDetails/attiny817-xpro)
- Micro-USB cable (Type-A/Micro-B)

## Setup

1. Connect the ATtiny817 Xplained Pro board to the PC using the USB cable.


## Operation
1. Download the zip file or clone the example to get the source code.

2. Open the .atsln file in Atmel Studio.

3. Configurations:
    - CPU clock: (default) 3.33 MHz.
    - Peripherals used:
        - ADC, TCA, USART, VREF.
        - ADC input channel is AIN 5: Pin PA5, 10-bit ADC resolution.
        - TCA: PWM signal is generated on pin PB0: 62 kHz, 50% duty cycle.
        - USART: TXD PB2, Baud rate: 19200, ADC result is sent to the terminal.
        - VREF selects the ADC reference voltage to 2.5V.

4. Configure the macro definitions as below to plot a graph without noise.
    - #define HARMONIC_NOISE 0
    - #define ADC_64X_ACCUMULATOR_ENABLE 0
    - #define SAMPLING_DELAY 0
    - #define ENABLE_ASDV 0

5. Build the solution and program the ATtiny817. 
    
6. In *Atmel Studio* go to *Tools* and open *Data Visualizer*. Configure *Data Visualizer* to plot a graph of the ADC samples. Refer to Appendix A in the Application Note [AN2551 - Noise Countermeasures for ADC Applications](https://www.microchip.com/DS00002551) on how to do this. 

7. Try plotting different signals by combining the use of random noise, periodic noise, sample accumulation and sampling delay. You do this by reconfiguring the macro definitions before building and programming the device. The new graph will be plotted in *Data Visualizer*.

8. Refer to [Data Visualizer User's Guide](https://www.microchip.com/DS40001903) for help with *Data Visualizer*.



## Conclusion
  We have now looked at how to use the powerful noise suppression features available on the Microchip tinyAVR® 1-series and megaAVR® 0-series ADCs. The example described how to use the ADC hardware sample accumulator to filter out zero mean random noise and surpassing harmonic noise through tuned sampling delays or automatic sampling delay variation.
