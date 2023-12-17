[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Poetry](https://img.shields.io/endpoint?url=https://python-poetry.org/badge/v0.json)](https://python-poetry.org/)

# Path Tracking Catalog
25 path-tracking algorithms are (goint to be) implemented with python.

- [Vehicle Models for Simulation](#vehicle-models-for-simulation)
  - [x] [Dynamic Bicycle Model](#dynamic-bicycle-model)
  - [x] [Kinematic Bicycle Model](#kinematic-bicycle-model)
  - [x] [Unicycle Model](#unicycle-model)
- [Control Algorithms](#control-algorithms)
  - [x] [Bang-Bang Control](#bang-bang-control)
  - [x] [PID Control](#pid-control)
  - [x] [Pure Pursuit Control](#pure-pursuit-control)
  - [x] [Stanley Control](#stanley-control)
  - [x] [Fuzzy Logic Control](#fuzzy-logic-control)
  - [ ] Genetic Algorithm
  - [x] [Dynamic Window Approach](#dynamic-window-approach)
  - [ ] State Lattice Planner
  - [x] [State Feedback Control](#state-feedback-control)
  - [x] [Linear Quadratic Regulator (infinite horizon)](#linear-quadratic-regulator)
  - [ ] Linear Quadratic Regulator (finite horizon)
  - [ ] Differential Dynamic Programming (infinite horizon)
  - [ ] Differential Dynamic Programming (finite horizon)
  - [ ] Iterative LQR (infinite horizon)
  - [ ] Iterative LQR (finite horizon)
  - [ ] Linear Model Predictive Control (formulated as Quadratic Programming)
  - [ ] Nonlinear Model Predictive Control (solved by C/GMRES method)
  - [x] [Model Predictive Path-Integral Control](#model-predictive-path-integral-control)
  - [ ] Sliding Mode Control
  - [ ] Q-Learning
  - [ ] Multi Layer Perceptron
  - [ ] Linear Quadratic Gaussian
  - [ ] H∞ Control (LMI)
  - [ ] Lyapunov
  - [ ] Adaptive Control

## Setup
```sh
git clone https://github.com/MizuhoAOKI/path_tracking_catalog.git
cd path_tracking_catalog
poetry install
```

## Vehicle Models for Simulation

### Definition of Coordinate Systems
<img src="./media/def_of_frames.svg" width="500px" alt="definition_of_frames">

### Dynamic Bicycle Model

```math
\begin{align}
&\frac{\mathrm{d}}{\mathrm{d}t}
\begin{bmatrix}
p^G_x \\
p^G_y \\
\phi \\
v^B_x \\
v^B_y \\
\omega \\
\end{bmatrix}
=
\begin{bmatrix}
v^B_x \cos\phi - v^B_y \sin\phi \\
v^B_x \sin\phi + v^B_y \cos\phi \\
\omega \\
{a}\cos\beta - (F_{f}^{\rm{lat}}\sin {{\delta}})/m + v^B_y \omega \\
{a}\sin\beta + F_{r}^{\rm{lat}}/m + F_{f}^{\rm{lat}} \cos{\delta}/m - v^B_x \omega \\
(F_{f}^{\rm{lat}}l_f\cos{\delta} - F_{r}^{\rm{lat}}l_r)/I_z\
\end{bmatrix}, \\ \\
& F_{f}^{\rm{lat}} = - C_f \left( \frac{v^B_y + l_f \omega}{v^B_x} - {\delta} \right), \\ \\
& F_{r}^{\rm{lat}} = - C_r \left( \frac{v^B_y - l_r \omega}{v^B_x} \right), \\ \\
& \beta = \tan^{-1} \left( \frac{v^B_y}{v^B_x} \right) \approx \frac{v^B_y}{v^B_x} \ \ \  (\because v^B_y \ll v^B_x ).
\end{align}
```
<p align="center">
<img src="./media/DBM.svg" width="500px" alt="DBM" />
</p>

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/d51c3821-9b35-4e91-8235-e63b18f33f03

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/dynamic_bicycle_model.ipynb
```

### Kinematic Bicycle Model

```math
\begin{align}
& \frac{\mathrm{d}}{\mathrm{d}t}
\begin{bmatrix}
p^G_x \\
p^G_y \\
\phi \\
V
\end{bmatrix}
=
\begin{bmatrix}
V \cos(\phi + \beta) \\
V \sin(\phi + \beta) \\
(V/l_r)  \sin\beta \\
{a}
\end{bmatrix},\\ \\
& \beta = \tan^{-1} \left( \frac{l_r}{l_f + l_r} \tan({\delta}) \right).
\end{align}
```

<p align="center">
<img src="./media/KBM.svg" width="500px" alt="KBM" />
</p>

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/b85fe31c-3e4a-47a9-bc54-694cde225bd5

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/kinematic_bicycle_model.ipynb
```

### Unicycle Model

```math
\begin{align}
\frac{\mathrm{d}}{\mathrm{d}t}
\begin{bmatrix}
p^G_x \\
p^G_y \\
\phi \\
V
\end{bmatrix}
=
\begin{bmatrix}
V \cos\phi \\
V \sin\phi \\
( V / l ) \tan{\delta} \\
{a}
\end{bmatrix}.
\end{align}
```

<p align="center">
<img src="./media/UM.svg" width="500px" alt="UM" />
</p>

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/8cba0010-6a21-4830-8974-b4b57c166bcf

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/unicycle_model.ipynb
```

## Control Algorithms
### Bang-Bang Control

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/cc88214e-3914-4126-ac57-3f63d8397094

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/bangbang.ipynb
```

### PID Control

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/83e813d9-b611-49da-abe2-45333bfb80d2

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/pid.ipynb
```

### Pure-Pursuit Control

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/a23f8437-d695-4848-83fb-a8424f311683

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/purepursuit.ipynb
```

### Stanley Control

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/43f3ce4f-8181-45ad-bc08-ac96f3a91e2b

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/stanley.ipynb
```

### Fuzzy Logic Control

https://github.com/MizuhoAOKI/path_tracking_catalog/assets/63337525/d8f9f256-4b2c-4b9e-8b57-e33f05e59e6f

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/fuzzy.ipynb
```

### Dynamic Window Approach

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/dwa_pathtracking.ipynb
```

### State Lattice Planner


### State Feedback Control

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/8e48380b-f840-49cc-91e0-07dad356b5be

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/state_feedback.ipynb
```

### Linear Quadratic Regulator

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/13d6abbc-2904-422d-acba-17ede074a181

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/lqr.ipynb
```

### Model Predictive Control


### Model Predictive Path-Integral Control

https://github.com/MizuhoAOKI/path_tracking_catalog/assets/63337525/acfefe3a-a22a-4cbc-a5c8-a83086943684

```sh
cd path_tracking_catalog
poetry run jupyter notebook notebooks/mppi_pathtracking.ipynb
```

### Sliding Mode Control


### Q-Learning

