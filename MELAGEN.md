# 🧪 Melagen Labs — Melanin–HDPE Radiation Shielding Composite  
**Proof-of-Concept Experimental Validation**

**Engineering Focus:** Experimental test system design, materials validation, statistical performance analysis, and mass-constrained engineering trade studies for aerospace and radiation-sensitive systems.

---

## System Context
This project was structured as a **materials test and validation system**, not a standalone experiment. The focus was on building a repeatable measurement pipeline — from physical setup and instrumentation geometry to statistical analysis — mirroring how aerospace and defense teams qualify new materials under **mass, performance, and reliability constraints**.

---

## Quick Specs
- **Radiation Source:** Cs-137 (10 µCi)  
- **Test Distances:** 3 cm, 5 cm, 10 cm  
- **Metrics:** mSv/hr, counts/sec  
- **Composite Density:** ~0.83 g/cm³  
- **Reference Material:** Aluminum (~2.6 g/cm³)  
- **Analysis:** Two-factor ANOVA + linear regression (Python)

## Overview
This repository documents the design, fabrication, and experimental validation of a **melanin–polyethylene (HDPE) composite radiation shielding material** developed at Melagen Labs. The objective was to evaluate whether a low-density, polymer-based composite could achieve **comparable gamma shielding performance to aluminum** while significantly reducing mass — a key constraint for space and aerospace applications where launch cost and payload mass dominate system tradeoffs.

## Engineering Objective
**Demonstrate comparable or better shielding efficacy to aluminum at substantially lower density.**

Target metrics:
- Shielding efficacy > 40% (relative to control)  
- Composite density < 1.0 g/cm³  
- Comparable performance to aluminum for matched thickness and distance  
- Statistical validation of material and distance effects  

---

## System Architecture

**Test Stack**
Cs-137 Source → Shielding Sample → Geiger Counter Probe → Data Logging → Python Analysis

**Control Variables**
- Radiation source: Cs-137 (10 µCi)  
- Sample placement: midpoint between source and detector  
- Test distances: 3.0 cm, 5.0 cm, 10.0 cm  
- Measurement metrics: mSv/hr, counts/s  

---

## Composite Formulation

**Material Composition**
- 5% melanin by weight  
- 95% high-density polyethylene (HDPE) by weight  

**Fabrication Process**
1. HDPE heated to ~160 °C and melted  
2. Melanin incrementally mixed to ensure uniform dispersion  
3. Composite poured into rectangular molds (10 mm, 8 mm, 4 mm)  
4. Cured, demolded, and sanded to controlled thickness  

This formulation prioritized **structural rigidity** while maintaining a melanin loading sufficient to evaluate shielding contribution.

---

## Test Samples

### Composite Samples
| Sample | Thickness (mm) | Mass (g) | Density (g/cm³) |
|--------|----------------|----------|------------------|
| Blue (Thick)  | 9.52 | 7.8 | 0.826 |
| White (Mid)  | 6.67 | 5.9 | 0.837 |
| Pink (Thin)  | 4.82 | 4.3 | 0.825 |

### Aluminum References
| Plate | Thickness (mm) | Mass (g) | Density (g/cm³) |
|-------|----------------|----------|------------------|
| Al-1 (Thick) | 9.58 | 75.8 | 2.533 |
| Al-2 (Mid)  | 6.59 | 56.2 | 2.731 |
| Al-3 (Thin) | 4.87 | 38.8 | 2.551 |

**Aggregate Density**
- Composite: **0.829 g/cm³**  
- Aluminum: **2.605 g/cm³**  

> The composite achieves ~**3.1× lower density** than aluminum at comparable thickness.

---

## Experimental Method

For each trial:
1. Measure control radiation (no shielding)  
2. Insert composite sample and measure attenuation  
3. Insert aluminum plate of corresponding thickness and measure attenuation  
4. Repeat at increasing source–detector distances  

**Shielding Efficacy**
Efficacy (%) = (1 - Shielded_Radiation / Control_Radiation) × 100

---

## Results Summary

### Aggregate Shielding Efficiency (Across All Distances)
| Material | Thick | Mid | Thin |
|----------|-------|-----|------|
| Composite | 92.20% | 93.78% | 93.71% |
| Aluminum | 91.65% | 93.01% | 94.02% |

At matched thickness and distance, **no statistically significant difference** in shielding efficacy was observed between composite and aluminum.

---

## Statistical Analysis (Python)

### Two-Factor ANOVA (Material × Distance)
| Factor | F-value | p-value | Interpretation |
|--------|---------|---------|----------------|
| Material Type | 0.097 | 0.760 | Not significant |
| Distance | 7.101 | 0.009 | **Significant** |
| Interaction | 0.133 | 0.877 | Not significant |

**Conclusion:**  
Distance from the radiation source is the dominant factor in shielding performance. Material type (composite vs aluminum) does **not** introduce statistically significant variation in efficacy at tested ranges.

---

## Regression Model

Linear model:
Shielding_Efficacy = β0 + β1(Material) + β2(Distance) + β3(Material × Distance)

Key findings:
- **Distance coefficient:** −0.744% efficacy per cm (aluminum)  
- **Composite interaction term:** +0.178% per cm  

> The composite exhibits a **~24% lower drop-off in shielding efficacy per cm** compared to aluminum, suggesting improved performance stability at increasing distances (trend-level, statistically insignificant at current sample size).

---

## Key Engineering Observations
- Composite density measured **~15% below theoretical**, likely due to air entrainment during open-air mixing  
- Despite reduced density, composite performance remained **comparable to aluminum**  
- Shielding efficacy drop-off with distance is **less steep for the composite**  
- Thickness variation across the tested range did **not** produce statistically significant differences  

---

## Limitations & Error Sources
- Open-air mixing introduced **voids and air pockets**  
- Composite composition drift due to material loss during stirring  
- Limited thickness range constrained ANOVA sensitivity  
- Measurement resolution limited to ±0.1 g mass and ±0.001 mm thickness  

---

## Implications
This proof-of-concept demonstrates that a **polymer-based, melanin-loaded composite can match aluminum’s gamma shielding performance at ~⅓ the density**, directly supporting mass-reduction strategies for:
- Satellite shielding  
- Deep-space electronics enclosures  
- Lightweight aerospace radiation barriers  

---

## Future Work
- Vacuum-assisted composite molding to eliminate air entrainment  
- Broader thickness and melanin concentration sweeps  
- Testing with additional radiation sources (beta/neutron)  
- Environmental stability testing (thermal cycling, vacuum exposure)  

---

## Technical Stack
- **Materials:** Melanin, HDPE, Aluminum reference plates  
- **Instrumentation:** Cs-137 gamma source, Geiger counter  
- **Analysis:** Python (NumPy, Pandas, StatsModels, Matplotlib)  
- **Methods:** ANOVA, linear regression, density analysis  

---

## Author
**Ibrahim Rogers**  
Co-Founder & COO — Melagen Labs  
Mechanical Engineering, Northeastern University
