---
slug: /125khzrfidtagreader/how-it-works 
title: How it works
id: 125khzrfidtagreader-how-it-works 
hide_title: False
---  

The **125kHz RFID Tag Reader Board** is a compact and efficient module designed for reading RFID tags operating at 125kHz. It is ideal for applications such as access control, personal identification, security systems, and interactive projects. It operates using its **ATTINY1604-SSNR chip** to read cards.

<CenteredImage src="/img/125khzrfidtagreader/RFID_chip.jpg" alt="ATTINY1604-SSNR chip on the board" caption="ATTINY1604-SSNR chip on the board" width="400px" /> 

---

## How the RFID reader works  

The **RFID reader** operates by detecting the presence of a compatible 125kHz tag near its antenna. The tag receives power wirelessly through electromagnetic waves emitted by the reader's antenna. Once powered, the tag transmits its unique code back to the RFID reader. This code is then decoded and sent to a microcontroller via UART communication.

The module supports a reading distance of **2–5 cm**, ensuring reliable performance in close-range applications. It uses **125kHz-compatible read-only or read/write tags**, making it suitable for various identification and control systems.


<CenteredImage src="/img/125khzrfidtagreader/RFID_info.png" alt="Basic RFID principle" caption="VBasic RFID principle" width="400px" />

---

## I2C communication  

The **LSM9DS1TR** uses the **I2C protocol** to communicate with a microcontroller, supporting both standard and fast modes (**100 kHz** and **400 kHz**) for efficient data transmission. The sensor has multiple I2C addresses depending on the state of the **SDO_A/G (SDO-A)** and **SDO_M pins**, which determine the addresses for the accelerometer/gyroscope and magnetometer, respectively. 

#### The typical I2C addresses are:
+ Accelerometer and Gyroscope: **0x6A** or **0x6B** depending on the SDO_A/G pin state.
+ Magnetometer: **0x1C** or **0x1E** depending on the SDO_M pin state.

These addresses can be configured by adjusting the logic levels on the **SDO_A/G** and **SDO_M** pins, allowing flexibility in I2C bus management. For **multiple LSM9DS1** devices on the **same I2C bus**, an **I2C multiplexer** can be used to manage different addresses and prevent conflicts.

---

## Measurement process  

1.  **Power-up and Initialization**
    
    *   LSM9DS1 enters a low-power mode when powered on.  
    *   On initialization, send a command to initialize the sensor. This typically involves setting the desired measurement ranges for the accelerometer, gyroscope, and magnetometer, as well as configuring any additional features like FIFO buffering or interrupt settings.
        
2.  **Taking a Measurement**
    
    *   Send a command to start the measurement process.   
    *   The sensor captures data for linear acceleration, angular rate, and magnetic field strength. The measurement process is typically continuous once started, with data being stored in the FIFO buffer if configured.
        
3.  **Data Retrieval**
    
    *   Use I2C or SPI to read the latest data from the sensor. This involves sending a read command to the sensor's address and retrieving the stored data.    
    *   The sensor outputs raw data for acceleration, angular velocity, and magnetic field strength, which may need to be converted into meaningful units (e.g., g for acceleration, dps for angular rate, gauss for magnetic field) using the sensitivity values provided in the datasheet.
        
4.  **Additional Steps**
    
    *   If the FIFO buffer is used, manage its contents by reading data regularly to prevent overflow or use interrupts to signal when new data is available.    
    *   Process the retrieved data to extract meaningful information such as orientation, motion patterns, magnetic field direction, or other desired metrics. This can involve combining data from all three sensors to achieve accurate navigation or gesture recognition capabilities.