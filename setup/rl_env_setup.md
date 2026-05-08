# RL Environment Setup

## Purpose

The RL environment is used for modern reinforcement learning development.

It is separate from ROS 2 to avoid dependency conflicts.

## Workspace

```text
~/rl_lab/rl_env
```

## Main Tools
- Python
- PyTorch
- Gymnasium
- Stable-Baselines3
- RLlib / Ray
- PyBullet
- TensorBoard
- NumPy
- Matplotlib

## Role in Thesis

This environment is used for:

- Basic RL algorithm validation
- CartPole and other Gymnasium tests
- SB3 experiments
- RLlib experiments
- PyBullet drone RL training
- Algorithm comparison
- Debugging observation/action spaces

## Important Decision

Old TensorFlow 1.x and stable_baselines 2.x dependencies are not installed in this environment.

The goal is to keep the environment modern and focused on PyTorch-based reinforcement learning.

## Current Status
- RL environment created
- Gymnasium direction selected
- Stable-Baselines3 direction selected
- RLlib / Ray direction selected
- PyBullet drone examples tested
