# Flightmare Setup Notes

## Purpose

Flightmare is used as the main thesis simulator for DRL-based autonomous drone navigation.

It is selected because it is relevant to agile quadrotor flight, visual navigation and drone racing research.

## Workspace

```text
~/flightmare_ws/flightmare
~/flightmare_ws/flightmare_env
```

## Current Status

Flightmare has been built successfully on Ubuntu 22.04.

Verified components:

- `flightgym` Python binding imports successfully
- `QuadrotorEnv_v1` is available
- `TestEnv_v0` is available
- `flightlib/tests/flightgym/interface.py` runs
- Unity renderer binary launches
- C++ Unity bridge test works
- RGB bridge test starts
- Depth bridge test starts
- Segmentation bridge test starts
- Point cloud bridge test starts
- ZeroMQ / zmqpp bridge issues resolved

## Important Notes

ROS is not required for the Flightmare Unity connection.

Legacy TensorFlow-based `flightrl` examples are skipped because this thesis uses a modern PyTorch-based training direction.

## Research Decision

Flightmare will be used as the core DRL research simulator.

The next goal is to build a modern Gymnasium-compatible wrapper for Flightmare so that it can be trained using:

- Stable-Baselines3
- RLlib
- Pure PyTorch
