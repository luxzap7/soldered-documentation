---
slug: /lsm6ds3tr/arduino/examples 
title: Measuring linear acceleration with LSM6DS3 Gyroscope (example)
id: lsm6ds3tr-arduino-3 
hide_title: False
---

This page contains some simple examples with function documentation on how to take measurements using the LSM6DS3 Accelerometer & Gyroscope.

---

## Initialization

To start working with the **Accelerometer & Gyroscope LSM6DS3 6-DOF Breakout**, you need to set up your Arduino environment. Firstly, include the required library, create the sensor object and initialize the sensor in the `setup()` function. You can use the return of `begin()` to check if everything is connected correctly:

