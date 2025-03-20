---
slug: /accelerometer-gyroscope/hardware 
title: Hardware details
id: accelerometer-gyroscope-hardware 
hide_title: False
---
## Pinout

<ErrorBox>The pinout image for this board hasn't been generated yet! We're working on it!</ErrorBox>

## Pin details

| Pin Marking | Pin Name | Description                                     |
| ----------- | -------- | ----------------------------------------------- |
| **VCC**     | Power    | Supply voltage (both 5V and 3V3 are supported). |
| **GND**     | Ground   | Common ground for power and signals.            |
| **SDA**     | Data     | I2C data line for communication.                |
| **SCL**     | Clock    | I2C clock line for communication.               |
| **INT1**    | Interrupt| Programmable interrupt 1                        |
| **INT2**    | Interrupt| Programmable interrupt 2                        |

<InfoBox>This breakout board operates on supply voltages of 2.5V to 3.6V making it work with both 3.3V and 5V systems.</InfoBox>

---

## Qwiic (formerly easyC)  

<CenteredImage src="/img/easyc_transparent.png" alt="EasyC/qwiic cable" width="550px" />
 
<InfoBox> This board is fully **Qwiic-compatible**! Just plug it into your board using a **Qwiic/easyC/STEMMA QT cable** and start coding! </InfoBox>

<QuickLink 
  title="Qwiic (formerly easyC) details and specifications" 
  description="Learn about hardware specifications, compatibility, and usage of the Qwiic connector." 
  url="/qwiic" 
/>

---

## Power consumption

The LSM6DS3 is designed for low-power operation, making it ideal for IoT and battery-powered applications.  

| Mode                  | Current Consumption |
| ----------------      | ------------------- |
| Normal mode           | ~0.9 mA             |
| High-performance mode | ~1.6 mA             | 

---

## Dimensions

- **Board Dimensions:** 2.5 mm × 3 mm x 0.83 mm  (0.09 x 0.11 x 0.03 inch)
- **Header Pin Holes:** 1.5 mm  
- **Screw Holes:** Designed for M3 screws (3.2 mm diameter)  
- Soldered boards are LEGO compatible! 🧱 

---

## Jumper Details

This board contains hardware jumpers, see below for their locations and functions:

<FlickityCarousel
  images={[
    { src: '/img/accelerometer-gyroscope/LSM6DS36_jp1.png', alt: 'LSM6DS3 jumper 1', caption: 'JP1' },
    { src: '/img/shtc3/shtc3_jp2.png', alt: 'SHTC3 jumper 2', caption: 'JP2' },
    { src: '/img/shtc3/shtc3_jp3.png', alt: 'SHTC3 jumper 3', caption: 'JP3' },
    { src: '/img/shtc3/shtc3_jp4.png', alt: 'SHTC3 jumper 4', caption: 'JP4' },
  ]}
  jumpers={true}
/>

| Jumper  | Default State            | Function                                                                                                      |
| ------- | ------------------------ | ------------------------------------------------------------------------------------------------------------- |
| **JP1** | **NC** (Normally closed) | Connects **SDA/SCL pull-up resistors to 5V** for I2C communication.                                           |
| **JP2** | **NC** (Normally closed) | Connects **SDA/SCL pull-up resistors to 3.3V** for I2C communication.                                         |
| **JP3** | **NC** (Normally closed) | When connected, the **voltage regulator is powered by 5V**, stepping it down to **3.3V for the IC**.          |
| **JP4** | **NO** (Normally open)   | When shorted, it **bypasses the voltage regulator**, allowing the board to be powered **directly from 3.3V** via headers. **Ensure JP3 is disconnected if JP4 is connected.** |

---