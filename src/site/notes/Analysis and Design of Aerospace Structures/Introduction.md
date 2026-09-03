---
{"dg-publish":true,"permalink":"/analysis-and-design-of-aerospace-structures/introduction/","tags":["aerospace-engineering","structural-analysis","mechanics-of-materials"],"noteIcon":"","dg-note-properties":{"tags":["aerospace-engineering","structural-analysis","mechanics-of-materials"],"type":"lecture-note","status":"active"}}
---


# EAS 4200: Analysis & Design of Aerospace Structures

> [!info] Course Overview & Assessments
> **Section:** 0001  
> **Course Work:** Homework assignments, reading quizzes, midterm exams, term project, and final exam.

---

## 1. Structural Analysis Overview

Structural analysis evaluates how a physical structure responds to applied external forces and moments using three primary interconnected concepts: **displacement**, **strain**, and **stress**.

### Core Analytical Process
$$\text{Forces \& Moments} \longrightarrow \text{Stress} \longrightarrow \text{Strain} \longrightarrow \text{Displacement}$$

Governing equations link these fundamental quantities, allowing for precise structural analysis and safety verification.

---

## 2. Aerospace Structures & Design Constraints

Aerospace engineering relies heavily on **weight-critical design**—structures must withstand demanding flight loads while minimizing overall structural mass.

### Thin-Walled Structures & Plane Stress
To achieve weight efficiency, aircraft and spacecraft predominantly utilize **thin-walled structures** (e.g., skins, webs, spars).

> [!exam] High Priority Exam Topic
> **Plane Stress** will be explicitly tested on the exam!

Thin-walled structures are typically modeled as **plane-stress** problems because stresses through the thin thickness dimension are negligible compared to in-plane stresses.

* **Example:** If the component is ultra-thin in the $x$-direction:
$$\sigma_x = 0, \qquad \tau_{xy} = 0, \qquad \tau_{xz} = 0$$

---

## 3. General 3D State of Stress & Strain

A general three-dimensional body experiencing loading involves **15 unknown quantities**:

| Category | Count | Quantities |
| :--- | :---: | :--- |
| **Displacements** | 3 | $u, v, w$ (one for each axis $x, y, z$) |
| **Strains** | 6 | 3 Normal ($\epsilon_x, \epsilon_y, \epsilon_z$) + 3 Shear ($\gamma_{xy}, \gamma_{yz}, \gamma_{xz}$) |
| **Stresses** | 6 | 3 Normal ($\sigma_x, \sigma_y, \sigma_z$) + 3 Shear ($\tau_{xy}, \tau_{yz}, \tau_{xz}$) |

---

## 4. Fundamental Field Quantities

### A. Displacement
**Displacement** defines the spatial movement vector $\mathbf{u}(P)$ of a material point $P$ transitioning from its original undeformed configuration to its deformed position $P'$.

```mermaid
graph LR
    A[Original Point P] -- "Displacement Vector u(P)" --> B[Deformed Point P']
````

### B. Stress

**Stress** describes internal forces developed per unit area ($\Delta A$) inside a structural body.

Code snippet

```
graph TD
    Force["Resultant Force Vector (ΔP)"] --> Normal["Normal Component (ΔPn)"]
    Force --> Shear["Shear Component (ΔPs)"]
    
    Normal --> Sig["Normal Stress (σ)"]
    Shear --> Tau["Shear Stress (τ)"]
```

#### Stress Limits & Equations

- **Normal Stress ($\sigma$):** Acts perpendicular to the differential surface area.
    
    $$\sigma = \lim_{\Delta A \to 0} \frac{\Delta P_n}{\Delta A}$$
    
- **Shear Stress ($\tau$):** Acts parallel (tangential) to the differential surface area.
    
    $$\tau = \lim_{\Delta A \to 0} \frac{\Delta P_s}{\Delta A}$$
    
- **Total Resultant Stress Magnitude ($t$):**
    
    $$t = \sqrt{\sigma^2 + \tau^2}$$
    

> [!note] Sign & Subscript Conventions
> 
> - **Normal Stress ($\sigma$):** Positive in **tension** (acting away from face); negative in **compression** (acting toward face).
>     
> - **Shear Stress ($\tau_{ij}$):** First subscript $i$ indicates the direction of the force; second subscript $j$ identifies the normal vector of the face.
>     

#### Complementary Shear Stresses

Rotational moment equilibrium on a differential element demands that shear stresses occur in equal, paired sets:

$$\tau_{xy} = \tau_{yx}, \qquad \tau_{xz} = \tau_{zx}, \qquad \tau_{yz} = \tau_{zy}$$

### C. Strain

**Strain** quantifies the local deformation and relative change in geometry of a body under load.

- **Engineering Normal Strain ($\epsilon$):**
    
    $$\epsilon = \frac{\Delta L}{L_0} = \frac{\text{Change in Length}}{\text{Original Length}}$$
    
- **Strain at a Point:** Evaluating the deformation limit as initial length approaches zero:
    
    $$\epsilon = \lim_{L_0 \to 0} \frac{\Delta L}{L_0}$$
    
- **Normal Strains in 3D:** $\epsilon_x, \epsilon_y, \epsilon_z$
    

> [!warning] Key Kinematic Assumptions
> 
> Classical linear structural mechanics assumes **small displacements** and **small rotation angles** ($\sin\theta \approx \theta$).

## 5. Equilibrium of a Differential Element

To establish governing field equilibrium equations, consider a small cubic element with dimensions $dx \times dy \times dz$.

Code snippet

```
graph TD
    Step1["1. Draw stress states on negative faces"] --> Step2["2. Apply 1st-order Taylor Expansion to positive faces"]
    Step3["3. Include external body forces (e.g., gravity)"] --> Step4["4. Apply ∑F = 0 and ∑M = 0 balance"]
    Step2 --> Step3
```

### 1D Stress Variation Example

If normal stress $\sigma_x$ varies continuously across an element of width $dx$, the stress acting on the positive face at position $(x + dx)$ is modeled using a **Taylor series expansion**:

$$\sigma_x(x + dx) \approx \sigma_x(x) + \frac{\partial \sigma_x}{\partial x} dx$$

_(Where $\frac{\partial \sigma_x}{\partial x} dx$ represents the incremental linear stress variation across the spatial domain)._