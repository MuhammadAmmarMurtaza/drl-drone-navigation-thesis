# Ubuntu 22.04 Research System Setup

## System Choice

This research setup uses native Ubuntu 22.04 instead of WSL.

The reason for using native Ubuntu is better compatibility with:

- NVIDIA GPU access
- USB devices
- RealSense cameras
- Robotics middleware
- Simulators
- ROS 2
- Gazebo
- Flightmare

## Base System

- Operating system: Ubuntu 22.04
- GPU: NVIDIA GPU available
- Python environments: virtual environments
- ROS 2: installed system-wide using apt
- RL libraries: installed inside isolated Python virtual environments

## Workspace Philosophy

The system uses separate workspaces for different parts of the research pipeline.

Example structure:

```text
~/
├── rl_lab/
├── flightmare_ws/
├── ros2_ws/
├── realsense_ws/
└── github_portfolio/

Environment Separation

ROS 2 is kept at the system level.

RL libraries such as PyTorch, Stable-Baselines3, RLlib and Gymnasium are kept inside Python virtual environments.

This avoids conflicts between ROS 2 Python packages and modern RL packages.

Current Status
Ubuntu 22.04 installed
NVIDIA GPU available
Python virtual environments used
ROS 2 Humble installed
Gazebo Fortress installed
Flightmare built successfully
PyBullet drone examples tested
