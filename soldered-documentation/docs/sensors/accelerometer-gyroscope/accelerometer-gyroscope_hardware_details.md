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