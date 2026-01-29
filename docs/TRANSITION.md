# Rovie Transition
### Details Transitioning Repo from Terrain Clearer to Road Constructor

---

## 📄 Document Overview
This repo was forked from the original repo (can be found [here](https://github.com/irodriguez0482/Rovie)) that was created for a terrain clearing rover that was developed by Senior Capstone students at Florida Polytechnic University during the 2024-2025 school year. Our team inherited this rover and we are modifying it to become a lunar road constructor. This document details what modifications were made to this repo.

---

## 📁 Directory Structure
### ◀️ Previous Structure
```
rovie/
├── main.py                       # Main entry point (handles mode switching)
├── config/
│   ├── constants.py              # All project-wide constants (distances, thresholds)
│   ├── pins.py                   # GPIO pin mappings for Raspberry Pi
│   ├── test_scenarios.py         # Testing Scenarios for when mocking hardware testing
│   └── README.md
├── core/                         # Core logic for behavior and modes
│   ├── autonomous.py             # 3x3 path clearing logic
│   ├── obstacle_avoidance.py     # Force button logic and rerouting
│   ├── state_machine.py          # Handles transitions between behaviors
│   └── arm_control_logic.py      # Decision logic for when to move arm
├── hardware/                     # Interfaces for sensors and actuators
│   ├── gps.py                    # GPS interface
│   ├── motors.py                 # Send commands to Arduino
│   ├── arm.py                    # Vibration + up/down arm control
│   ├── force_button.py           # Read obstacle sensor
│   ├── estop.py                  # Emergency stop button logic
│   ├── README.md
│   └── mock/                     # Mock versions of above (for testing without hardware)
│       ├── gps.py
│       ├── motors.py
│       ├── arm.py
│       ├── estop.py
│       └── force_button.py
├── utils/
│   ├── logger.py                 # Logging GPS data, sensor events, errors
│   ├── coordinate_utils.py       # Haversine + coordinate math
│   ├── timer.py                  # For timeouts, delays, safety checks
│   └── map_tracker.py            # For creating pathing map
├── logs/                         # All generated logs saved here
│   ├── gps/
│   ├── sensors/
│   ├── flags/
│   ├── errors/
│   └── README.md
├── arduino/                      # C++ Arduino code
│   ├── MotorCommunication.ino
│   └── README.md                 # Flashing instructions, serial protocol docs
├── testing/                      # Unit and integration tests
│   ├── test_gps.py               # Runs GPS code in isolation
│   ├── test_force_button.py
│   ├── test_pathing_straight.py  # Can run on real hardware or mock
│   └── ...
└── README.md                     # Project overview and setup instructions

```

### 🆕 Modified Structure
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

