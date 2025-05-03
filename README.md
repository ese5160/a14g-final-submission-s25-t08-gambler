[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/AlBFWSQg)

# a14g-final-submission

* Team Number: 08
* Team Name: Gambler
* Team Members: Hao Tan, Tianyu Gao
* Github Repository URL: https://github.com/ese5160/a14g-final-submission-s25-t08-gambler
* Description of test hardware: SAMW25 Xpro dev board, DRV8833 motor driver, 28BYJ-48 stepper motor, DC motor, TCRT1000 reflective photo sensor, BH1750 light sensor, custom PCB based on SAMW25, SPI display, Windows 10 laptop

## 1. Video Presentation

[Video Link Coming Soon]

## 2. Project Summary

### Device Description

The Automated Card Dealer is an IoT-enabled device that distributes playing cards to multiple players with precision and consistency. It features a motorized card-dealing mechanism controlled via a mobile app or web interface, with support for various card games including standard dealing and blackjack modes.

### Inspiration

As avid card game players, we were inspired to create a solution that would eliminate human dealing errors and ensure fair card distribution in games. Traditional card dealing can be inconsistent, slow, and sometimes unfair, which our automated system solves while adding IoT capabilities for remote control and monitoring.

### Internet Connectivity

Our device uses WiFi connectivity to enable remote control through a Node-RED dashboard. Users can select the number of players, choose between distribution modes (normal or blackjack), and monitor the remaining cards in real-time through a web interface, making the card dealing experience more interactive and customizable.

## 3. Hardware & Software Requirements

### Device Functionality

Our card dealer is designed with a dual-motor system:

- A stepper motor (28BYJ-48) precisely positions the card output direction for multiple players, controlled through a DRV8833 motor driver
- A DC motor handles the card ejection mechanism, pushing one card at a time
- A TCRT1000 reflective photo sensor detects each card as it's dealt
- A BH1750 light sensor monitors the card tray to detect when cards are depleted
- A custom PCB based on the SAMW25 microcontroller provides WiFi connectivity

### System Block Diagram

```
    +---------------+      +----------------+
    |               |      |                |
    | Web Dashboard |<---->| MQTT Broker    |
    | (Node-RED)    |      |                |
    +---------------+      +----------------+
            ^                      ^
            |                      |
            v                      v
    +------------------------------------------+
    |                                          |
    |              SAMW25 MCU                  |
    |                                          |
    +------------------------------------------+
        ^         ^          ^           ^
        |         |          |           |
        v         v          v           v
    +------+  +--------+  +--------+  +--------+
    | Light |  | Photo  |  | Stepper|  |  DC    |
    | Sensor|  | Sensor |  | Motor  |  | Motor  |
    +------+  +--------+  +--------+  +--------+
```

## 4. Project Photos & Screenshots

[Screenshots/Photos Coming Soon]

## Codebase

- Embedded C firmware: https://github.com/ese5160/final-project-t08-gambler/tree/main/Application
- Node-RED dashboard code: https://github.com/ese5160/final-project-t08-gambler/tree/main/NodeRED
- Drivers for peripherals: https://github.com/ese5160/final-project-t08-gambler/tree/main/Diver%20codebase

## 5. Challenges

We faced several challenges during development:

- Precisely controlling the stepper motor timing to ensure cards were dealt to the correct positions
- Creating reliable card detection with the photo sensor that could handle different card types and lighting conditions
- Integrating the WiFi module with our MQTT system for reliable communication
- Power management to ensure stable operation from both battery and USB power sources

We overcame these challenges through extensive testing, refining our drivers, and implementing robust error-handling mechanisms. For the stepper motor control, we implemented proper sequencing and tunable delay parameters. For card detection, we calibrated the photo sensor with various threshold values and debouncing.

## 6. Prototype Learnings

Building this prototype taught us valuable lessons about designing interconnected systems that combine mechanical components with IoT capabilities. We learned the importance of power management in battery-operated devices and how to optimize code for reliable real-time operation on resource-constrained microcontrollers.

If building this device again, we would integrate motor drivers directly onto our custom PCB rather than using separate modules, which would reduce wiring complexity and improve reliability. We would also implement a more sophisticated user interface with a built-in display, reducing dependency on external devices.

## 7. Next Steps & Takeaways

Future improvements include:

- Adding card shuffling capabilities
- Implementing more game modes
- Creating a mobile app interface
- Reducing power consumption for longer battery life
- Improving the physical design for better card handling and aesthetics

Through ESE5160, we learned the full IoT development process from PCB design to embedded programming and cloud connectivity. We gained valuable skills in hardware-software integration, real-time systems design, wireless communication, and creating production-ready IoT devices with professional documentation.

## 8. Project Links

- Node-RED instance: [URL to be provided]
- Altium 365 PCBA: [URL to be provided]
