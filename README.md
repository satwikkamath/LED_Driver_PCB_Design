# LED Driver PCB Design

## Overview

This project involves designing a PCB to drive four high-power LEDs using the CAT4104 LED driver IC. The PCB supports PWM dimming control provided by an ESP32 microcontroller and is powered by a 28V supply.

## Features

- **4 Channels**: Each channel drives one LED.
- **PWM Control**: Dim the LEDs using a single PWM signal from the ESP32.
- **Current Regulation**: Adjustable current setting for consistent LED brightness.
- **High-Voltage Operation**: Designed to operate with a 28V power supply.
- **Compact Design**: Optimized PCB layout for efficient space utilization.

## Components

### 1. **CAT4104 LED Driver IC**

- **Description**: The CAT4104 is a 4-channel LED driver IC with built-in PWM control. It regulates the current through each LED to ensure consistent brightness and supports PWM dimming for adjusting the LED intensity.
- **Pins**:
  - **LED1, LED2, LED3, LED4**: Connect to the anodes of the LEDs.
  - **RSET**: Sets the current through the LEDs. Connect a resistor here to configure the desired current.
  - **VIN**: Connect to the 28V power supply.
  - **EN/PWM**: Connect to the PWM output from the ESP32 for controlling LED brightness.
  - **GND**: Connect to the ground plane.

### 2. **LM2596 Buck Converter**

- **Description**: The LM2596 is a step-down (buck) voltage regulator that converts the 28V input voltage to 5V. This 5V output powers the ESP32 and other 5V components.
- **Pins**:
  - **VIN**: Connect to the 28V power supply.
  - **GND**: Connect to the ground plane.
  - **VOUT**: Provides the regulated 5V output.
  - **ADJ**: Used to set the output voltage with a feedback resistor network.
  - **ON/OFF**: Used to enable or disable the regulator.

### 3. **ESP32 C3**

- **Description**: The ESP32 C3 is a microcontroller with Wi-Fi and Bluetooth capabilities. In this project, it provides the PWM signal required for dimming the LEDs.
- **Pins**:
  - **PWM Output**: Connect to the EN/PWM pin of the CAT4104.

### 4. **USB Mini Connector**

- **Description**: The USB Mini connector allows for power and data connection to external devices. In this design, it provides a way to connect the PCB to a USB power source or for debugging and programming purposes.
- **Pins**:
  - **VBUS**: Connects to the 5V power supply.
  - **D+**: Data line positive.
  - **D-**: Data line negative.
  - **GND**: Connects to the ground plane.

### 5. **CP2102 USB to UART Converter**

- **Description**: The CP2102 USB to UART converter, enables communication between the microcontroller (ESP32) and a computer via USB. It converts USB signals to UART (serial) signals for programming and debugging.
- **Pins**:
  - **TX**: Transmit data from the converter to the ESP32.
  - **RX**: Receive data from the ESP32 to the converter.
  - **GND**: Connects to the ground plane.
  - **VCC**: Provides 3.3V or 5V power to the ESP32 if needed.

### 6. **Passive Components**

- **Capacitors**:
  - **10µF, 50V Capacitor**: Used on the VIN pin of the CAT4104 to filter out noise.
  - **0.1µF Capacitor**: Used for decoupling on the CAT4104's VCC pin to stabilize the internal regulator.
- **Resistors**:
  - **Current Setting Resistor (RSET)**: Determines the current through the LEDs.

## Schematic

The schematic of the circuit includes:

- **Power Supply**: 28V input connected to the VIN pin of the LM2596 and CAT4104.
- **Current Setting**: Resistor connected to the RSET pin of the CAT4104 to set the LED current.
- **PWM Input**: Connected to the EN/PWM pin of the CAT4104 from the ESP32.
- **LED Channels**: Connected to the anodes of the LEDs.
- **Ground Connections**: All components share a common ground plane.

## Documentation

- **CAT4104 Datasheet**: [Link to datasheet](https://www.onsemi.com/pub/Collateral/CAT4104-D.PDF)
- **LM2596 Datasheet**: [Link to datasheet](https://www.ti.com/lit/ds/symlink/lm2596.pdf)
- **ESP32 C3 Datasheet**: [Link to datasheet](https://www.espressif.com/en/support/download/documents?category=esp32&field=esp32-c3)
- **USB Mini Connector**: [Typical Pinout Information](https://en.wikipedia.org/wiki/USB#Mini-USB)
- **USB to UART Converter**: [CP2102 Datasheet](https://www.silabs.com/documents/public/data-sheets/cp2102.pdf)
