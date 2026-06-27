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

This thesis pipeline is organized into separate repositories to keep foundational learning, Flightmare training, visualization, reusable pipeline code, and final evidence documentation modular.

| Repository | Role |
|---|---|
| `drl-drone-navigation-thesis` | Main thesis hub, research pipeline, setup notes, and progress tracking |
| `rl-gym-pybullet-drone-baselines` | Foundational RL, Gymnasium, continuous-control, and early PyBullet drone baseline work |
| `flightmare-headless-rl-wrapper` | Flightmare headless RL wrapper and PPO training/evaluation tools |
| `flightmare_racing_visualization` | Flightmare UnityBridge visualization, YAML racing tracks, camera capture, and gate-passing logs |
| `flightmare-vision-aware-drl-pipeline` | Reusable implementation pipeline for vision-aware Flightmare gate-navigation experiments |
| `flightmare-vision-aware-drl-results` | Curated thesis-ready results, plots, tables, GIFs, videos, screenshots, and visual validation evidence |

## Research Progression

```text
Foundational Gymnasium / PyBullet RL baselines
↓
Flightmare headless RL wrapper
↓
Flightmare UnityBridge visualization and racing-track tooling
↓
Vision-aware Flightmare DRL pipeline
↓
Curated thesis results and visual evidence archive
```

## Vision-Aware Flightmare DRL Pipeline and Results

The latest Flightmare thesis work is split into two complementary repositories.

### Implementation Repository

`flightmare-vision-aware-drl-pipeline`

This repository contains the reusable implementation pipeline for:

- Privileged-state teacher PPO training
- Teacher rollout dataset generation
- Compact gate/vision-feature observation design
- 25D vision-proprioceptive student observation design
- Imitation learning
- PPO-from-scratch baselines
- IL-initialized PPO fine-tuning
- Robustness evaluation
- UnityBridge replay export

### Results and Evidence Repository

`flightmare-vision-aware-drl-results`

This repository contains curated thesis-ready evidence:

- Phase-wise reports
- Policy comparison tables
- Failure-mode summaries
- Observation-space comparisons
- Phase 5 imitation-learning diagnostics
- Phase 8 robustness plots
- Phase 9 UnityBridge replay GIFs and MP4s
- Onboard RGB evidence
- Feature-to-camera consistency evidence

### Important Interpretation

The current vision-aware DRL result demonstrates replay-based visual validation of a compact 25D vision-proprioceptive imitation-learning policy in Flightmare UnityBridge.

It should not be interpreted as:

- raw RGB end-to-end control,
- real-world drone deployment,
- fully validated sim-to-real transfer.

It is a thesis-level simulation pipeline toward vision-aware autonomous drone navigation using DRL.