---
slug: /lsm6ds3tr/how-it-works 
title: How it works
id: lsm6ds3tr-how-it-works 
hide_title: False
---  

The LSM6DS3 is a system in a package that combines a 3D digital accelerometer and a 3D digital gyroscope, allowing linear acceleration and rotational motion to be tracked in three dimensions.

<CenteredImage src="/img/lsm6ds3tr/LSM6DS36_onboard.png" alt="LSM6DS3 chip on the board" caption="LSM6DS3 chip on the board" width="400px" />
---

## Datasheet

For an in-depth look at technical specifications, refer to the official LSM6DS3 6-DOF Datasheet:  

<QuickLink  
  title="LSM6DS3 6-DOF Datasheet"  
  description="Detailed technical documentation for the LSM6DS3 6-DOF Accelerometer & Gyroscope"  
  url="https://soldered.com/productdata/2023/08/Soldered_LSM6DS3_datasheet.pdf"  
/>  

---

## How the accelerometer works  

The **accelerometer** on this board works by reading the movement of its mass where its **movement coused by external force** input is then **transformed into readable input** that is transfered into data. It all works by containing a **tiny proof mass attached to a spring** within its casing. When acceleration occurs, the proof mass moves relative to the casing due to inertia, causing the spring to compress or stretch. This movement is **detected by capacitive or piezoresistive sensors**, which convert the **mechanical displacement into electrical signals**. These signals are then processed and amplified by onboard electronics to provide precise measurements of acceleration, supporting full-scale ranges from **±2 g to ±16 g**.  

<CenteredImage src="/img/lsm6ds3tr/accelerometer.png" alt="SHTC3 sensor on board" caption="Visual representation of the accelerometer" width="400px" />

---

## How the gyroscope works  

The **gyroscope** on this board works in a simular matter to the accelerometer with a simple difference that it works by **contain tiny vibrating structures** that move due to the **Coriolis force** when **rotation occurs**. This movement is detected by **capacitive or piezoresistive sensors**, which **convert the mechanical displacement** into **electrical signals**. These signals are then processed and amplified by onboard electronics to provide precise measurements of angular rate, supporting full-scale ranges from **±125 dps to ±2000 dps**. The gyroscope's operation is based on **MEMS technology**, ensuring high precision and low power consumption, making it suitable for applications such as drone stabilization and robotics. The gyroscope's design allows for efficient data management and low power modes, ensuring optimal performance without significant energy consumption.

<CenteredImage src="/img/lsm6ds3tr/gyroscope.png" alt="SHTC3 sensor on board" caption="Visual representation of the gyroscope" width="400px" />

---

## I2C communication  

The SHTC3 uses the I2C protocol to communicate with a microcontroller. It operates with a fixed I2C address of **0x6A** and supports fast mode (400 kHz) for rapid data transmission.  

Upon request, the sensor responds with two 16-bit values—one for humidity and one for temperature—along with a CRC checksum for data integrity.  

---

## Measurement process  

1. **Power-up and initialization**  
   - LSM6DS3 enters a low-power mode when powered on  
   - On initialization send a command to initialize the sensor. This typically involves setting the desired measurement ranges for the accelerometer and gyroscope, as well as configuring any additional features like FIFO buffering or interrupt settings..  

2. **Taking a measurement**  
   - Send a command to start the measurement process. 
   - The sensor captures data for linear acceleration and angular rate. The measurement process is typically continuous once started, with data being stored in the FIFO buffer if configured.

3. **Data retrieval**  
   - Use I2C or SPI to read the latest data from the sensor. This involves sending a read command to the sensor's address and retrieving the stored data. 
   - The sensor outputs raw data for acceleration and angular velocity, which may need to be converted into meaningful units (e.g., g for acceleration, dps for angular rate) using the sensitivity values provided in the datasheet.
4. **Additional Steps**  
   - If the FIFO buffer is used, manage its contents by reading data regularly to prevent overflow or use interrupts to signal when new data is available.
   - Process the retrieved data to extract meaningful information such as orientation, motion patterns, or other desired metrics.