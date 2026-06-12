
# Progress Log

## Foundational RL and PyBullet Drone Baselines Repository Created

### Repository

`rl-gym-pybullet-drone-baselines`

### Status

`v0.1.0 foundational RL baseline portfolio repo`

### Purpose

This repository documents and implements the foundational reinforcement learning and early drone-simulation baseline phase of the thesis pipeline.

It includes:

- Gymnasium-based RL algorithm testing
- Stable-Baselines3 experiments
- RLlib / Ray experiments
- Discrete-control baselines
- Continuous-control baselines
- Early PyBullet drone simulation testing
- Documentation of algorithm roles for drone-control research

### Relationship to Thesis

This repository represents the foundational learning and baseline-testing phase before advanced Flightmare training, Flightmare Unity visualization, and later ROS 2/Gazebo/hardware integration.

It supports the larger MS thesis direction:

**Deep Reinforcement Learning-Based Autonomous Drone Navigation**

The repository helps build the step-by-step learning path:

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

### Technical Environment

- WSL2 Ubuntu 22.04
- Python 3.10 virtual environment
- Stable-Baselines3 (SB3)
- RLlib / Ray
- Ray version: 2.55.1
- PyTorch
- Gymnasium
- PyBullet
- External `gym-pybullet-drones` tested separately

### Completed Features

- Created clean public GitHub repository under portfolio
- Added organized source scripts for SB3 and RLlib experiments
- Added documentation for foundational RL algorithms
- Added continuous-control learning path
- Added PyBullet drone simulation notes
- Added results summaries
- Added media/GIF previews
- Added run scripts
- Added `.gitignore` to avoid virtual environments, trained models, logs, TensorBoard runs, cache files, and large videos

### Included RL Experiments

#### SB3 CartPole-v1

Algorithms:

- PPO
- A2C
- DQN

#### RLlib CartPole-v1

Algorithms:

- PPO
- DQN

#### SB3 Pendulum-v1

Algorithms:

- PPO
- SAC

#### RLlib Pendulum-v1

Algorithms:

- PPO
- SAC

#### SB3 MountainCarContinuous-v0

Algorithms:

- SAC
- TD3
- PPO optional

### PyBullet Drone Testing

The external `gym-pybullet-drones` project was tested separately.

Observed status:

- `python pid.py` worked successfully
- PyBullet visual simulation opened with drones and scene objects
- `python cf.py` was skipped because `CFAviary` requires `pycffirmware`
- External simulator source code is **not copied** into this repository

### RLlib Notes Documented

Important RLlib 2.55.1 notes were documented:

- New API stack is enabled by default
- Training worked with `config.build_algo()`
- `algo.save()` returns a `TrainingResult`
- Checkpoint path is accessed via `result.checkpoint.path`
- Legacy `compute_single_action()` failed under the new API stack
- Testing was fixed using `algo.get_module("default_policy")`
- CartPole PPO inference uses action-distribution logits with`torch.argmax(...)`

### Algorithm Roles for Drone Research

| Algorithm | Role |
|------------|------|
| PPO | Stable on-policy actor-critic baseline; good first choice but sample inefficient |
| SAC | Strong off-policy continuous-control method with entropy regularization |
| TD3 | Deterministic off-policy continuous-control method useful for precise control |
| A2C | Simpler actor-critic baseline |
| DQN | Useful for discrete actions but not suitable for direct continuous drone motor control |

### Drone-Control Priority

Current priority for drone-control experiments:

1. PPO
2. SAC
3. TD3

### Next Tasks

- Review and polish README presentation
- Add stronger thesis-connection wording
- Improve screenshots and GIF captions
- Add `drone_visual_test.py` implementation for scripted hover, move, and land
- Add PyBullet drone state-inspection script
- Add more continuous-control benchmarks
- Keep this repository focused on foundational RL and PyBullet baselines

## Mode B — Flightmare Unity Racing Visualization Completed

### Repository

`flightmare_racing_visualization`

### Status

`v0.1.0 visualization tooling baseline`

### Purpose

This repository contains Mode B of the thesis pipeline: Flightmare UnityBridge-based racing visualization and track tooling.

It provides configurable tools for:

- YAML-driven racing tracks
- Flightmare UnityBridge visualization
- Scene selection
- Local-origin scene calibration
- Onboard camera capture
- Gate-passing detection
- CSV logging
- UZH/RPG-inspired configurable track templates

### Relationship to Mode A

Mode A headless RL training remains separate in:

`flightmare-headless-rl-wrapper`

Mode B visualization and racing-track tooling is handled in:

`flightmare_racing_visualization`

This separation keeps the thesis pipeline modular:

- Mode A: fast headless RL training and evaluation
- Mode B: Unity visualization, racing-track tooling, camera capture and trajectory/gate analysis

### Completed Features

- Created clean public GitHub repository under portfolio
- Added CMake-based build system
- Added professional example naming instead of internal demo labels
- Added build and run scripts
- Added README and documentation
- Added GIF previews for visual credibility
- Added YAML track loader
- Added scene selection support
- Added local-origin coordinate calibration
- Added onboard camera capture
- Added gate-passing logger with CSV output
- Added approximate UZH/RPG-inspired track templates

### YAML Track Loader

The repository supports loading racing tracks from YAML files.

Supported coordinate modes:

```yaml
use_track_origin: true
track_origin_world: [x0, y0, z0]
```

This allows both direct world-coordinate tracks and local-origin calibrated tracks.

### Supported Scenes

YAML scene selection works for:

- `WAREHOUSE`
- `INDUSTRIAL`
- `GARAGE`
- `NATUREFOREST`

### Onboard Camera Capture

The onboard camera system is configurable from YAML.

### Current status:

- RGB capture works
- Depth capture tested
- Segmentation capture tested
- Camera disabled by default
- Camera enabled explicitly from YAML
- Outputs use repo-relative paths such as:
- outputs/camera_capture/


### Gate-Passing Logger

The repository includes sequential gate-passing detection.

Current status:

- Gate-pass events detected
- Gate-pass events logged to CSV
- Lap completion detected
- Outputs use repo-relative paths such as:

```text
outputs/gate_logs/
```

### UZH/RPG-Inspired Tracks

Approximate configurable YAML templates were added for:

- SplitS
- Figure 8
- Kidney

These are clearly documented as inspired templates, not official UZH/RPG reproductions.

### Important Limitations

- Flightmare must be installed separately
- Flightmare Unity renderer binaries are not included
- Headless RL training is not included in this repo
- Trained models are not included
- Current examples use scripted trajectory playback, not learned control
- UZH-inspired tracks are approximate configurable templates, not official coordinates
- ROS 2/Gazebo sim-to-real work remains a later phase

### Next Milestones

- Connect trained policies from Mode A to Mode B visualization
- Visualize PPO policy rollouts in Unity
- Add more configurable racing tracks
- Add standardized trajectory playback format
- Add comparison between scripted and learned trajectories
- Add cleaner camera dataset export format
- Prepare future ROS 2/Gazebo integration phase

## Flightmare Headless RL Wrapper Completed

### Repository

`flightmare-headless-rl-wrapper`

### Status

`v0.1.0 stable baseline ready for first public push`

### Purpose

This repository contains the first completed technical contribution of the thesis pipeline: a modern headless reinforcement learning wrapper for Flightmare-based quadrotor training.

The repo is separate from the main thesis hub and separate from Unity visualization work.

### Technical Environment

- Ubuntu 22.04
- Python 3.10
- RL environment: `~/rl_lab/rl_env`
- Simulator backend: Flightmare
- RL tools: Stable-Baselines3, PyTorch, Gymnasium, RLlib/Ray
- Unity rendering: not used in this repo
- ROS 2: not required for this repo

### Completed Technical Progress

- Built and tested Flightmare locally on Ubuntu 22.04
- Configured modern Python 3.10 RL environment
- Tested basic RL tools such as Gymnasium, SB3, RLlib/Ray and PyTorch
- Created raw Flightmare vector wrapper
- Created Gymnasium-compatible single-environment wrapper
- Created SB3-compatible VecEnv wrapper
- Created scaled-action SB3 VecEnv wrapper
- Connected Flightmare's native 100 parallel quadrotor environments to SB3 PPO
- Verified editable install using `pip install -e .`
- Verified `flightgym` import
- Verified raw wrapper smoke test
- Verified scaled SB3 VecEnv smoke test
- Completed PPO vectorized headless training
- Completed PPO headless evaluation
- Completed action-scale ablation for ±0.2, ±0.3, ±0.4 and ±0.5

