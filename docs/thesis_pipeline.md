# Thesis Pipeline

## Project Title

Deep Reinforcement Learning-Based Autonomous Drone Navigation

## Objective

The objective of this research is to develop, train, evaluate and eventually deploy DRL-based navigation policies for quadrotor drones.

The project follows a simulation-first approach, where policies are first developed in controlled simulation environments and later moved toward deployment-oriented robotics integration.

## Pipeline Overview

### Stage 1: Basic RL Validation

Simple Gymnasium environments are used to validate reinforcement learning algorithms and training workflows.

Example tasks:

- CartPole
- MountainCar
- LunarLander

Purpose:

- Understand environment interaction
- Compare SB3, RLlib and pure PyTorch workflows
- Validate logging and evaluation methods

---

### Stage 2: PyBullet Drone Baselines

PyBullet drone simulation is used for fast testing of drone control, hovering and baseline RL experiments.

Purpose:

- Test drone dynamics quickly
- Debug observation and action spaces
- Design reward functions
- Train early PPO/SAC baselines

---

### Stage 3: Flightmare Main Simulator

Flightmare is used as the main thesis simulator because it is designed for agile quadrotor flight and visual navigation research.

Purpose:

- Quadrotor navigation experiments
- Visual navigation
- Racing-style tasks
- RGB, depth, segmentation and point cloud bridge testing
- High-speed drone navigation research

---

### Stage 4: Modern Flightmare Gymnasium Wrapper

A modern Gymnasium-compatible wrapper will be developed for Flightmare.

Purpose:

- Avoid outdated TensorFlow 1.x and stable_baselines 2.x dependencies
- Use modern DRL tools such as Stable-Baselines3, RLlib, and PyTorch
- Create a cleaner training interface

---

### Stage 5: ROS 2 and Gazebo Integration

ROS 2 and Gazebo are used for system integration and deployment-style testing.

Purpose:

- Sensor node design
- Policy inference node
- Command publishing
- RealSense integration
- Simulation-to-deployment architecture

---

### Stage 6: RealSense and Jetson Deployment

Future work will move toward hardware-oriented testing using RealSense sensors and Jetson Orin Nano.

Purpose:

- RGB-D perception
- Visual-inertial tracking
- Onboard inference
- Edge deployment testing

## Simulator Roles

| Simulator / Tool | Role |
|---|---|
| Gymnasium | Basic RL algorithm validation |
| PyBullet drones | Fast drone baseline testing |
| Flightmare | Main thesis simulator |
| ROS 2 + Gazebo | Robotics integration and deployment testing |
| AirSim | Optional future comparison |

## Completed Technical Milestone: Mode A Headless RL

The first completed technical milestone is a reusable repository named:

`flightmare-headless-rl-wrapper`

This repository implements Mode A: headless reinforcement learning training using Flightmare's quadrotor backend without Unity rendering.

Key achievements:

- Flightmare buffer-based Python binding wrapped for modern RL use
- Gymnasium-compatible single-environment wrapper created
- SB3-compatible vectorized wrapper created
- Scaled-action wrapper created
- PPO training and evaluation completed in headless mode
- 100 native Flightmare parallel environments used for vectorized RL
- Action-scale ablation completed
- Best current internal action range: ±0.5

This establishes the first stable baseline for Flightmare-based DRL training in the thesis pipeline.

## Mode B: Flightmare Unity Racing Visualization

Mode B focuses on Unity-based visualization and racing-track tooling for the Flightmare thesis pipeline.

The dedicated repository is:

`flightmare_racing_visualization`

### Purpose

This repository provides configurable Flightmare UnityBridge tools for:

- Quadrotor racing visualization
- YAML-driven racing tracks
- Scene selection
- Local-origin scene calibration
- Onboard camera capture
- UZH/RPG-inspired track templates
- Gate-passing detection
- CSV logging

### Relationship to Mode A

Mode A headless RL training is handled separately in:

`flightmare-headless-rl-wrapper`

Mode B visualization and racing-track tooling is handled in:

`flightmare_racing_visualization`

This creates a clean separation:

| Mode | Repository | Purpose |
|---|---|---|
| Mode A | `flightmare-headless-rl-wrapper` | Headless RL training and PPO evaluation |
| Mode B | `flightmare_racing_visualization` | Unity visualization, track tooling, camera capture, and gate logging |

### Current Mode B Features

- YAML track loader
- Flightmare UnityBridge scene connection
- Quadrotor and gate spawning
- World-coordinate track support
- Local-origin calibrated track support
- Scene selection for Warehouse, Industrial, Garage, and NatureForest
- Configurable onboard camera capture
- RGB/depth/segmentation capture testing
- Sequential gate-passing logger
- CSV output for gate-pass events
- Lap completion detection
- UZH/RPG-inspired configurable track templates

### Current Mode B Limitations

- Flightmare must be installed separately
- Unity renderer binaries are not included
- Examples currently use scripted trajectory playback
- Learned policy visualization is a future milestone
- UZH/RPG-inspired tracks are approximate templates, not official reproductions

### Thesis Role

