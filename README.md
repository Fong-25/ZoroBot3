# ZoroBot3

The third version of our first robot: a high-performance Micromouse featuring an STM32F4, high-resolution magnetic encoders, a suction fan, and plenty of cool LEDs.

![ZoroBot3](./images/ZoroBot3_rev2_finish_3.jpg "ZoroBot3")

## 🏆 Achievements

| 🥇 | 🥈 | 🥉 |
|:--:|:--:|:--:|
| **8** | **0** | **0** |

### Competition Results

| Event | Category | Placement | Year |
|--------|-----------|:--------:|:---:|
| <img src="./images/flags/portugal-flag-xs.png" height="16px" title="Portugal" alt="🇵🇹"/> **Micromouse Portuguese Contest** | Micromouse Classic | 🥇 | 2026 |
| <img src="./images/flags/romania-flag-xs.png" height="16px" title="Romania" alt="🇷🇴"/> **RoboChallenge** | Maze | 🥇 | 2025 |
| <img src="./images/flags/spain-flag-xs.png" height="16px" title="Spain" alt="🇪🇸"/> **OSHWDem** | Micromouse Classic | 🥇 | 2025 |
| <img src="./images/flags/portugal-flag-xs.png" height="16px" title="Portugal" alt="🇵🇹"/> **Micromouse Portuguese Contest** | Micromouse Classic | 🥇 | 2025 |
| <img src="./images/flags/portugal-flag-xs.png" height="16px" title="Portugal" alt="🇵🇹"/> **Micromouse Portuguese Contest** | Time Trial | 🥇 | 2025 |
| <img src="./images/flags/romania-flag-xs.png" height="16px" title="Romania" alt="🇷🇴"/> **RoboChallenge** | Maze | 🥇 | 2024 |
| <img src="./images/flags/spain-flag-xs.png" height="16px" title="Spain" alt="🇪🇸"/> **OSHWDem** | Micromouse Classic | 🥇 | 2024 |
| <img src="./images/flags/spain-flag-xs.png" height="16px" title="Spain" alt="🇪🇸"/> **OSHWDem** | Micromouse Wall-Follower | 🥇 | 2023 |

---

## ⚙️ Hardware

- **Microcontroller**: STM32F405RGT6 @ 168 MHz
- **Motor driver**: MP6551 @ 20 kHz
- **Gyroscope**: LSM6DSRTR, 4000 dps
- **Encoders**: AS5145B-HSST
- **MOSFETs**: AO3400 (A09T), used to switch both the sensor emitters and the suction fan
- **Regulator**: CN3903 + LDO ME611C33M5G
- **38 kHz IR receiver**: TSSP77038TR
- **Battery**: Turnigy nano-tech LiPo 2S, 260 mAh, 35–70C
- **Sensors**:
  - 4× SFH-4550 IR emitters
  - 4× ST-1KL3A IR receivers
- **Drive system**:
  - 2× generic 8520 7.4 V coreless motors (AliExpress)
  - Kyosho K.MZW39-30 tire rubber
  - PCB chassis with motor and fan mounts made from PLA
  - 8T 0.5M motor pinions
  - 40T 0.5M wheel gears
  - 22T 0.5M resin-printed encoder gears
  - 4× MR63ZZ bearings (wheels)
  - 2× MR52ZZ bearings (encoders)
  - 2× 6×2.5 mm radial magnets

![ZoroBot3 Chassis](./images/ZoroBot3_rev2_3d_model.png "ZoroBot3 - Chassis")

## 💻 Software

- Developed in VSCode and PlatformIO using LibOpenCM3.
- All analog values are read using **DMA** and processed every 1 ms.
- Sensors are read by a **16 kHz state machine**, which switches the emitters on and off to **filter ambient light**.
- Encoder values are read in **hardware quadrature mode** using two timers.
- The IMU is read over SPI.
- The main control loop—comprising linear-speed, angular-speed, front-wall, and side-wall PID controllers—runs every 1 ms.
- Position is reset when a side wall is lost to improve navigation.
- Turns use **sinusoidal acceleration** profiles for smoother motion.
- The firmware includes right- and left-wall following, exploration, and solving programs using weighted FloodFill (see [TimeBased FloodFill Simulator](https://github.com/OPRobots/TimeBased-FloodFill-Simulator)), as well as hardcoded movement sequences.

## 🎥 Videos

### Micromouse Portuguese Contest 2026 - 🥇
<p align="center" width="100%">
<video src="https://github.com/user-attachments/assets/5a7cf803-e31e-463a-afa9-e5784b378937" width="80%" controls></video>
</p>

### OSHWDem 2025 - 🥇
<p align="center" width="100%">
<video src="https://github.com/user-attachments/assets/332fd117-6600-4692-b59f-4b1154166f3f" width="80%" controls></video>
</p>

### Micromouse Portuguese Contest 2025 - 🥇
<p align="center" width="100%">
<video src="https://github.com/user-attachments/assets/cf21e942-3fe0-4065-8892-fa3d181a9791" width="80%" controls></video>
</p>

### RoboChallenge 2024 - 🥇
<p align="center" width="100%">
<video src="https://github.com/user-attachments/assets/a8c53e97-a756-4934-9c83-6c93fda1b235" width="80%" controls></video>
</p>

### OSHWDem 2024 - 🥇
<p align="center" width="100%">
<video src="https://github.com/user-attachments/assets/a70629e6-34b6-473f-afb0-14d8290bd128" width="80%" controls></video>
</p>