### Latest PPO Evaluation Result

| Metric | Value |
|---|---:|
| Mean reward | 2.5187 |
| Reward std | 0.0925 |
| Mean episode length | 36.1 |

### Best Current Action Scale

The best current scaled-action result is:

```text
Internal Flightmare action range: ±0.5
```

### Known Limitation

The current Flightmare Python binding exposes full-vector reset only.

It does not currently expose:

```python
reset_one(env_index)
```

Because of this, the current SB3 VecEnv wrapper uses a global-reset strategy. If any internal environment terminates, all 100 environments are marked done and reset together.

### Next Milestones

- Add argparse support for training and evaluation scripts
- Add configurable output directories and model paths
- Add CSV logging for evaluation results
- Add more PPO training benchmarks
- Investigate per-environment reset support through Flightmare C++/pybind
- Later connect trained policy visualization through a separate Unity visualization workflow


### Completed Technical Progress

- Built and tested Flightmare locally on Ubuntu 22.04
- Configured modern Python 3.10 RL environment
- Tested basic RL tools such as Gymnasium, SB3, RLlib/Ray and PyTorch
- Created raw Flightmare vector wrapper
- Created Gymnasium-compatible single-environment wrapper
- Created SB3-compatible VecEnv wrapper
- Created scaled-action SB3 VecEnv wrapper
- Connected Flightmare's native 100 parallel quadrotor environments to SB3 PPO
- Verified editable install using `pip install -e .`
- Verified `flightgym` import
- Verified raw wrapper smoke test
- Verified scaled SB3 VecEnv smoke test
- Completed PPO vectorized headless training
- Completed PPO headless evaluation
- Completed action-scale ablation for ±0.2, ±0.3, ±0.4 and ±0.5

### Latest PPO Evaluation Result

| Metric | Value |
|---|---:|
| Mean reward | 2.5187 |
| Reward std | 0.0925 |
| Mean episode length | 36.1 |

### Best Current Action Scale

The best current scaled-action result is:

```text
Internal Flightmare action range: ±0.5
```

## Known Limitation

The current Flightmare Python binding exposes full-vector reset only.

It does not currently expose:

```python
reset_one(env_index)
```

Because of this, the current SB3 VecEnv wrapper uses a global-reset strategy. If any internal environment terminates, all 100 environments are marked done and reset together.

## Next Milestones
- Add argparse support for training and evaluation scripts
- Add configurable output directories and model paths
- Add CSV logging for evaluation results
- Add more PPO training benchmarks
- Investigate per-environment reset support through Flightmare C++/pybind
- Later connect trained policy visualization through a separate Unity visualization workflow



## Initial Setup
## Profile and Thesis Repository Setup

### Completed

- Created GitHub profile README repository
- Created main thesis research repository
- Set up native Ubuntu 22.04 research system
- Installed ROS 2 Humble system-wide
- Installed Gazebo Fortress
- Configured Python RL environment
- Tested Gymnasium / SB3 / RLlib direction
- Tested PyBullet drone examples
- Built Flightmare successfully
- Verified Flightmare Python bindings
- Verified Flightmare Unity renderer and bridge tests
- Created public thesis research hub repository
- Pinned profile README repository
- Pinned thesis research repository
- Added thesis pipeline documentation
- Added Ubuntu 22.04 setup notes
- Added RL environment setup notes
- Added Flightmare setup notes
- Added Flightmare interface test summary
- Added PyBullet PID test summary

### Current Focus

- Organize public research documentation
- Prepare Flightmare modern Gymnasium wrapper
- Document PyBullet baseline experiments
- Document Flightmare setup and interface tests
The current focus is to make the GitHub profile credible and focused for robotics and DRL-based drone navigation research.

### Next Tasks

- Add Ubuntu 22.04 setup notes
- Add RL environment setup notes
- Add Flightmare setup notes
- Add PyBullet PID test summary
- Add thesis pipeline document
- Create `flightmare-gymnasium-wrapper`
- Add wrapper design documentation
- Create initial Gymnasium environment skeleton
- Add SB3 CartPole baseline result
- Add PyBullet RL baseline plan