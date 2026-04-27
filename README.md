# 🤖 Glass Cleaning Robot Arm

A simulation model of an autonomous glass-cleaning robot arm that replicates real-world window cleaning actions. This project integrates **SolidWorks** for mechanical design and **MATLAB/Simulink** with **Simscape Multibody** for dynamics simulation and motion control.

---

## 📁 Project Structure

| File/Folder | Description |
|-------------|-------------|
| `DOF2_test.slx` | Main Simulink model — load this first to set up the model workspace |
| `assem1.m` | MATLAB script to generate the Rigid Body Tree from the SolidWorks assembly |
| `Selected_Area_Cleaning/` | Simulink model for targeted area cleaning using Inverse Kinematics |
| `Rotational_Cleaning/` | Simulink model for full rotational cleaning motion |

---

## 🔧 Getting Started

```
(1) Open DOF2_test.slx and update it to the model workspace
(2) Run assem1.m to generate the Rigid Body Tree
(3) Open Selected_Area_cleaning.slx under the Selected Area Cleaning folder
(4) Wait for the simulation to complete
(5) In the input angle section, select the region (A, B, C, D...) and set the input_angle value accordingly
```

---

## 🪟 Cleaning Modes

### 1. Selected Area Cleaning

Forward and Inverse Kinematics blocks in MATLAB compute the required joint angles for the motor to reach a target position. The target is specified as an `(x, y)` coordinate matrix. Since IK computation takes time, the calculated joint angle matrix is saved and can be directly fed as input to the motors in subsequent runs — enabling faster real-time performance.

![Selected Area Cleaning](https://github.com/user-attachments/assets/fb7338c5-9a79-4ece-8fd6-51292ebf8674)

### 2. Rotational Cleaning

Two Signal Builder blocks drive the two cleaning arms in coordinated rotational motion to ensure complete surface coverage across the cleaning zone.

![Rotational Cleaning](https://github.com/user-attachments/assets/a4a7964a-569b-4fc3-9155-cc96bc81f95e)

---

## 🖥️ Simulink Models

**Inverse / Forward Kinematics Model**

<img src="https://github.com/user-attachments/assets/b8e872d3-bcc4-48d6-beb8-547c682c23fc" alt="Kinematics Model" width="400"/>

**Glass Cleaning Arm Model**

<img src="https://github.com/user-attachments/assets/c77447f3-1899-48b2-8d01-c1a5d8e0e42c" alt="Glass Cleaning Arm" width="400"/>

**SolidWorks Design**

<img src="https://github.com/user-attachments/assets/5d04d014-d32c-467f-8374-2f70d3e43ce5" alt="SolidWorks Drawing" width="400"/>

---

## 🛠️ Tech Stack

| Component | Tool |
|-----------|------|
| Mechanical Design | SolidWorks |
| Dynamics Simulation | MATLAB Simulink, Simscape Multibody |
| Motion Planning | Inverse Kinematics, Robotic System Toolbox |
| Trajectory Generation | MATLAB Signal Builder, Robotic System Toolbox |
| Image Processing | MATLAB Image Processing Toolbox |

---

## ⚙️ System Design

- **5 rigid body subsystems** (rods, motors, suction cups) interconnected via revolute joints in Simscape Multibody
- **8 predefined cleaning zones** (A–H) with pre-computed IK matrices for real-time motion
- **Optical sensors** for dirt detection; joint angles adjusted autonomously based on detected contamination
- **Proximity sensors** for obstacle avoidance and path verification
- **Suction cups** with vacuum pumps for stable adhesion to glass surfaces
