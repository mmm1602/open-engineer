---
{"dg-publish":true,"permalink":"/analysis-and-design-of-aerospace-structures/lecture-notes/","tags":["aerospace-engineering","structural-analysis","mechanics-of-materials","course-notes"],"noteIcon":"","dg-note-properties":{"tags":["aerospace-engineering","structural-analysis","mechanics-of-materials","course-notes"],"type":"lecture-note","status":"active"}}
---


# Analysis & Design of Aerospace Structures

> [!info] Course Framework
> **Core Objective:** Connect applied forces & moments to displacements using the governing equations of continuum mechanics:
> $$\text{Forces \& Moments} \longrightarrow \text{Stress} \longrightarrow \text{Strain} \longrightarrow \text{Displacement}$$

---

## 1. Fundamentals of Continuum Mechanics

### Governing System of Equations
A complete 3D structural analysis involves **15 unknown field variables** solved using **15 field equations**:

```mermaid
graph TD
    Unk["15 Unknowns"] --> Disp["3 Displacements (u, v, w)"]
    Unk --> Str["6 Strains (3 Normal, 3 Shear)"]
    Unk --> Strs["6 Stresses (3 Normal, 3 Shear)"]

    Eq["15 Equations"] --> EqEq["3 Equilibrium Equations (Forces/Moments)"]
    Eq --> KinEq["6 Kinematic Equations (Strain-Displacement)"]
    Eq --> ConEq["6 Constitutive Equations (Stress-Strain)"]
````

### Plane Stress Assumption (Thin-Walled Structures)

Aerospace structures rely heavily on **weight-critical design**, leading to thin-walled structural members.

> [!exam] Key Assumption: Plane Stress
> 
> If a structure is thin along the $z$-direction, stresses through the thickness are negligible:
> 
> $$\sigma_z \approx 0, \qquad \tau_{xz} \approx 0, \qquad \tau_{yz} \approx 0$$

## 2. Displacements, Stresses & Strains

### A. Displacement Vector

Displacement describes the spatial shift of a material point $P(x,y,z)$ to a deformed location $P'$:

$$\mathbf{u} = u\hat{i} + v\hat{j} + w\hat{k}$$

Where $u, v, w$ are the displacement components along the $x, y, z$ axes respectively.

### B. Stress Tensor & Definitions

Stress represents internal force per unit area ($\text{Pressure} = \text{Force}/\text{Area}$):

- **Normal Stress ($\sigma$):** Force component perpendicular to the face.
    
    $$\sigma = \lim_{\Delta A \to 0} \frac{\Delta P_n}{\Delta A}$$
    
- **Shear Stress ($\tau$):** Force component parallel to the face.
    
    $$\tau = \lim_{\Delta A \to 0} \frac{\Delta P_s}{\Delta A}$$
    
- **Total Resultant Stress ($t$):**
    
    $$t = \sqrt{\sigma^2 + \tau^2}$$
    

#### Sign Conventions & Index Rules

- **First Subscript:** Specifies the face normal vector direction.
    
- **Second Subscript:** Specifies the direction of the stress vector.
    
- **Positive Faces:** Positive stress acts in the positive coordinate direction on a positive face.
    

#### Complementary Shear Stresses (Moment Equilibrium)

To maintain local rotational equilibrium:

$$\tau_{xy} = \tau_{yx}, \qquad \tau_{xz} = \tau_{zx}, \qquad \tau_{yz} = \tau_{zy}$$

### C. Strain Definitions & Kinematics

#### 1. Normal Strain ($\epsilon$)

Measures fractional change in length (unitless):

$$\epsilon = \frac{A'B' - AB}{AB} = \frac{\Delta L}{L}$$

- **Point Normal Strains:**
    
    $$\epsilon_x = \frac{\partial u}{\partial x}, \qquad \epsilon_y = \frac{\partial v}{\partial y}, \qquad \epsilon_z = \frac{\partial w}{\partial z}$$
    

#### 2. Shear Strain ($\gamma$)

Measures the change in angle between two perpendicular lines (in radians):

$$\gamma_{xy} = \gamma_{yx} = \theta_1 + \theta_2$$

Assuming **small displacements and small angles** ($\theta_1 \approx \sin\theta_1 = \frac{\partial v}{\partial x}$):

$$\gamma_{xy} = \frac{\partial v}{\partial x} + \frac{\partial u}{\partial y}$$

$$\gamma_{xz} = \frac{\partial w}{\partial x} + \frac{\partial u}{\partial z}$$

$$\gamma_{yz} = \frac{\partial w}{\partial y} + \frac{\partial v}{\partial z}$$

### D. Compatibility Equations

Since the 6 strain components are derived from only 3 displacement functions $(u,v,w)$, they cannot vary independently. They must satisfy continuous deformation conditions so no gaps/voids form in the material.

- **Primary 2D Compatibility Example:**
    
    $$\frac{\partial^2 \gamma_{xy}}{\partial x \partial y} = \frac{\partial^2 \epsilon_y}{\partial x^2} + \frac{\partial^2 \epsilon_x}{\partial y^2}$$
    

### E. Special Deformation Modes

- **Pure Rigid Body Translation:** Strains $\epsilon = 0, \gamma = 0$ ($u = \text{const}, v = \text{const}$).
    
- **Pure Rigid Body Rotation:** Strains $\epsilon = 0, \gamma = 0$ ($u = -\alpha y, v = \alpha x$).
    
- **Pure Shear:** $\epsilon_x = \epsilon_y = 0$, but $\gamma_{xy} \neq 0$ (no volume change in 2D).
    
- **Volumetric Strain ($e$):**
    
    $$e = \frac{\Delta V}{V} = \epsilon_x + \epsilon_y + \epsilon_z$$
    

## 3. Equilibrium Equations of a Differential Element

Balancing differential forces on an element $dx \times dy \times dz$ including body forces $(X, Y, Z)$ using 1st-order Taylor Series expansion:

$$\frac{\partial \sigma_x}{\partial x} + \frac{\partial \tau_{yx}}{\partial y} + \frac{\partial \tau_{zx}}{\partial z} + X = 0$$

$$\frac{\partial \tau_{xy}}{\partial x} + \frac{\partial \sigma_y}{\partial y} + \frac{\partial \tau_{zy}}{\partial z} + Y = 0$$

$$\frac{\partial \tau_{xz}}{\partial x} + \frac{\partial \tau_{yz}}{\partial y} + \frac{\partial \sigma_z}{\partial z} + Z = 0$$

## 4. Constitutive Relations (Hooke's Law)

### Isotropic 3D Stress-Strain Relationships

Using Young's Modulus ($E$), Shear Modulus ($G$), and Poisson's Ratio ($\nu$):

$$\epsilon_x = \frac{1}{E}\left[\sigma_x - \nu(\sigma_y + \sigma_z)\right]$$

$$\epsilon_y = \frac{1}{E}\left[\sigma_y - \nu(\sigma_x + \sigma_z)\right]$$

$$\epsilon_z = \frac{1}{E}\left[\sigma_z - \nu(\sigma_x + \sigma_y)\right]$$

$$\tau_{xy} = G \gamma_{xy}, \qquad \tau_{yz} = G \gamma_{yz}, \qquad \tau_{xz} = G \gamma_{xz}$$

Where the **Shear Modulus** is defined as:

$$G = \frac{E}{2(1+\nu)}$$

### Matrix Forms

#### Compliance Matrix (Strains from Stresses):

$$\begin{Bmatrix} \epsilon_x \\ \epsilon_y \\ \epsilon_z \end{Bmatrix} = \frac{1}{E} \begin{bmatrix} 1 & -\nu & -\nu \\ -\nu & 1 & -\nu \\ -\nu & -\nu & 1 \end{bmatrix} \begin{Bmatrix} \sigma_x \\ \sigma_y \\ \sigma_z \end{Bmatrix}$$

$$\begin{Bmatrix} \gamma_{yz} \\ \gamma_{xz} \\ \gamma_{xy} \end{Bmatrix} = \frac{1}{G} \begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} \begin{Bmatrix} \tau_{yz} \\ \tau_{xz} \\ \tau_{xy} \end{Bmatrix}$$

#### Stiffness Matrix for Plane Stress ($\sigma_z = 0$):

$$\begin{Bmatrix} \sigma_x \\ \sigma_y \end{Bmatrix} = \frac{E}{1-\nu^2} \begin{bmatrix} 1 & \nu \\ \nu & 1 \end{bmatrix} \begin{Bmatrix} \epsilon_x \\ \epsilon_y \end{Bmatrix}, \qquad \tau_{xy} = G \gamma_{xy}$$

#### Hydrostatic Pressure & Bulk Modulus

Under uniform hydrostatic stress ($\sigma_x = \sigma_y = \sigma_z = -P$):

$$e = -\frac{3(1-2\nu)}{E} P \implies P = -K e$$

$$\text{Bulk Modulus } K = \frac{E}{3(1-2\nu)}$$

## 5. Stress & Strain Transformations

Changing coordinate axes does not change actual physical forces or stresses—it only alters their mathematical components.

Code snippet

```
graph LR
    SystemA["Standard Coordinates (x, y)"] -- "Rotation Angle θ" --> SystemB["Rotated Coordinates (x', y')"]
