# Deep Reinforcement Learning-Based Autonomous Drone Navigation

This repository documents my MS research project on **Deep Reinforcement Learning-Based Autonomous Drone Navigation**.

The project follows a simulation-first robotics research pipeline. The goal is to develop, train, evaluate and eventually deploy DRL-based quadrotor navigation policies.

## Research Motivation

Autonomous drone navigation in complex environments requires robust perception, control, decision-making and safe deployment. Deep Reinforcement Learning provides a promising approach for learning navigation policies through interaction, but real-world drone training is expensive and risky.

Therefore, this project starts with simulation-based development and gradually moves toward deployment-oriented robotics integration.

## Research Pipeline

1. Validate DRL algorithms on simple Gymnasium tasks
2. Test drone control baselines in PyBullet
3. Use Flightmare as the main thesis simulator
4. Build a modern Gymnasium-compatible Flightmare wrapper
5. Train policies using Stable-Baselines3, RLlib and PyTorch
6. Integrate policy inference with ROS 2
7. Test RealSense-based perception
8. Move toward Jetson Orin Nano deployment

## Current Environment Status

- Native Ubuntu 22.04
- NVIDIA GPU available
- Python virtual environments for RL isolation
- ROS 2 Humble installed system-wide
- Gazebo Fortress installed
- PyBullet drone examples tested
- Flightmare built successfully
- Flightmare Python bindings tested
- Unity renderer and bridge tests verified

## Main Tools

- Python
- PyTorch
- Gymnasium
- Stable-Baselines3
- RLlib / Ray
- PyBullet
- Flightmare
- ROS 2 Humble
- Gazebo Fortress
- RealSense
- Jetson Orin Nano

## Repository Structure

```text
docs/       Thesis planning, research notes and progress tracking
setup/      Environment setup and installation notes
results/    Experiment logs, test summaries and observations
diagrams/   Pipeline diagrams and architecture figures
```

## Current Focus

The current focus is to document the working Ubuntu 22.04 research environment and prepare the foundation for a modern Flightmare-to-Gymnasium DRL training pipeline.

Flightmare is treated as the main thesis simulator. PyBullet is used for fast baseline testing. ROS 2 and Gazebo are used for robotics integration and deployment-style testing.

## Thesis Repository Ecosystem

This thesis pipeline is organized into separate repositories to keep training, visualization and documentation modular.

| Repository | Role |
|---|---|
| `drl-drone-navigation-thesis` | Main thesis hub, research pipeline, setup notes, progress tracking |
| `rl-gym-pybullet-drone-baselines` | Foundational RL, Gymnasium, continuous-control, and early PyBullet drone baseline work |
| `flightmare-headless-rl-wrapper` | Mode A: headless Flightmare RL training using Gymnasium/SB3/PyTorch |
| `flightmare_racing_visualization` | Mode B: Flightmare Unity visualization, YAML racing tracks, camera capture and gate-passing logs |

### Foundational RL and PyBullet Baselines

Repository:

`rl-gym-pybullet-drone-baselines`

This repository documents the early learning and baseline-testing phase of the thesis. It includes SB3 and RLlib experiments on Gymnasium environments such as CartPole, Pendulum, and MountainCarContinuous, plus initial PyBullet drone simulation testing.


### Mode A: Headless RL Training

Mode A focuses on fast reinforcement learning training without Unity rendering.

Repository:

`flightmare-headless-rl-wrapper`

Main features:

- Flightmare buffer-based wrapper
- Gymnasium-compatible single environment
- SB3-compatible VecEnv wrapper
- Scaled-action wrapper
- PPO headless training and evaluation
- Action-scale ablation

### Mode B: Unity Racing Visualization

Mode B focuses on Flightmare UnityBridge visualization and racing-track tooling.

Repository:

`flightmare_racing_visualization`

Main features:

- YAML-driven racing tracks
- Scene selection
- Local-origin scene calibration
- Onboard camera capture
- Gate-passing detection
- CSV logging
- UZH/RPG-inspired configurable track templates

Mode A and Mode B are intentionally separated. Mode A is used for training and evaluation, while Mode B is used for visualization, track tooling and future trained-policy demonstrations.