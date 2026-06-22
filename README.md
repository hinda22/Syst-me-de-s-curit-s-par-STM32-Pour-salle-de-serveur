# Systéme de sécurités par STM32 Pour salle de serveur
# STM32-Based Security System for Server Rooms

## Overview

This project presents an intelligent security system developed using the STM32 Nucleo-F446RE microcontroller. The system is designed to secure access to a server room through password authentication while also monitoring environmental temperature conditions.

The project combines access control, user interaction, alarm management, and temperature monitoring in a single embedded system.

## Features

### Access Control

* Password entry using a 4x4 matrix keypad.
* Verification of user credentials.
* Servo motor control to simulate door opening when the password is correct.
* Green LED indication for authorized access.

### Security Alarm

* Red LED visual alarm.
* Buzzer sound alarm for unauthorized access attempts.
* Alarm remains active until the STOP button is pressed.

### Password Management

* Secure password modification mode.
* Activated after three presses of the mode button.
* New password validation within a 5-second timeout.

### Temperature Monitoring

* Real-time temperature measurement using the DS18B20 sensor.
* Automatic indication of heating or cooling requirements.
* LCD display of system status and temperature-related messages.

### User Interface

* LCD 16x2 I2C display for messages and system information.
* Keypad interface for password entry.
* Buttons for password management and alarm reset.

---

## Hardware Components

| Component           | Function                   |
| ------------------- | -------------------------- |
| STM32 Nucleo-F446RE | Main controller            |
| LCD 16x2 I2C        | User display               |
| 4x4 Matrix Keypad   | Password input             |
| Servo Motor         | Door opening simulation    |
| Buzzer              | Sound alarm                |
| Green LED           | Access granted indicator   |
| Red LED             | Alarm indicator            |
| Orange LED          | Heating/Cooling indicator  |
| DS18B20 Sensor      | Temperature monitoring     |
| Mode Button         | Password change activation |
| Validation Button   | Password confirmation      |
| STOP Button         | Alarm reset                |

---

## Software Environment

* STM32CubeIDE
* STM32 HAL Library
* C Programming Language

### External Libraries

#### LCD Library

STM32_HAL_I2C_HD44780

Used to:

* Initialize LCD
* Display messages
* Control cursor position
* Clear display

#### Keypad Library

Keypad4x4 Library

Used to:

* Scan keypad rows and columns
* Detect key presses
* Manage password input

---

## System Workflow

1. User enters a password using the keypad.
2. The entered password is compared with the stored password.
3. If the password is correct:

   * Door opens using the servo motor.
   * Green LED turns on.
   * LCD displays an access granted message.
4. If the password is incorrect:

   * Red LED flashes.
   * Buzzer activates.
   * LCD displays an access denied message.
5. The alarm can be stopped using the STOP button.
6. Temperature is continuously monitored using the DS18B20 sensor.
7. Depending on temperature thresholds:

   * Cooling mode is activated.
   * Heating mode is activated.
   * Status is displayed on the LCD.

---

## Password Change Procedure

1. Press the Mode button three times.
2. Enter the new password using the keypad.
3. Press the Validation button.
4. The new password must be confirmed within 5 seconds.
5. If validation is successful, the password is updated in RAM and a confirmation message is displayed.

---

## Project Structure

```text
Core/
│
├── main.c
├── gpio.c
├── i2c.c
├── tim.c
├── usart.c
├── stm32f4xx_it.c
│
├── liquidcrystal_i2c.c
├── liquidcrystal_i2c.h
│
├── keypad.c
└── keypad.h
```

---

## Future Improvements

 Store passwords in Flash memory instead of RAM.
 Add GSM notifications for security alerts.
 Integrate cloud connectivity for remote monitoring.
 Add a flame or smoke sensor for fire detection.
 Develop a web dashboard for real-time supervision.

---


 Hind Saada


Faculty of Sciences of Bizerte (FSB)
University of Carthage
Academic Year 2024–2025
