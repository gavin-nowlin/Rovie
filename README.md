# 🚀 Rovie: Lunar Road Construction
### **Autonomous Rover for Constructing Roads on the Lunar Terrain**  
[![GitHub repo](https://img.shields.io/badge/GitHub-Rovie-blue?style=flat&logo=github)](https://github.com/gavin-nowlin/Rovie)

## 📌 Project Overview
Rovie is a **surface construction rover** designed for **autonomous picking and placing of pavers**.  
This project aims to create a **semi-autonomous system** capable of efficiently **starting and extending roads**.  

---

## 📁 Repository Structure
```
rovie/
├── main.py                       # Main entry point (handles mode switching)
├── README.md                     # Project overview and setup instructions
│
├── archive/                      # Files from the previous team that are no longer in use
│   ├── force_sensor.py           # No longer needed
│   ├── force_sensor.py           # No longer needed
│   ├── map_tracker.py            # Replaced with paver_database.py
│   ├── test_pathing_straight.py  # No longer needed
│   └── obstacle_avoidance.py     # Simplified into navigation.py
│
├── arduino/                      # C++ Arduino code
│   ├── README.md                 # Flashing instructions, serial protocol docs
│   └── MotorCommunication.ino    #
│
├── configs/                      #
│   ├── README.md                 #
│   ├── __init__.py               # 
│   ├── constants.py              # All project-wide constants (distances, thresholds)
│   ├── gripper_config.py         # 
│   ├── mission_config.py         # 
│   ├── paver_specs.py            # 
│   ├── pins.py                   # GPIO pin mappings for Raspberry Pi
│   └── test_scenarios.py         # Testing Scenarios for when mocking hardware testing
│
├── core/                         # Core logic for behavior and modes
│   ├── autonomous.py             #
│   ├── navigation.py             #
│   ├── paver_pickup.py           #
│   ├── paver_placement.py        #
│   ├── mission_planner.py        #
│   ├── obstacle_avoidance.py     # Force button logic and rerouting
│   ├── state_machine.py          # Handles transitions between behaviors
│   └── arm_control_logic.py      # Decision logic for when to move arm
│
├── docs/                         # Repo documentation
│   ├── README.md                 # Overview and table of contents for docs
│   └── TRANSITION.md             # Details repo transition from lunar clearer to constructor
│
├── hardware/                     # Interfaces for sensors and actuators
│   ├── README.md                 # 
│   ├── __init__.py               # 
│   ├── gps.py                    # GPS interface
│   ├── gripper.py                # 
│   ├── camera.py                 # 
│   ├── imu.py                    # 
│   ├── arm.py                    # 
│   ├── motors.py                 # Send commands to Arduino
│   ├── estop.py                  # Emergency stop button logic
│   └── mock/                     # Mock versions of above (for testing without hardware)
│       ├── __init__.py           # 
│       ├── gps.py                # 
│       ├── gripper.py            # 
│       ├── camera.py             # 
│       ├── imu.py                # 
│       ├── arm.py                # 
│       ├── motors.py             # 
│       ├── estop.py              # 
│       └── force_button.py       # 
│
├── logs/                         # All generated logs saved here
│   ├── gps/                      # 
│   ├── sensors/                  # 
│   ├── flags/                    # 
│   ├── errors/                   # 
│   └── README.md                 # 
│
├── testing/                      # Unit and integration tests
│   ├── test_gps.py               # Runs GPS code in isolation
│   ├── test_state_machine.py     # 
│   ├── test_navigation.py        # 
│   ├── test_gripper.py           # 
│   ├── test_paver_detection.py   # 
│   ├── test_pickup_routine.py    # 
│   ├── test_placement_routine.py # 
│   └── README.md                 # 
│
└── utils/                        # 
    ├── logger.py                 # Logging GPS data, sensor events, errors
    ├── paver_database.py         # 
    ├── vision_processor.py       # 
    ├── waypoint_planner.py       # 
    ├── coordinate_utils.py       # Haversine + coordinate math
    └── timer.py                  # For timeouts, delays, safety checks

```

---

## 🛠 Features
- ✅ **Autonomous Pathing** – Uses GPS & IMU for navigation  
- ✅ **Obstacle Avoidance** – Detects large rocks & reroutes  
- ✅ **Motor Control** – Smooth movement and turning logic  
- ✅ **Plow System** – Vibrating motors to clear regolith  
- ✅ **Force Sensor Integration** – Adjusts movement based on resistance  

---

## 📦 Getting Started

### 🔧 Prerequisites
- Raspberry Pi (or another microcontroller)
- Arduino (for motor control)
- GPS Module (e.g., u-blox NEO-6M)
- IMU Sensor (e.g., MPU6050)
- Motor drivers
- Python 3.x installed

### 📥 Installation

1️⃣ **Clone the Repository**  
```bash
git clone git@github.com:gavin-nowlin/Rovie.git
cd Rovie
```
2️⃣ **Install Dependencies**  
```bash
pip install -r requirements.txt
```
3️⃣ **Run the Rover Control Script**  
```bash
python main.py
```

---

## ⚡ Hardware & Sensor Setup

| Component  | Purpose |
|------------|---------|
| **Raspberry Pi**  | Controls pathing & sensors |
| **Arduino**  | Motor control |
| **GPS Module**  | Provides location data |
| **IMU Sensor**  | Detects tilt and movement |
| **Force Sensor** | Adjusts plowing force |

---

## 🔬 Testing & Debugging
- **Run unit tests**:  

- **View system logs**:  
  ```bash
  tail -f logs/system.log
  ```
- **Simulate pathing in a virtual environment**:  


---

## 🛠 Contributing

Want to help? Here’s how:

1. **Fork the repo**  
2. **Create a feature branch**:  
   ```bash
   git checkout -b feature/new-pathing
   ```
3. **Commit changes**:  
   ```bash
   git commit -m "Added new obstacle detection logic"
   ```
4. **Push to GitHub**:  
   ```bash
   git push origin feature/new-pathing
   ```
5. **Create a pull request** 🎉  

---

## 📅 Project Tasks & Issues
🚀 **Want to see what’s next?** Check out our [GitHub Issues](https://github.com/gavin-nowlin/Rovie/issues) for ongoing tasks.

---

## 📜 License
This project is licensed under the

---

## 👥 Team Members
| Name | Role |
|------|------|
| **Trent Anderson** | Software Developer |
| **Bo Brynjulfson** | Computer Engineer |
| **Connor Kuziemko** | Software Developer |
| **James Mather** | Lead Mechanical Engineer |
| **Blake Miller** | Engineering Physics |
| **Gavin Nowlin** | Lead Software Developer |
| **Hayden Rutland** | Mechanical Engineer |
| **Colin Sadowitz** | Team Lead & Software Developer |
| **Eddrick Tirado** | Electrical Lead |

## 👥 Original Team Members
| Name | Role |
|------|------|
| **Eva Rodriguez** | Integration Specialist |
| **Cate Holt** | Hardware Specialist |
| **Alex Go** | Software Developer |

---

## 🔗 Useful Resources
- 📖 **[Project Docs](docs/README.md)**
- 🛠 **[Hardware Setup Guide](docs/hardware.md)**
- 🚀 **[Software Overview](docs/software.md)**

---

## 📌 Next Steps

---