---
slug: /slider-potentiometer/arduino-3 
title: Reading Slider Potentiometer (Qwiic version)
id: slider-potentiometer-arduino-3
hide_title: False
---

This page contains some simple examples on how to take analog slider measurements using the Slider Potentiometer with Qwiic.

---

## Initialization

To start using the **Slider Potentiometer Breakout**, you need to connect it to your microcontroller. The potentiometer acts as a voltage divider, and its output can be read through an analog pin on your microcontroller.

Here’s how you can set it up:

```cpp
#include "Slider-potentiometer-easyC-SOLDERED.h"

// Declare the sensor object
sliderPot slider;

void setup()
{
    // Initialize the serial communication via UART
    Serial.begin(115200);

    // Initialize the sensor
    slider.begin();
}
```

<FunctionDocumentation  
  functionName="slider.begin()"  
  description="Initializes the Slider Potentiometer Breakout, setting up the necessary configurations for reading analog values from the potentiometer. This function ensures that the potentiometer is ready for use and properly connected to the microcontroller."  
  returnDescription="**Returns `true`**: If initialization is successful, indicating that the potentiometer is properly connected.  
- **Returns `false`**: If initialization fails, indicating a connection issue or incorrect setup."  
  parameters={[]}  
/>


---

## Reading slider given data

To start reading data given by moving the slider we can follow the code given bellow.

```cpp
    Serial.print("Raw value of slider potentiometer: "); //Print information message
    Serial.println(slider.getValue()); //Prints raw value of slider potentiometer

    Serial.print("Minimum value of slider potentiometer: "); //Print information message
    Serial.println(slider.minValue()); //Prints minimum value of potentiometer

    Serial.print("Maximum value of slider potentiometer: "); //Print information message
    Serial.println(slider.maxValue()); //Prints maximum value of potentiometer

    Serial.print("Percent value of slider potentiometer: "); //Print information message
    Serial.println(slider.getPercentage()); //Prints percent value of slider potentiometer
    delay(1000);
```

<FunctionDocumentation  
  functionName="slider.getValue()"  
  description="Reads the raw analog value from the slider potentiometer and returns it as an integer. The value corresponds to the position of the slider, typically ranging from 0 (one end) to 1023 (the other end) on a 10-bit ADC system."  
  returnDescription="**Returns an integer**: The raw analog value of the slider potentiometer, representing its position."  
  parameters={[]}  
/>

<FunctionDocumentation  
  functionName="slider.getPercentage()"  
  description="Calculates and returns the current position of the slider potentiometer as a percentage. The percentage is derived by mapping the raw analog value to a range of 0% (minimum position) to 100% (maximum position)."  
  returnDescription="**Returns a float**: The position of the slider as a percentage (0% to 100%)."  
  parameters={[]}  
/>


---

## Full example

Try all of the above-mentioned functions in this full example which prints out the measured gyroscope data over Serial at 115200 baud:

```cpp
#include "Slider-potentiometer-easyC-SOLDERED.h"

// Declare the sensor object
sliderPot slider;

void setup()
{
    // Initialize the serial communication via UART
    Serial.begin(115200);

    // Initialize the sensor
    slider.begin();
}

void loop()
{
    Serial.print("Raw value of slider potentiometer: "); //Print information message
    Serial.println(slider.getValue()); //Prints raw value of slider potentiometer

    Serial.print("Minimum value of slider potentiometer: "); //Print information message
    Serial.println(slider.minValue()); //Prints minimum value of potentiometer

    Serial.print("Maximum value of slider potentiometer: "); //Print information message
    Serial.println(slider.maxValue()); //Prints maximum value of potentiometer

    Serial.print("Percent value of slider potentiometer: "); //Print information message
    Serial.println(slider.getPercentage()); //Prints percent value of slider potentiometer
    delay(1000);
    
}

```
<QuickLink 
  title="Read_value.ino" 
  description=" Most basic example of use."
  url="https://github.com/SolderedElectronics/Soldered-Slider-Potentiometer-with-easyC-Arduino-Library/blob/dev/examples/Read_value/Read_value.ino" 
/>
