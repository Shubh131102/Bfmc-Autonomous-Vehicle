# Autonomous Vehicle Platform (Bosch Future Mobility Challenge)

A small self-driving car built from the sensor mounts up: FEA-validated LiDAR and camera mounts, a ROS 2 navigation stack with CNN-based perception, and a live telemetry dashboard. Developed in Gazebo and transferred to the physical vehicle.

<p align="center">
  <img src="media/Screenshot%202025-08-23%20213924.png" alt="Gazebo simulation of the competition track with pedestrians and traffic signs" width="640">
</p>

## Results

| | |
|---|---|
| Sensor mount stability under vibration (FEA) | **Within 0.8 mm** |
| Traffic rule compliance | 85% across highway, ramps, roundabout, intersections, and pedestrian zones |
| Sign and pedestrian detection | 92% accuracy at 20 Hz |
| Deployment | Sim-to-real transfer from Gazebo to the car |

## Mechanical design

- LiDAR and camera mounts designed in SolidWorks
- ANSYS FEA under dynamic vibration loading to hold the sensors within 0.8 mm
- GD&T on critical datum features for sub-millimeter sensor alignment
- Laser-cut parts designed for easy cable routing and field service

## Autonomy stack

| Component | Approach |
|---|---|
| Lane following | Camera-based |
| Traffic lights and signs | CNN classification |
| Pedestrians | Camera and LiDAR detection |
| Planning | Shortest-path route plus rule-aware behavior |
| Simulation | Gazebo competition track |

## Telemetry dashboard

<p align="center">
  <img src="media/Image.jpeg" alt="Web dashboard showing speed, steering angle, battery, and driving mode" width="520">
</p>

Live view of speed, steering angle, battery, driving mode (manual, auto, legacy), camera feed, and CPU and memory use.

## What's in this repo

| Path | Contents |
|---|---|
| `launch/bfmc_sim.launch.py` | Simulation launch file |
| `docker/` | Dockerfile, compose file, and entrypoint for a reproducible setup |
| `requirements.txt` | Python dependencies |
| `media/` | Simulation and dashboard screenshots |

## Quick start

```bash
cd docker && docker compose up --build
# or, in a ROS 2 workspace:
pip install -r requirements.txt
ros2 launch launch/bfmc_sim.launch.py
```

## License

MIT
