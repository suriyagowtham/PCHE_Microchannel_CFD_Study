# Effect of Microchannel Cross-Sectional Profile on the Thermal-Hydraulic Performance of Straight Printed Circuit Heat Exchangers

**Authors:** Suriyagowtham S., Rahul Tarodiya  
**Institution:** Department of Mechanical Engineering, VNIT Nagpur  
**Submitted to:** Applied Thermal Engineering  
**Solver:** OpenFOAM v2512 (`chtMultiRegionSimpleFoam`)

---

## Overview

Printed Circuit Heat Exchangers (PCHEs) are compact, diffusion-bonded heat exchangers
capable of withstanding pressures above 50 MPa and temperatures beyond 1000 K, with
surface-area densities of 700–2500 m²/m³. They are used in supercritical-CO₂ power
cycles, LNG processing, aerospace thermal management, and advanced nuclear systems.

Most PCHE studies fix the cross-sectional shape (semicircular) and vary the channel
planform (zigzag, wavy, serpentine). This study does the opposite — the planform is kept
straight and the cross-sectional profile is treated as both a **design variable** and a
**fabrication variable**.

Thirteen straight PCHE microchannel profiles are compared under identical helium/Alloy-617
conditions using 3D steady-state conjugate heat transfer CFD.

---

## Channel Profiles Studied (13 Total)

| Family | Profile | Geometric Parameter |
|--------|---------|-------------------|
| Semicircular (baseline) | SCP | Diameter D = 2.0 mm |
| Rectangular | RP_R0 | Corner radius R = 0 mm |
| Rectangular | RP_R0.1 | Corner radius R = 0.1 mm |
| Rectangular | RP_R0.2 | Corner radius R = 0.2 mm |
| Rectangular | RP_R0.3 | Corner radius R = 0.3 mm |
| Rectangular | RP_R0.4 | Corner radius R = 0.4 mm |
| Rectangular | RP_R0.5 | Corner radius R = 0.5 mm |
| Trapezoidal | TP_Deg45 | Sidewall angle φ = 45° |
| Trapezoidal | TP_Deg54.7 | Sidewall angle φ = 54.7° |
| Trapezoidal | TP_Deg60 | Sidewall angle φ = 60° |
| Trapezoidal | TP_Deg66.7 | Sidewall angle φ = 66.7° |
| Trapezoidal | TP_Deg70 | Sidewall angle φ = 70° |
| Trapezoidal | TP_Deg75 | Sidewall angle φ = 75° |

---

## Geometry

| Parameter | Value |
|-----------|-------|
| Strip width | W = 3.6 mm |
| Channel height | H = 3.2 mm |
| Plate thickness | tₚ = 1.6 mm |
| Channel length | L = 50 mm |
| Configuration | Counter-flow strip (1 hot + 1 cold channel) |
| Solid material | Alloy-617 |

---

## Operating Conditions

| Parameter | Value |
|-----------|-------|
| Working fluid | Helium (He) |
| Operating pressure | 3 MPa |
| Hot inlet temperature | 1173 K |
| Cold inlet temperature | 813 K |
| Mean temperature | 993 K |
| Fluid density ρ | 1.455 kg/m³ |
| Dynamic viscosity µ | 4.08 × 10⁻⁵ Pa·s |
| Thermal conductivity k | 0.298 W/m·K |
| Prandtl number Pr | 0.711 |
| Flow regime | Laminar (Re ≈ 441–2207) |

### Reynolds Number Cases

| Case | Full PCHE flow rate | Re |
|------|--------------------|----|
| FR10 | 10 kg/h | ≈ 441 |
| FR20 | 20 kg/h | ≈ 883 |
| FR30 | 30 kg/h | ≈ 1324 |
| FR40 | 40 kg/h | ≈ 1766 |
| FR50 | 50 kg/h | ≈ 2207 |

---

## Numerical Setup

