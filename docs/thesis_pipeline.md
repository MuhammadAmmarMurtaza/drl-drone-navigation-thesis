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
