# 2-Wheel Self-Balancing Robot (ESP32-S3 + STM32F411)

A modular hardware PCB design and embedded software repository for a 2-wheel self-balancing robot. This project serves as a practical setup for multi-sheet schematic capture, PCB layout in KiCad 10, and firmware development for STM32 and ESP32-S3 microcontrollers.

## 🛠 Hardware Overview

- **Main MCU (Motor Control & Sensors):** STM32F411CEU6 (WeAct Black Pill)
- **Co-MCU (Display & Wireless/Vision):** ESP32-S3 WROOM CAM
- **Power Supply:** 2S Li-ion Battery pack (7.4V – 8.4V) with 2S BMS protection
- **Buck Regulators:**
  - **MP1584EN:** 3.3V Step-down regulator for system logic
  - **LM2596 - will be changed:** 6.0V Step-down regulator for motors and peripheral loads
- **Motor Driver:** DRV8833 dual H-bridge module for DC motors with quadrature encoders
- **Sensors (Shared I2C Bus):** 
  - **MPU6050:** 6-axis IMU (Accelerometer + Gyroscope)
  - **INA219:** High-side DC current and voltage monitor
- **Lighting:** Cree XM-L2 / XHP50 High-Power LED (Controlled via N-Channel MOSFET AO3400A)

## 📌 Hardware Pin Mapping & Interfaces

- **I2C2 (PB10 / PB3):** Shared I2C bus connecting MPU6050 and INA219 to STM32
- **USART1 (PA9 / PA10):** Hardware UART interface between STM32 and ESP32-S3
- **TIM3 / TIM4:** Hardware timer channels configured for dual-motor quadrature encoder input

## 📂 Project Structure

- `small project.kicad_pro`: KiCad 10 main project configuration
- `stm32.kicad_sch`: STM32 microcontroller and motor control schematic sheet
- `esp32.kicad_sch`: ESP32-S3 co-processor and OLED display schematic sheet
- `bms_batt.kicad_sch`: Battery management system and power distribution sheet
- `small project.kicad_pcb`: PCB layout file
- `lib/`: Custom footprint, symbol, and 3D block libraries
