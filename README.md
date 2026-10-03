# Autonomous Combat Robotics Platform & H-Bridge Motor Controller

[![Award](https://img.shields.io/badge/Competition-Robot%20Wars%202nd%20Place-silver?style=for-the-badge&logo=target)](https://www.harry-rogers.com)
[![Grade](https://img.shields.io/badge/Module%20Grade-82%25%20(A%2B)-success?style=for-the-badge)](https://www.harry-rogers.com)
[![Platform](https://img.shields.io/badge/Platform-Microchip%20PIC%20%7C%20MPLAB%20XC8-red?style=for-the-badge&logo=microchip)](https://www.microchip.com)
[![EDA](https://img.shields.io/badge/EDA-Proteus%20Design%20Suite-blue?style=for-the-badge)](https://www.labcenter.com)

> Hardware schematics, PCB layouts, and embedded C firmware for the **University of Brighton Robot Wars Competition**, achieving a **2nd Place Overall Podium Finish** in the inter-collegiate arena combat tournament. Combines dual high-current DC motor H-bridge drivers, ultrasonic obstacle tracking, stepper actuation, and an onboard HD44780 status display.

---

### 📜 Academic Integrity & Attribution Disclosure
- **Team Project Context & Individual Contributions:** Developed as part of the collegiate Robot Wars competition team during undergraduate engineering studies. Harry Rogers served as lead systems and firmware engineer, authoring the embedded C motor driver routines, ultrasonic sonar capture interrupts, and Proteus simulation schematics.
- **Distinct Project Scope:** This combat platform was engineered specifically for the Robot Wars arena tournament, distinct from the autonomous corridor-navigating sensor buggy and separate from the low-level MPASM assembly library.
- **Third-Party & Vendor IP:** Compiler runtime and device peripheral registers are copyright **Microchip Technology Inc.** Simulation models and EDA schematic libraries utilize standard components from **Labcenter Electronics Proteus Design Suite**.

---

## 🏆 Key Achievements

- **2nd Place Podium Finish** in the University of Brighton Robot Wars Tournament.
- **82% Distinction Grade (A+)** in XE521 Engineering Design.
- **Dual Motor Differential Drive:** High-torque H-bridge motor driver schematic designed and verified in **Labcenter Proteus Design Suite** (`schematics_proteus/`).
- **Real-Time Sonar Ranging:** Ultrasonic sensor (HC-SR04) echo capture routines executed via hardware timer interrupts for target detection and wall evasion.
- **Embedded C Firmware:** Modular XC8 C architecture for pulse width modulation, differential steering, and auxiliary weapon actuation.

---

## 🏗️ Hardware Architecture

```mermaid
flowchart TD
    subgraph Sensors ["Sensory Array"]
        SONAR["HC-SR04 Ultrasonic Sonar\n(Target Acquisition & Range Timing)"]
    end

    subgraph MCU ["PIC Microcontroller (Firmware: MPLAB XC8)"]
        TIMER["Timer Capture Engine\n(Echo Pulse Measurement)"]
        FSM["Combat Navigation FSM\n(SEARCH -> ENGAGE -> EVADE)"]
        PWM_OUT["PWM Motor Pulse Generator"]
        LCD_DRV["HD44780 LCD Controller"]
    end

    subgraph Actuation ["Power & Drive Electronics"]
        H_BRIDGE["Dual H-Bridge Motor Driver\n(High-Current MOSFET Topology)"]
        MOTORS["High-Torque DC Drive Motors\n(Differential Tank Steering)"]
        STEPPER["Stepper Weapon Actuator"]
    end

    SONAR -->|Echo Pulse| TIMER
    TIMER --> FSM
    FSM --> PWM_OUT --> H_BRIDGE --> MOTORS
    FSM --> STEPPER
    FSM --> LCD_DRV
```

---

## 📂 Repository Contents

```
robot-wars-combat-platform/
├── schematics_proteus/
│   ├── Motor Controller.pdsprj     # Primary Proteus PCB schematic & simulation
│   ├── MotorController.pdsprj      # H-bridge MOSFET driver board design
│   └── MotorController1.pdsprj     # Power distribution & filtering layout
└── firmware_xc8/
    ├── drive_controller/
    │   ├── MovementCode.c          # Dual-wheel differential drive & speed control
    │   └── lcd.c                   # HD44780 character LCD diagnostic interface
    ├── ultrasonic_sonar/
    │   └── ultrasonic_driver.c     # Precision timer-based HC-SR04 sonar driver
    └── stepper_weapon/
        └── newmain.c               # Actuator step-sequencing and weapon trigger
```

---

## 🛠️ Build & Simulation Guide

### Circuit Simulation in Proteus
1. Open **Labcenter Proteus 8 Professional**.
2. Load `schematics_proteus/Motor Controller.pdsprj`.
3. Press **Play** in the VSM simulation panel to test logic levels, gate drive waveforms, and motor direction controls.

### Firmware Compilation in MPLAB X
1. Open **Microchip MPLAB X IDE**.
2. Open the project targeting the PIC microcontroller.
3. Select **XC8** C compiler.
4. Build the solution and flash via PICkit or simulate in Proteus with the generated `.hex` artifact.

---

## 🎓 Academic Attribution

- **Author:** Harry Rogers
- **Degree:** BEng (Hons) Electronic & Computer Engineering (First-Class Honours)
- **Institution:** University of Brighton
- **Module:** XE521 - Engineering Design & EO524 - Embedded Systems
- **Distinction:** Robot Wars 2nd Place Prize
- **Portfolio:** [www.harry-rogers.com](https://www.harry-rogers.com)

---

## 📄 License
This repository is licensed under the MIT License.
