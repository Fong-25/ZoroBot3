# ZoroBot3 — Technical Documentation

> High-performance Micromouse robot featuring an STM32F4, high-resolution magnetic encoders, a suction fan, and four infrared sensors.

![ZoroBot3](assets/imgs/ZoroBot3_rev2_finish_3.jpg "ZoroBot3")

---

## 🏆 Achievements

| 🥇 | 🥈 | 🥉 |
|:--:|:--:|:--:|
| **8** | **0** | **0** |

### Competition Results

| Event | Category | Placement | Year |
|--------|-----------|:--------:|:---:|
| <img src="assets/imgs/portugal-flag-xs.png" style="height:16px" alt="🇵🇹"/> **Micromouse Portuguese Contest** | Micromouse Classic | 🥇 | 2026 |
| <img src="assets/imgs/romania-flag-xs.png" style="height:16px" alt="🇷🇴"/> **RoboChallenge** | Maze | 🥇 | 2025 |
| <img src="assets/imgs/spain-flag-xs.png" style="height:16px" alt="🇪🇸"/> **OSHWDem** | Micromouse Classic | 🥇 | 2025 |
| <img src="assets/imgs/portugal-flag-xs.png" style="height:16px" alt="🇵🇹"/> **Micromouse Portuguese Contest** | Micromouse Classic | 🥇 | 2025 |
| <img src="assets/imgs/portugal-flag-xs.png" style="height:16px" alt="🇵🇹"/> **Micromouse Portuguese Contest** | Time Trial | 🥇 | 2025 |
| <img src="assets/imgs/romania-flag-xs.png" style="height:16px" alt="🇷🇴"/> **RoboChallenge** | Maze | 🥇 | 2024 |
| <img src="assets/imgs/spain-flag-xs.png" style="height:16px" alt="🇪🇸"/> **OSHWDem** | Micromouse Classic | 🥇 | 2024 |
| <img src="assets/imgs/spain-flag-xs.png" style="height:16px" alt="🇪🇸"/> **OSHWDem** | Micromouse Wall-Follower | 🥇 | 2023 |

---

## ⚙️ Hardware

- **Microcontroller**: STM32F405RGT6 @ 168 MHz
- **Motor driver**: MP6551 @ 20 kHz
- **Gyroscope**: LSM6DSRTR, 4000 dps
- **Encoders**: AS5145B-HSST (12-bit, hardware quadrature decoding)
- **Regulator**: CN3903 + LDO ME611C33M5G
- **IR sensors**: 4× SFH-4550 emitters + 4× ST-1KL3A receivers + TSSP77038TR (38 kHz)
- **Battery**: Turnigy nano-tech LiPo 2S, 260 mAh, 35–70C
- **Drive system**: 2× 8520 7.4 V coreless motors, PCB chassis, Kyosho tires

![Chassis](assets/imgs/ZoroBot3_rev2_3d_model.png "ZoroBot3 - Chassis")

---

## 💻 Software

- Developed in **C11** using VSCode, PlatformIO, and **LibOpenCM3**.
- Analog values are read using **DMA** and processed every **1 ms**.
- IR sensors are managed by a **16 kHz state machine** with ambient-light filtering.
- Encoders use **hardware quadrature decoding** via timers; the IMU communicates over **SPI**.
- **Seven cascaded PID loops** (linear speed, angular speed, front-wall, and side-wall control) run every 1 ms.
- Position is reset when a side wall is lost.
- Turns use **sinusoidal acceleration** profiles.
- Algorithms include wall following, exploration, **kinematically weighted FloodFill**, and hardcoded movement sequences.

---

## 📚 Detailed Documentation

- **[Hardware](01-hardware.md)** — MCU, sensors, motors, encoders, battery, chassis, and robot revisions
- **[Software Architecture](02-software-architecture.md)** — Main loop, SysTick ISR, race flow, and exploration
- **[Sensors](03-sensors.md)** — ADC state machine, linearization, wall detection, and hysteresis
- **[Movement](04-movement.md)** — Movement types, turn profiles, speed runs, and wall-loss correction
- **[Floodfill](05-floodfill.md)** — BASIC/DIAGONAL/TIME_BASED algorithms, BFS, and path following
- **[PID Control](06-control-system.md)** — Seven cascaded loops, anti-windup, and battery compensation
- **[Menu](07-menu-system.md)** — Navigation, algorithm selection, and speed configuration
- **[Debugging](08-debug-system.md)** — LEDs, RGB, USART, and debug functions
- **[Calibration](09-calibration.md)** — Front/side sensor calibration, gyroscope, and EEPROM persistence
- **[Scripts: Sensor Calibration](10-scripts-sensors.md)** — Jupyter tool for IR linearization profiles and magics
- **[EEPROM](11-eeprom.md)** — Storage, checksum, and persistent maze data
- **[Encoders and Gyroscope](12-encoders-gyro.md)** — AS5145B-HSST, LSM6DSR, and angular integration
- **[Battery and LEDs](13-battery-leds.md)** — Voltage monitoring, voltage divider, and status LEDs
- **[MMSIM Simulator](14-simulator.md)** — Virtual-wall API and time estimation
- **[Kinematics](15-kinematics.md)** — Speed strategies, acceleration profiles, and turn parameters
- **[Scripts: Turn Profiles](16-scripts-turn-profiles.md)** — Offline generation of sinusoidal turn profiles
- **[Known Issues](17-known-issues.md)** — Documented issues, their impact, and proposed solutions

---

## 🔧 Technology Stack

| Component | Details |
|-----------|---------|
| **MCU** | STM32F405RGT6 @ 168 MHz (ARM Cortex-M4F) |
| **Framework** | LibOpenCM3 + PlatformIO |
| **Language** | C11 |
| **Compiler** | GCC ARM Embedded (arm-none-eabi-gcc) |
| **IDE** | VSCode |
| **Version control** | Git |

---

## 🎥 Videos

### Micromouse Portuguese Contest 2026 — 🥇
<video src="https://github.com/user-attachments/assets/5a7cf803-e31e-463a-afa9-e5784b378937" width="50%" controls></video>

### OSHWDem 2025 — 🥇
<video src="https://github.com/user-attachments/assets/332fd117-6600-4692-b59f-4b1154166f3f" width="50%" controls></video>

### Micromouse Portuguese Contest 2025 — 🥇
<video src="https://github.com/user-attachments/assets/cf21e942-3fe0-4065-8892-fa3d181a9791" width="50%" controls></video>

### RoboChallenge 2024 — 🥇
<video src="https://github.com/user-attachments/assets/a8c53e97-a756-4934-9c83-6c93fda1b235" width="50%" controls></video>

### OSHWDem 2024 — 🥇
<video src="https://github.com/user-attachments/assets/a70629e6-34b6-473f-afb0-14d8290bd128" width="50%" controls></video>
