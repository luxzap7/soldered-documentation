---
slug: /lsm6ds3tr/arduino/examples 
title: Measuring linear acceleration with LSM6DS3 Accelerometer (example)
id: lsm6ds3tr-arduino-2 
hide_title: False
---

This page contains some simple examples with function documentation on how to take measurements using the LSM6DS3 Accelerometer & Gyroscope.

---

## Initialization

To start working with the **Accelerometer & Gyroscope LSM6DS3 6-DOF Breakout**, you need to set up your Arduino environment. Firstly, include the required library, create the sensor object and initialize the sensor in the `setup()` function. You can use the return of `begin()` to check if everything is connected correctly:

```cpp
// Include libraries
#include "LSM6DS3-SOLDERED.h"
#include "Wire.h"

// Create an LSM6DS3 object
Soldered_LSM6DS3 myIMU; // Default address is 0x6B

void setup()
{
    // Initialize serial communication
    Serial.begin(115200);
    delay(1000); // Relax...

    // Initialize sensor
    if (!myIMU.begin())
    {
        // 'begin' returned false, there is an error
        Serial.println("Can't initialize LSM6DS3!");
        Serial.println("Check connection!");
        while (true)
            ;
    }

    Serial.println("LSM6DS3 initialized successfully.");
}
//...
```

<FunctionDocumentation
  functionName="!myIMU.begin()"
  description="Initializes the **LSM6DS3 Accelerometer & Gyroscope sensor**, setting up communication over I2C or SPI and configuring the sensor for operation. This function also verifies the presence of the sensor on the specified I2C address or SPI bus."
  returnDescription="**Returns `true`**: If initialization is successful, indicating that the sensor is properly connected and configured.
- **Returns `false`**: If initialization fails, indicating a connection issue or incorrect configuration."
  parameters={[]}
/>

## Configurating `setup()`

To start measuring velocity information we firstly need to setup the **serial monitor** and **configurate the IMU**.

```cpp
void setup()
{
    // Init serial communication
    Serial.begin(115200);
    delay(1000); // Relax...

    // Call .begin() to configure the IMU
    myIMU.begin();
}
```
<FunctionDocumentation
  functionName="myIMU.begin();"
  description=" responsible for initializing the LSM6DS3 Accelerometer & Gyroscope sensor"
  returnDescription="True: Initialization successful; the sensor is ready for use. False: Initialization failed; check wiring, power supply, or I2C address."
  parameters={[]}
/>

```cpp
    // Read acceleration and print it on serial
    Serial.print("ACCX:");
    Serial.print(myIMU.readFloatAccelX(), 4);
    Serial.print(",");
    Serial.print("ACCY:");
    Serial.print(myIMU.readFloatAccelY(), 4);
    Serial.print(",");
    Serial.print("ACCZ:");
    Serial.print(myIMU.readFloatAccelZ(), 4);
    Serial.print(",");
```