```

### Transformation Equations (Angle $\theta$)

$$\sigma_x' = \frac{\sigma_x + \sigma_y}{2} + \frac{\sigma_x - \sigma_y}{2}\cos 2\theta + \tau_{xy}\sin 2\theta$$

$$\tau_{x'y'} = -\frac{\sigma_x - \sigma_y}{2}\sin 2\theta + \tau_{xy}\cos 2\theta$$

_(Strain equations follow identical forms by substituting $\sigma \to \epsilon$ and $\tau \to \frac{\gamma}{2}$)_

## 6. Principal Stresses & Mohr's Circle

### Principal Planes & Stresses

Principal planes are orientations where **shear stress is zero** ($\tau = 0$), leaving only extreme normal stresses:

$$\tan 2\theta_p = \frac{2\tau_{xy}}{\sigma_x - \sigma_y}$$

$$\sigma_{\text{I}, \text{II}} = \frac{\sigma_x + \sigma_y}{2} \pm \sqrt{\left(\frac{\sigma_x - \sigma_y}{2}\right)^2 + \tau_{xy}^2}$$

### Maximum In-Plane Shear Stress

Maximum shear occurs at planes oriented **$45^\circ$ away** from principal planes:

$$\tau_{\max} = \pm \sqrt{\left(\frac{\sigma_x - \sigma_y}{2}\right)^2 + \tau_{xy}^2} = \frac{\sigma_{\text{I}} - \sigma_{\text{II}}}{2}$$

### Step-by-Step Construction of 2D Mohr's Circle

Code snippet

```
graph TD
    P1["1. Plot Point A: (σ_x, τ_xy)"] --> P2["2. Plot Point B: (σ_y, -τ_xy)"]
    P2 --> P3["3. Connect A and B with a straight line"]
    P3 --> P4["4. Center = ((σ_x + σ_y)/2, 0)"]
    P4 --> P5["5. Draw circle with Diameter = AB"]
