# RoboRacers System

<p align="center">
  <img src="logo_clean.png" alt="RU" width="200"/>
</p>

*A guide to setting up and running the RoboRacers autonomous racing platform.*

## Table of Contents
- [Introduction](#introduction)
- [Requirements](#requirements)
- [Installation & Setup](#installation--setup)
  - [Start the Container](#start-the-container)
  - [Start a Tmux Session](#start-a-tmux-session)
  - [Activate the Car](#activate-the-car)
  - [Activate Rviz](#activate-rviz)
  - [Activate the Drive Package](#activate-the-drive-package)
- [Editing the Drive Publisher](#editing-the-drive-publisher)
- [Conclusion](#conclusion)
- [Acknowledgments](#acknowledgments)

---

## Introduction
This README provides step-by-step instructions on how to start and configure the RoboRacers system. It covers activating the car, setting up visualization in Rviz, and running the drive package.

## Requirements
- A properly configured RoboRacers car
- A PS4 controller
- Access to a Linux terminal with ROS2 installed

## Installation & Setup
### Start the Container
Execute the following commands to start the container:

```bash
cd ~/f1tenth_system/scripts
./run_container.sh
```

This ensures that all necessary environments are correctly loaded.

### Start a Tmux Session
To run multiple processes in parallel, use `tmux`:

```bash
tmux
```

### Activate the Car
Execute the following commands:

```bash
source /opt/ros/foxy/setup.bash
source /f1tenth_ws/install/setup.bash
ros2 launch f1tenth_stack bringup_launch.py
```

This loads the ROS2 environment and starts the required packages for the car.

### Activate Rviz
1. Open a new `tmux` window using **`Ctrl + B` followed by `C`**
2. Run:

```bash
source /opt/ros/foxy/setup.bash
source /f1tenth_ws/install/setup.bash
rviz2
```

3. Configure Rviz:
   - Change `/map` to `/scan`
   - Add **Lazermap**
   - Select **Lazermap** and set the source to `/scan`

### Activate the Drive Package
1. Open a new `tmux` window using **`Ctrl + B` followed by `C`**
2. Build the drive package:

```bash
colcon build --packages-select drive_publisher
source install/setup.bash
```

3. Run the drive package:

```bash
ros2 run drive_publisher drive_publisher
```

## Editing the Drive Publisher
If modifications are needed in the `drive_publisher`, follow these steps:

1. Open the file:

```bash
nano src/drive_publisher/drive_publisher/drive_publisher.py
```

2. Make changes and save using **`Ctrl + X`**, **`Y`**, and **`Enter`**.
3. Rebuild the package:

```bash
colcon build --packages-select drive_publisher
```

## Conclusion
This guide ensures the proper setup and operation of the RoboRacers system. Follow the steps carefully to avoid errors. Contributions and improvements to this guide are welcome!

---

### Acknowledgments
This project is developed by [Jannus-dev](https://github.com/Jannus-dev) and is part of research initiatives from the **Donders Centre for Cognition, Radboud University**, and **Cavaa (Counterfactual Assessment and Valuation for Awareness Architecture)**. 

For more details, visit:
- [Donders Centre for Cognition](https://www.ru.nl/donders/)
- [Radboud University](https://www.ru.nl/english/)
- [Cavaa](https://cavaa.eu/)
  
<p align="center">
  <img src="https://www.ru.nl/sites/default/files/styles/content_full/public/2022-10/logo-donders-institute.png.webp?itok=nkQy2JYH" alt="Donders Centre for Cognition" width="200"/>
  <img src="https://cdn.oneworld.nl/app/uploads/2020/06/Radboud-University-goed.png" alt="RU" width="200"/>
  <img src="https://cavaa.eu/files/cavaa/layout/images/logo.png" alt="Cavaa Logo" width="200"/>
</p>

Special thanks to the RoboRacers community for their contributions.
![RoboRacers Logo](https://roboracer.ai/logos/logo-white-vector-animated.svg) 

---
For more information, visit the [RoboRacers website](https://roboracers.org).