| Parameter | Specification |
|-----------|--------------|
| Solver | `chtMultiRegionSimpleFoam` (OpenFOAM v2512) |
| Simulation type | Steady-state 3D conjugate heat transfer |
| Fluid regions | `hot_fluid`, `cold_fluid` (He gas) |
| Solid region | `solid_plate` (Alloy-617) |
| Mesh tool | `snappyHexMesh` |
| Mesh type | Structured hexahedral |
| Production mesh size | 1.0 million cells |
| Max skewness | < 0.3 |
| Orthogonality angle | > 70° |
| y⁺ | < 1 |
| Pressure–velocity coupling | SIMPLE |
| Convection scheme | Gauss linearUpwind (2nd-order upwind) |
| Diffusion scheme | Gauss linear corrected |
| Convergence criterion | 10⁻⁶ |

---

## Performance Metrics

| Metric | Description |
|--------|-------------|
| Nu | Nusselt number — convective heat transfer strength |
| f | Fanning friction factor — flow resistance |
| NTU | Number of Transfer Units — heat exchanger effectiveness |
| Qvol | Volumetric heat density (MW/m³) |
| ΔP | Pressure drop (kPa) |
| **PEC** | **Performance Evaluation Criterion** |

### PEC Definition (Webb & Eckert, 1972)

At equal pumping power:

$$\text{PEC} = \frac{Nu / Nu_{SCP}}{(f / f_{SCP})^{1/3}}$$

- PEC = 1.00 → matches semicircular baseline
- PEC > 1.00 → net gain over baseline at equal pumping power
- PEC < 1.00 → deficit relative to baseline

---

## Key Results

### Full Results Table (Re ≈ 441 and Re ≈ 2207)

| Profile | Nu (Re≈441) | PEC (Re≈441) | Nu (Re≈2207) | PEC (Re≈2207) |
|---------|------------|-------------|-------------|--------------|
| **SCP (baseline)** | 1.723 | **1.000** | 4.384 | **1.000** |
| RP_R0 | 1.744 | 0.995 | 4.289 | 0.980 |
| RP_R0.1 | 1.582 | 0.895 | 4.019 | 0.907 |
| RP_R0.2 | 1.635 | 0.925 | 4.128 | 0.932 |
| RP_R0.3 | 1.652 | 0.939 | 4.169 | 0.946 |
| RP_R0.4 | 1.653 | 0.945 | 4.151 | 0.949 |
| **RP_R0.5** | 1.659 | **0.952** | 4.170 | **0.953** |
| TP_Deg45 | 1.384 | 0.863 | 3.744 | 0.911 |
| TP_Deg54.7 | 1.454 | 0.888 | 3.839 | 0.916 |
| TP_Deg60 | 1.518 | 0.911 | 3.965 | 0.921 |
| TP_Deg66.7 | 1.534 | 0.919 | 3.969 | 0.923 |
| **TP_Deg70** | 1.609 | **0.936** | 4.145 | **0.935** |
| TP_Deg75 | 1.593 | 0.914 | 4.075 | 0.910 |

### Summary of Findings

- **SCP gives the highest PEC at every Reynolds number** — it is the thermal-hydraulic benchmark
- **RP_R0.5 is the best practical rectangular profile** (PEC ≈ 0.952–0.953) — fully rounded, manufacturing-tolerant, and avoids the tool-wear trap of RP_R0
- **RP_R0.1 gives the lowest rectangular PEC** (≈ 0.895–0.907) — a small fillet removes corner-driven heat transfer without sufficient friction reduction to compensate
- **TP_Deg70 is the best trapezoidal profile** (PEC ≈ 0.935–0.936); no trapezoidal case reaches PEC = 0.95
- **Manufacturing insight:** Sharp RP_R0 corners degrade to ≈RP_R0.1 under micro-milling tool wear, causing a large PEC drop. RP_R0.5 is immune to this effect.
- **Recommended design pair:** SCP + RP_R0.5 — highest performance with manufacturing reliability

---

## Model Validation

Validated against the helium PCHE data of Figley et al. (Progress in Nuclear Energy, 2013) at 3 MPa, Re ≈ 883–2207. Maximum deviation in overall heat-transfer coefficient: **6%**.

---

## Repository Structure
