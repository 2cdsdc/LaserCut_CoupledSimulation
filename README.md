# 🔥 Coupled Transient Thermal & Structural Analysis of Laser Cutting  
> Simulated using ANSYS Workbench 2024 R1

## 📌 Overview

This repository contains a **multi-physics simulation** of a laser cutting process where **transient thermal analysis** is coupled with **structural stress analysis**. The project explores how localized, high-temperature heat input (simulating a laser beam) induces temperature gradients, thermal strain, and mechanical deformation in a metallic part.

---

## 🎯 Objectives

- Model a realistic laser cutting condition with a moving thermal source
- Analyze transient temperature propagation in a steel body
- Study resulting thermo-mechanical stress and strain behavior
- Evaluate deformation, residual stress, and potential failure regions

---

## ⚙️ Simulation Setup

### 🔹 Geometry

- Imported via DesignModeler from a parametric `.pmdb` file
- Model Dimensions:
  - X: 20 mm, Y: 2 mm, Z: 16.5 mm
  - Volume: ~6.6e-7 m³
  - Total parts: 12 solid bodies (meshed)

### 🔹 Material

- **Structural Steel**
- Properties:
  - Nonlinear behavior enabled
  - Thermal strain effects activated
  - Temperature-dependent properties used
- Reference Temperature: 22 °C

---

## 🔥 Transient Thermal Analysis

- Duration: 10 seconds
- Time steps: 10 (1s each)
- Max simulated temperature: **165.14 °C**
- Boundary condition: Imported Body Temperature from another thermal simulation
- Temperature mapping:
  - Volumetric interpolation
  - Origin-aligned rigid transformation
- Faces selected via named selections
- Total mapped temperature points: 15

---

## 🛠️ Structural Analysis

- Type: Transient Structural
- Solver: ANSYS Mechanical APDL
- Features:
  - Large deformation ON
  - Newton-Raphson method for nonlinear convergence
  - Frictionless supports on 3 faces
- Coupling:
  - **Imported temperature field (A6)** mapped to 12 bodies
  - Stress-strain results coupled with thermal inputs
- Output:
  - Stress, strain, Euler angles, volume/energy tracking

---

## 🧩 Contact and Coupling

- Total Contact Regions: **29**
- All contacts: **Bonded** (program-controlled formulation)
- Scoping: Geometry-based face-to-face interactions
- Tolerance: 6.5e-5 m
- Advanced settings: Sliding, stiffness, penetration—all program-controlled

---

## 🧱 Mesh

- Nodes: **7982**
- Elements: **1196**
- Mesh Quality: Verified
- Analysis type: 3D, solid elements
- Geometry clean-up: Stitching and decomposition enabled

---

## 📊 Key Results

| Metric                      | Value         |
|----------------------------|---------------|
| Max Temperature            | ~165 °C       |
| Max Stress (Equivalent)    | Calculated    |
| Deformation                | Thermally induced |
| Heat Affected Zone (HAZ)   | Clearly visible |
| Material Behavior          | Nonlinear, expanding |

---

