# Smart Car System with Arduino

## Project Overview

The Smart Car System is designed to enhance safety and monitor various aspects of a car using Arduino and sensors. It provides alerts for the following scenarios:

1. **Driver Seat Sensor:** Warns if the motor is on and the driver is in place without wearing a safety belt.
2. **Car Light Sensor:** Provides an alert if the car's light is on but the bulb is not working.
3. **Wheel Sensor:** Alerts if the car is on and the air pressure inside a tire is too low.
4. **Reverse Mode Sensor:** Works when the car is in reverse, and it's connected to a voice system for obstacle distance alerts.

The system uses LCDs to display car status, LEDs for problem indication, and an alarm (buzzer) during reverse mode.

## Components

Here are the key components used in this project:

- Arduino board
- Driver seat sensor
- Car light sensor
- Wheel sensor
- Reverse mode sensor
- Voice system (for obstacle distance alerts)
- LCDs
- LEDs
- Buzzer!
- Wiring and connection components
![Screenshot 2023-10-13 at 16 00 36](https://github.com/sara-totah/smartCarSystem/assets/62484242/c14db573-fc99-48cb-ba93-f87c6bdf5e5e)

## Setup Instructions


1. **Hardware Setup:** Connect the sensors and components as per your project design. Ensure proper wiring and connections.

2. **Arduino IDE:** Upload the Arduino code provided for this project to your Arduino board using the Arduino IDE.

3. **Power Supply:** Ensure your Arduino board has a power supply, typically via USB or an external power source, as required.

4. **Testing:** Test each sensor by simulating different scenarios to ensure the system functions as intended.

## Usage

- When you turn on your car, the system will monitor and display the status on the LCDs.
- If there's an issue with the driver seat, car light, or wheel, LEDs will indicate the problem.
- During reverse mode, the buzzer will provide alerts, and the reverse mode sensor will trigger the voice system based on obstacle distance.

## Additional Notes

- Make sure you have a clear understanding of the sensor wiring and how the Arduino code works.
- You may need to calibrate or adjust sensors for accurate readings.
- If the project involves a specific physical setup, consider including pictures or diagrams to help users understand how to set up the components correctly.


This README provides a brief overview of the Smart Car System project, its components, setup instructions, and usage. Depending on your course requirements, you may need to include pictures or diagrams to illustrate the hardware setup, but it's not always necessary.