Mode B provides the visualization and racing-track tooling layer needed to inspect, demonstrate, and later evaluate trained policies from Mode A.

The future goal is to connect policies trained in `flightmare-headless-rl-wrapper` to Unity visualization workflows in `flightmare_racing_visualization`.

## Foundational RL and PyBullet Drone Baselines

Before advanced Flightmare-based quadrotor training, the thesis pipeline includes a foundational reinforcement learning and early drone-simulation baseline phase.

The dedicated repository is:

`rl-gym-pybullet-drone-baselines`

### Purpose

This repository documents and implements early reinforcement learning experiments using:

- Gymnasium
- Stable-Baselines3
- RLlib / Ray
- PyTorch
- PyBullet
- External `gym-pybullet-drones` testing

The purpose is to build algorithm understanding and baseline control experience before moving to more advanced Flightmare-based quadrotor learning.

### Learning Progression

The foundational learning path is:

```text
CartPole-v1
↓
Pendulum-v1
↓
MountainCarContinuous-v0
↓
Reacher / InvertedPendulum
↓
gym-pybullet-drones
↓
custom quadcopter Gym environment
↓
Flightmare
↓
ROS 2 / Gazebo / RealSense / Jetson integration
```

### Repository Role in Thesis

| Repository | Role |
|------------|------|
| `rl-gym-pybullet-drone-baselines` | Foundational reinforcement learning experiments, Gymnasium environments, continuous-control algorithms, and early PyBullet drone testing |
| `flightmare-headless-rl-wrapper` | Advanced Mode A headless Flightmare reinforcement learning training |
| `flightmare_racing_visualization` | Mode B Flightmare Unity visualization and racing-track tooling |
| `drl-drone-navigation-thesis` | Main thesis repository, documentation hub, and progress tracker |

### Algorithms Covered

This repository includes experiments, implementations, and notes for the following reinforcement learning algorithms:

- PPO (Proximal Policy Optimization)
- SAC (Soft Actor-Critic)
- TD3 (Twin Delayed Deep Deterministic Policy Gradient)
- A2C (Advantage Actor-Critic)
- DQN (Deep Q-Network)

### Algorithm Relevance

PPO is treated as the first stable baseline because of its robustness and simplicity.

SAC is important for continuous-control robotics because it is sample-efficient and uses entropy regularization for exploration.

TD3 is important for deterministic continuous-control tasks and can be useful for precise low-level control.

DQN is included for discrete-control understanding but is not considered suitable for direct continuous drone motor control.

### PyBullet Drone Role

PyBullet drone simulation is treated as a lightweight intermediate step before Flightmare.

It is useful for:

- Visual drone simulation sanity checks
- Basic hover and control experimentation
- Early debugging of drone states, actions, and observations
- Reinforcement learning integration testing
- Bridging the gap between simple Gymnasium tasks and full quadrotor simulators

### Relationship to Flightmare

This repository is intentionally kept separate from the Flightmare repositories.

It supports the thesis foundation, while the advanced Flightmare work is handled in:

- `flightmare-headless-rl-wrapper`
- `flightmare_racing_visualization`

---

## Flightmare Vision-Aware DRL Gate-Navigation Pipeline

The latest focused technical direction is:

**From Privileged State to Vision Features: A Practical Flightmare Pipeline for DRL-Based Drone Gate Navigation**

This work is organized into two repositories:

| Repository | Purpose |
|---|---|
| `flightmare-vision-aware-drl-pipeline` | Reusable implementation pipeline |
| `flightmare-vision-aware-drl-results` | Curated results and visual evidence archive |

### Pipeline Repository

`flightmare-vision-aware-drl-pipeline`

This repository contains reusable source code, configs, scripts, and documentation for:

- Privileged-state teacher policy training
- Teacher rollout dataset generation
- 12D gate-feature student learning
- 25D vision-proprioceptive student learning
- PPO-from-scratch baselines
- IL-initialized PPO fine-tuning
- Robustness evaluation
- UnityBridge replay export

### Results Repository

`flightmare-vision-aware-drl-results`

This repository contains selected thesis-ready results and evidence:

- Phase-wise reports
- Policy comparison tables
- Failure-mode summaries
- Observation-space summaries
- Training/evaluation figures
- UnityBridge replay GIFs and videos
- Onboard RGB evidence
- Feature-to-camera consistency evidence

### Main Experimental Conclusion

The 25D vision-proprioceptive imitation-learning student was the strongest practical student policy.

It was trained using teacher-guided imitation learning and uses a compact observation space combining gate/vision-like features with proprioceptive feedback.

### Key Interpretation

The pipeline shows that moving from privileged state to compact vision-proprioceptive features is a practical intermediate direction for Flightmare-based drone gate navigation.

The current validation is simulation-based and replay-based through UnityBridge. It is not raw RGB end-to-end real-drone deployment.

### Future Research Direction

Future work can extend the reusable pipeline toward:

- Figure-8 tracks
- Split-S tracks
- Kidney tracks
- Multi-lap racing layouts
- More robust policy evaluation
- Better sim-to-real preparation
- ROS 2/Gazebo and hardware-oriented deployment stages