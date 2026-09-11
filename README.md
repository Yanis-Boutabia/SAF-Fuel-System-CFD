# SAF Compatibility Analysis — Airbus A320 / CFM56-5B Fuel System

CFD study of Sustainable Aviation Fuel (SAF HEFA) compatibility with the A320/CFM56-5B fuel system, focused on wall shear stress behavior compared to conventional Jet-A1.

## Overview

Fuel system corrosion in service is rarely a purely chemical phenomenon — it is accelerated by the mechanical stresses of the flow itself (corrosion-erosion). This project complements a COMSOL electrochemical corrosion study (galvanic corrosion, AlCl²⁺ concentration) with a CFD analysis of the mechanical side: wall shear stress (WSS) and the effect of pipe wall roughness, to build a combined risk picture for the CFM56 fuel circuit.

> **My contribution:** the STAR-CCM+ CFD analysis (wall shear stress, roughness study). The COMSOL electrochemical corrosion analysis was carried out separately as a complementary chemical study.

## Methodology

- **Tool:** STAR-CCM+
- **Domain:** Cylindrical conduit representative of a CFM56 fuel line — D = 25 mm, L = 250 mm
- **Mesh:** Polyhedral, ~22,000 cells, 3 prism layers at the wall
- **Turbulence model:** k-ω SST, All y+ wall treatment
- **Conditions:** Steady-state, inlet velocity 2 m/s (representative of the CFM56 HP fuel pump)
- **Fluids compared:** Jet-A1 (reference) vs SAF HEFA (adjusted density ρ and viscosity μ)
- **Reynolds number:** Re ≈ 31,700 (Jet-A1) · Re ≈ 33,100 (SAF HEFA)

## Results

### Wall Shear Stress — SAF HEFA vs Jet-A1

![Wall shear stress distribution — Jet-A1](./images/screenshot-2.png)
*Wall shear stress distribution on the pipe wall for Jet-A1 (reference case)*

![Wall shear stress distribution — SAF HEFA](./images/screenshot-3.png)
*Wall shear stress distribution for SAF HEFA — lower peak stress than Jet-A1*

| Fuel | WSS min (Pa) | WSS mean (Pa) | WSS max (Pa) | Δ vs Jet-A1 |
|---|---|---|---|---|
| Jet-A1 (reference) | 9.22 | 16.8 | 24.3 | — |
| **SAF HEFA** | 8.67 | 15.8 | 23.0 | **−6.0 %** |

**Key result: SAF HEFA reduces wall shear stress by 6% compared to Jet-A1**, driven by its lower viscosity and the resulting lower wall friction.

### Effect of material roughness

Three CFM56 fuel circuit materials were tested at SAF HEFA conditions (Re ≈ 32,000):

| Material | Ra (µm) | WSS max | Variation |
|---|---|---|---|
| Aluminium 2024 (polished) | 0.4 | 23.0 Pa | reference |
| Stainless steel 316L | 1.5 | 23.0 Pa | +0.0 % |
| Carbon steel | 45 | 23.0 Pa | +0.0 % |

Despite a 110× higher roughness for carbon steel versus polished aluminium, WSS remains identical (23 Pa) across all three materials. This is explained by the flow regime: at Re ≈ 31,700–33,100, the flow is hydraulically smooth — the viscous sublayer remains thicker than the wall roughness elements. Differentiating materials mechanically would require Re > 100,000.

![Mesh — polyhedral with prism layers](./images/screenshot-1.png)
*STAR-CCM+ polyhedral mesher with 3 wall prism layers*

## Conclusion

1. **SAF is mechanically less aggressive than Jet-A1** — a 6% reduction in wall shear stress, consistent with the COMSOL chemical results (−61% AlCl²⁺ with eSAF): both approaches converge on SAF being less aggressive to the fuel system.
2. **SAF/material compatibility is primarily a chemical issue** — material nature has no measurable effect on mechanical wall stress at nominal regime (ΔWSS < 1% between aluminium, stainless steel and carbon steel), validating the COMSOL approach as the relevant selection criterion.
3. **Combined corrosion-erosion risk identified** — a wall chemically weakened by Jet-A1 and subjected to continuous WSS degrades faster. This combined risk is significantly reduced with SAF, a double benefit for fuel circuit durability.

## Tools

`STAR-CCM+` · `COMSOL Multiphysics` (complementary chemical study)

---
*Academic project (EN426) — IPSA Paris, Aero 4-VEH, 2025–2026.*
