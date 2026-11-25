# DOC-Oc Continuum Arm

## Overview
DOC-Oc is a simulation and control framework for a tendon-driven continuum robotic arm, developed using MuJoCo. The project combines physics-based simulation, keyboard-driven actuation, kinematic estimation, and strain monitoring to explore the behaviour and control of a flexible robotic structure.

The arm is actuated through four tendons arranged around its central structure, enabling bending in different directions. The system provides an interactive environment for testing actuation patterns, observing deformation, and analysing the arm's motion before applying commands to the physical hardware.

## Features

- **Four-Tendon Actuation:** Uses four tendons (`px`, `nx`, `py`, `ny`) to control bending along the X and Y axes.
- **Interactive Control:** Keyboard-based control allows users to incrementally actuate individual tendons, with repeated actuation while keys are held.
- **MuJoCo Simulation:** Simulates the arm's physical behaviour and provides a real-time visualisation of its deformation and movement.
- **Kinematic Estimation:** Implements a Piecewise/Constant Curvature (PCC) model to estimate the arm's configuration from tendon measurements.
- **Real-Time Measurements:** Tracks the end-effector position, tendon lengths, bending parameters, and central-wire measurements.
- **Strain Monitoring:** Estimates tensile strain in the central Nitinol wires and monitors the arm for potentially unsafe deformation.
- **Safety Mechanism:** Implements a strain-based safety lock to prevent further actuation when predefined strain thresholds are exceeded.
- **Hardware Integration:** The combined controller supports Wi-Fi UDP communication with the physical arm, allowing simulation controls to be translated into hardware commands.

## Architecture

The project is organised into separate components for simulation, control, measurement, and kinematic analysis:

- **Controller:** Handles keyboard inputs, tendon actuation, simulation interaction, and communication with the physical hardware.
- **Measurement Module:** Extracts simulation data, including end-effector position, tendon lengths, and central-wire lengths.
- **Kinematics Module:** Uses tendon geometry and a Jacobian-based least-squares approach to estimate curvature, axial strain, bending direction, bending angle, and tip position.
- **Robot Model:** Contains the MuJoCo model and geometric representation of the continuum arm.
- **Configuration:** Stores the parameters required to configure the robot and simulation.

## Controls

| Key | Action |
|---|---|
| W / S | Bend along positive / negative Y |
| A / D | Bend along negative / positive X |
| ESC | Exit the controller |

## Project Structure

- `meshes/` – Geometric assets.
- `model/` – MuJoCo robot model.
- `parameters/` – Configuration and robot parameters.
- `src/` – Control, measurement, and kinematics modules.

## Technologies

Python, MuJoCo, NumPy, PyYAML, and pynput.

DOC-Oc serves as a development platform for experimenting with continuum robotics, tendon-based actuation, deformation estimation, and the integration of simulation with physical robotic systems.


## Requirements

Need to setup a environment that has mujoco 3.17.0 ,Numy,Python,pynput

## Note

the files need to be launched as a module since this follows standalone files architecture
