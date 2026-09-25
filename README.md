# Actuator-26

A small ESP8266-based WiFi robot car project that creates its own access point and exposes a simple web interface for controlling motor movement.

This repository contains a single Arduino/ESP8266 sketch (`main.cpp`) that:

- starts an access point on the ESP8266
- hosts a small webpage with directional control buttons
- drives two DC motors for forward, reverse, left, right, and stop motion
- uses PWM to control motor speed

## Features

- WiFi access point mode (`MY_BOT_AP`)
- Browser-based remote control interface
- Forward / backward / left / right / stop movement controls
- Motor speed fixed at 100 for both sides
- ESP8266 compatible and designed for Arduino IDE

## Hardware Overview

This project is meant for a basic two-wheel robot chassis with:

- ESP8266 development board (for example, NodeMCU)
- 2 DC motors
- motor driver or H-bridge circuit
- power supply for the motors and ESP8266

## Pin Mapping

The sketch uses the following GPIO assignments:

| Function | ESP8266 Pin |
| --- | --- |
| Left motor input 1 | D4 |
| Left motor input 2 | D5 |
| Right motor input 1 | D6 |
| Right motor input 2 | D7 |
| Left motor PWM | D1 |
| Right motor PWM | D2 |

## Project Structure

- `main.cpp` — complete robot control program

## How it Works

When the ESP8266 boots:

1. It switches to access point mode.
2. It creates the WiFi network `MY_BOT_AP` with password `12345678`.
3. It starts a small web server on port 80.
4. The root page contains buttons for movement commands.
5. Each button triggers an HTTP endpoint such as `/forward`, `/backward`, `/left`, `/right`, and `/stop`.
6. The handler sets the motor pins to move the robot in the selected direction.

## Setup Instructions

1. Install the ESP8266 board support package in Arduino IDE.
2. Open `main.cpp` in the Arduino IDE.
3. Select your ESP8266 board and correct serial port.
4. Connect the motor driver and motors to the pins listed above.
5. Upload the sketch to the ESP8266.
6. Power the board and connect your phone or computer to the WiFi network:
   - SSID: `MY_BOT_AP`
   - Password: `12345678`
7. Open the following address in a browser:
   - `http://192.168.4.1`

## Control Interface

The webpage includes buttons for:

- Forward
- Backward
- Left
- Right
- Stop

## Important Notes

- The default WiFi SSID and password are hardcoded in the code and should be changed before using this project in a real environment.
- Motor speed is currently fixed at `100` for both wheels.
- The project is intended as a simple prototype and can be expanded for sensors, autonomous control, or a more polished web UI.

## Example Usage

After connecting to the robot's access point, visit the IP address shown in the serial monitor and use the web buttons to manually drive the chassis.

## License

No explicit license has been provided in this repository. If you plan to reuse or distribute the code, check whether a license is required by the original author.
