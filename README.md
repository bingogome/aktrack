# Autokinesis Tracker (aktrack)

A comprehensive system for tracking eye and hand movements during visual perception experiments with a focus on autokinesis effects.

![demo_5min_data](https://github.com/bingogome/aktrack-slicer/blob/main/demo_5min_data.gif)

## Overview

The Autokinesis Tracker system integrates several specialized components to create a complete experimental setup for tracking and analyzing eye and hand movements during visual perception tasks. The system was developed at Johns Hopkins University to study visual perception phenomena, particularly focusing on the autokinesis effect (the apparent movement of a stationary light source when viewed in darkness).

## System Architecture

The Autokinesis Tracker consists of multiple interconnected components, each responsible for a specific aspect of the experimental setup:

1. **Control Center (aktrack-slicer)**: The main user interface for managing experiments, built as a 3D Slicer extension
2. **Eye Tracking (aktrack-goggle)**: Tracks eye movements using specialized goggles
3. **Visual Stimuli (aktrack-screen)**: Displays visual targets with controlled movement parameters
4. **Hand Tracking (aktrack-ros)**: Tracks hand/pointer position using optical tracking or joystick input
5. **Data Processing (aktrack-matlab)**: Analysis tools for experimental data
6. **Data Storage (aktrack-data)**: Repository for experimental data and results

## Features

- **Comprehensive Tracking**: Simultaneous tracking of eye and hand movements
- **Multiple Experimental Protocols**:
  - VPB (Visual Perception of Bias) - Stationary dot tasks
  - VPM (Visual Perception of Motion) - Moving dot tasks with variable speeds
  - VPC (Visual Perception Calibration) - System calibration procedures
- **Controlled Visual Stimuli**: Precise control of stimuli position, speed, and direction
- **Integrated Data Recording**: Synchronized data collection across all tracking devices
- **Real-time Visualization**: Live display of tracking data during experiments
- **Flexible Analysis**: Tools for post-experiment data processing and analysis

## Setup Requirements

Please refer to all sub repos for specific guides.

### Hardware

- Computer system with multiple monitors
  - Control room computer (running 3D Slicer and ROS)
  - Subject room computer (running visual stimuli display)
- Eye tracking goggles
- Hand tracking device (optical tracker or joystick)
- Network connection between control and subject computers

### Software

- Windows: 3D Slicer and eye tracking components
- Linux (Ubuntu): ROS for hand tracking component
- Python 3.6+
- C# (.NET Framework)
- MATLAB for data analysis

## Installation

The Autokinesis Tracker system uses Git submodules to manage its components. To install the complete system:

1. Clone the repository with all submodules:
   ```bash
   git clone --recursive https://github.com/bingogome/aktrack.git
   ```

2. Alternatively, clone the repository and then initialize submodules:
   ```bash
   git clone https://github.com/bingogome/aktrack.git
   cd aktrack
   git submodule update --init --recursive
   ```

3. Follow the installation instructions for each component:

   - **aktrack-slicer**: Install as a 3D Slicer module
   - **aktrack-goggle**: Run directly on Windows
   - **aktrack-screen**: Run directly on Windows
   - **aktrack-ros**: Build as a ROS workspace on Linux
   - **aktrack-matlab**: Run directly in MATLAB

## Component-Specific Setup

### Control Center (aktrack-slicer)

1. Install 3D Slicer
2. Add the aktrack-slicer directory as a module path in 3D Slicer settings
3. Restart 3D Slicer and locate the "Control Room" module

### Eye Tracking (aktrack-goggle)

1. Set up the eye tracking goggles in the subject room
2. Configure the IP address in the configuration file to match your network
3. Run the application.py script

### Visual Stimuli (aktrack-screen)

1. Set up a display in the subject room
2. Configure the IP address in the configuration file to match your network
3. Run the application.py script

### Hand Tracking (aktrack-ros)

1. Create a ROS workspace
2. Use the provided script to link the submodules
3. Build the workspace with `catkin build`
4. Launch the system with `roslaunch aktrack_ros all.launch`

### Data Processing (aktrack-matlab)

1. Open MATLAB
2. Add the aktrack-matlab directory to your MATLAB path
3. Run the analysis scripts as needed

## Network Configuration

The Autokinesis Tracker components communicate over a network using UDP. Default ports:

- **Eye Tracking**: 8297 (receive), 8293 (send)
- **Visual Stimuli**: 8753 (receive), 8757 (send), 8769 (acknowledge)
- **Hand Tracking**: 8057 (receive), 8059 (send), 8083 (high-frequency)

These port configurations can be adjusted in the respective configuration files.

## Running Experiments

1. Start all components (Control Center, Eye Tracking, Visual Stimuli, Hand Tracking)
2. In the Control Center:
   - Create or select a subject
   - Generate or load an experiment sequence
   - Connect to all components
   - Calibrate the eye tracking system
3. Start the experiment from the Control Center
4. Monitor real-time results during the experiment
5. Analyze collected data after the experiment

## Experimental Protocols

### Visual Perception of Bias (VPB)

- **VPB-hfixed**: Stationary target with fixed head position
- **VPB-hfree**: Stationary target with free head movement

### Visual Perception of Motion (VPM)

- Format: `VPM-[speed]-[direction]`
- Speeds: 2, 4, 6, 8, 12, 18 deg/sec
- Directions: L (left), R (right), U (up), D (down)
- Example: `VPM-6-R` - 6 deg/sec rightward movement

### Visual Perception Calibration (VPC)

- Format: `VPC-[direction]`
- Fixed speed of 2 deg/sec
- Directions: L, R, U, D

## Data Structure

Experimental data is saved with a standardized naming convention:
```
[timestamp]_[subject]_[trial-type].csv
```

Data files include timestamps and positional data for both eye and hand tracking.

## Troubleshooting

- **Connection Issues**: Verify IP addresses and ports in all configuration files
- **Tracking Problems**: Run calibration procedures for eye and hand tracking
- **Missing Data**: Check that all components are properly recording and saving data
- **Synchronization Issues**: Ensure system clocks are synchronized across devices

## Citation

If you use the Autokinesis Tracker system in your research, please cite:

@article{liu2024autokinesis, title={Autokinesis Reveals a Threshold for Perception of Visual Motion}, author={Liu, Yihao and Tian, Jing and Martin-Gomez, Alejandro and Arshad, Qadeer and Armand, Mehran and Kheradmand, Amir}, journal={Neuroscience}, volume={543}, pages={101--107}, year={2024}, publisher={Elsevier} }