```

- **X-Axis Intersections:** Yield Principal Stresses $\sigma_{\text{I}}, \sigma_{\text{II}}$.
    
- **Peak Y-Values:** Yield Maximum Shear Stress $\tau_{\max}$.
    
- **3D Formulation (Eigenvalues):**
    
    $$[\sigma]\{n\} - S[I]\{n\} = \{0\} \implies \det([\sigma] - S[I]) = 0$$
    

## 7. St. Venant's Principle

> [!abstract] Principle Statement
> 
> Statically equivalent load distributions produce virtually identical stress distributions sufficiently far from the point of load application.

- Near local points of application, local stress distributions vary dramatically.
    
- Far from load application points, stresses smooth out to standard nominal values ($\sigma = \frac{P}{A}$).
    

## 8. Cross-Sectional & Geometric Properties

### A. Centroid ($\bar{x}, \bar{y}$)

The geometric center where the first moment of area equals zero:

$$\bar{x} = \frac{\int x \, dA}{\int dA} = \frac{\sum \bar{x}_i A_i}{\sum A_i}, \qquad \bar{y} = \frac{\int y \, dA}{\int dA} = \frac{\sum \bar{y}_i A_i}{\sum A_i}$$

> [!tip] Symmetry Shortcut
> 
> - If a section has **one axis of symmetry**, the centroid lies on that axis.
>     
> - If a section has **two axes of symmetry**, the centroid lies at their intersection.
>     

### B. Thin-Walled Idealization (Thin-Walled Approximations)

For thin structural sections where thickness $t \ll$ length $L$, centerline calculations simplify analysis without significant loss of accuracy (errors are typically $<1\%$).

#### Moments of Inertia for Thin Rectangular Segments ($b \times t$):

|**Orientation**|**Ixx​**|**Iyy​**|**Ixy​**|
|---|---|---|---|
|**Horizontal ($b \parallel x, t \parallel y$)**|$\frac{1}{12} b t^3 \approx 0$|$\frac{1}{12} b^3 t$|$0$|
|**Vertical ($t \parallel x, b \parallel y$)**|$\frac{1}{12} b^3 t$|$\frac{1}{12} b t^3 \approx 0$|$0$|

#### Parallel Axis Theorem:

$$I_{xx} = \bar{I}_{xx} + A d_y^2, \qquad I_{yy} = \bar{I}_{yy} + A d_x^2, \qquad I_{xy} = \bar{I}_{xy} + A d_x d_y$$