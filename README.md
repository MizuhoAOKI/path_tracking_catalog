# Path Tracking
Several path-tracking algorithms are (going to be) implemented with python.


## Vehicle Models for Simulation

### Definition of Coordinate Systems
<img src="./media/def_of_frames.svg" width="500px" alt="definition_of_frames">

### Dynamic Bicycle Model

$$
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
\bm{a}\cos\beta - (F_{f}^{\rm{lat}}\sin {\bm{\delta}})/m + v^B_y \omega \\
\bm{a}\sin\beta + F_{r}^{\rm{lat}}/m + F_{f}^{\rm{lat}} \cos\bm{\delta}/m - v^B_x \omega \\
(F_{f}^{\rm{lat}}l_f\cos\bm{\delta} - F_{r}^{\rm{lat}}l_r)/I_z\
\end{bmatrix}, \\ \\
& F_{f}^{\rm{lat}} = - C_f \left( \frac{v^B_y + l_f \omega}{v^B_x} - \bm{\delta} \right), \\ \\
& F_{r}^{\rm{lat}} = - C_r \left( \frac{v^B_y - l_r \omega}{v^B_x} \right), \\ \\
& \beta = \tan^{-1} \left( \frac{v^B_y}{v^B_x} \right) \approx \frac{v^B_y}{v^B_x} \ \ \  (\because v^B_y \ll v^B_x ).
\end{align}
$$

<img src="./media/DBM.svg" width="500px" alt="DBM" />

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/d51c3821-9b35-4e91-8235-e63b18f33f03

```sh
cd path_tracking
poetry run jupyter notebook notebooks/dynamic_bicycle_model.ipynb
```

### Kinematic Bicycle Model

$$
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
\bm{a}
\end{bmatrix},\\ \\
& \beta = \tan^{-1} \left( \frac{l_r}{l_f + l_r} \tan(\bm{\delta}) \right).
\end{align}
$$

<img src="./media/KBM.svg" width="500px" alt="KBM" />

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/b85fe31c-3e4a-47a9-bc54-694cde225bd5

```sh
cd path_tracking
poetry run jupyter notebook notebooks/kinematic_bicycle_model.ipynb
```

### Unicycle Model

$$
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
( V / l ) \tan\bm{\delta} \\
\bm{a}
\end{bmatrix}.
\end{align}
$$

<img src="./media/UM.svg" width="500px" alt="UM" />

https://github.com/MizuhoAOKI/path_tracking/assets/63337525/8cba0010-6a21-4830-8974-b4b57c166bcf

```sh
cd path_tracking
poetry run jupyter notebook notebooks/unicycle_model.ipynb
```

## Control Algorithms
### PID Control


### Pure-Pursuit Control


### Stanley Control


### Dynamic Window Approach


### State Feedback Control


### Linear Quadratic Regulator


### Model Predictive Control


### Model Predictive Path-Integral Control


### Sliding Mode Control


### Q-Learning

