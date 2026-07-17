# Thermo-Hydraulic Characterization of PCHE Microchannel Profiles

Numerical investigation of thermal-hydraulic performance of 13 Printed Circuit 
Heat Exchanger (PCHE) microchannel profiles using OpenFOAM v2512.

## Overview

Printed Circuit Heat Exchangers (PCHEs) are compact, high-efficiency heat 
exchangers used in nuclear, hydrogen, and gas turbine applications. This study 
evaluates the effect of microchannel cross-sectional geometry on thermal-hydraulic 
performance to identify the optimal profile for compact heat exchanger design.

## Microchannel Profiles Studied

| Category      | Profiles                          |
|---------------|-----------------------------------|
| Rectangular   | RP_R0, RP_R0.5, RP_R1.0, ...     |
| Trapezoidal   | TP_V1, TP_V2, ...                 |
| Semicircular  | SP_V1, SP_V2, ...                 |

**Total: 13 profiles**

## Methodology

- **Solver:** `chtMultiRegionSimpleFoam` (OpenFOAM v2512)
- **Simulation type:** Steady-state Conjugate Heat Transfer (CHT)
- **Reynolds number range:** Re = 200 – 1000 (laminar regime)
- **Regions:** Fluid (coolant) + Solid (stainless steel wall)

## Performance Parameters Evaluated

| Parameter | Description |
|-----------|-------------|
| Nu | Nusselt number — convective heat transfer |
| f | Darcy friction factor — flow resistance |
| NTU | Number of Transfer Units — heat exchanger effectiveness |
| PEC | Performance Evaluation Criterion — thermal vs pumping penalty |

**PEC formula:**
$$PEC = \frac{Nu/Nu_0}{(f/f_0)^{1/3}}$$

## Key Result

**Optimal profile: RP_R0.5** (Rectangular with 0.5 mm fillet radius)
- PEC ≈ 0.99 — best balance of heat transfer and pressure drop
- Recommended for compact PCHE design applications

## Repository Structure
