# Ibrahim Rogers

**Mechanical Engineering · Test Systems · Hardware Development**

B.S. Mechanical Engineering, Northeastern University · Expected May 2028
Quality & Sustaining Engineering Co-op @ Parker Hannifin, Precision Fluidics

**→ [Full portfolio (PDF)](IROGERS_ME_PORTFOLIO_2027.pdf)** · drawings, P&IDs, hardware, results

---

## Selected Work

### Liquid Valve Endurance Tester & Leak-Test Fixture
`Parker Hannifin, Precision Fluidics` · `2026` · `Inventor` · `P&ID` · `hydraulics`

Closed-loop DI-water tester cycling a bank of valves simultaneously, scoped and built end to end.

- Consolidated conflicting quality, manufacturing, and engineering requirements into one defined scope
- Developed hydraulic architecture; sized pump, chiller, reservoir, manifold, and instrumentation
- Released drawings, schematics, and P&IDs
- Built the loop: plumbed suction and return runs, installed filtration and isolation valves, wired and commissioned the pump, leak-checked the assembly

<details>
<summary><b>Commissioning: two findings that turned out to be one</b></summary>

<br>

First runs showed air trapped in the line and a check valve not reaching cracking pressure. These were worked as separate faults longer than they should have been.

Entrained gas is compressible. It was absorbing the pressure rise that should have been developing across the check valve, so the loop never built enough differential pressure to crack it. The valve was the symptom; the air was the cause.

A bleed valve resolved both. Bleed points now go into the P&ID from the start, at the high points of the routing.

</details>

**In progress:** extending the loop into a corrosion study on wetted internals. Hypochlorite exposure cycled against air purge and DI flush rather than a continuous soak. Dosing pump sized from a fill-time requirement across the internal volume of the valve string plus interconnecting tubing; peristaltic selected so the working fluid contacts nothing but tubing.

**Companion fixture:** pressure-decay leak test for supplier-side incoming inspection of a molded component. Pressure decay chosen over flow-based measurement because flow instrumentation fine enough to resolve the required leak rate was not available at acceptable cost. Locating and sealing functions separated so the probe seals against the orifice without over-constraining a part carrying real dimensional variation. Probe geometry sized against worst-case tolerance using MMC/LMC.

---

### Printed Fixturing — Nest, Petri Tray & Purge Manifold
`Parker Hannifin, Precision Fluidics` · `2026` · `FDM` · `mechanism design`

Three fixtures for one product family. Each exists to take the operator out of a variable.

| Fixture | Problem | Approach |
|---|---|---|
| **Load-frame nest** | Hand-positioning adds run-to-run variation to the measurement being taken | Slot constrains the part laterally, wide base sits flat on the platen, sealing face left open |
| **Compliant petri tray** | A plain recess holds a dish by clearance alone, so the dish moves | Retention wall arches over a void with slit hinges either side; the dish deflects the wall going in |
| **Purge manifold** | Blowing parts dry by hand gives a different result per part and per operator | Ten stations on a common plenum, one inlet, one operation per batch |

**Notes on the tray:** the first print did not produce the feature at all. The wall was drawn thinner than the printer could resolve, so the pockets came out as plain recesses. Thickening the neck recovered it. Retention across repeated insertions is **not yet verified** and waits on a PETG build.

**Notes on the manifold:** flow distribution across the stations, not station count, is what decides whether the fixture does what it claims.

---

### Contamination Root-Cause Investigations
`Parker Hannifin, Precision Fluidics` · `2026` · `DOE` · `failure analysis`

Two independent investigations into recurring return failures with distinct mechanisms.

- Isolated an orifice-corrosion source across supplier, stock, cleaning, and floor-process variables through designed experiments
- Traced a separate foreign-object mechanism by teardown and comparative inspection against conforming parts

---

### Packaging Redesign & Machine-Vision Inspection
`Parker Hannifin, Precision Fluidics` · `2026` · `Python` · `OpenCV`

- Redesigned packaging for a low-volume, high-value component after field-reported transit damage, inside a fixed cost ceiling set by unit economics
- Building a machine-vision inspection system to flag defects on a production cell before shipment

---

### Refreshable Braille Tactile Display
`Forge, Northeastern University Hardware Product Lab` · `2026` · `Onshape` · `tolerance analysis`

Six-dot cell producing the full 64-character set from **two actuators instead of six**.

- Each half-cell's eight pin states encoded as discrete positions on a stepped rack
- Motors sit outboard, driving racks inward through a bevel geartrain, clearing the 6.25 mm cell footprint so cells tile at reading pitch
- Full self-authored drawing package
- Jam rate cut from ~15% to under 2% across 2,000+ cycles: guide clearance opened from 0.1 to 0.15 mm, lead-in chamfers added, PLA → PETG

---

### Vision-Guided Pan/Tilt Tracking System
`Independent` · `2025–26` · `Raspberry Pi` · `OpenCV` · [**details →**](GIMBAL.md)

Closed-loop target tracking across mechanical gimbal, electronics, and control software.

- Raspberry Pi 5, OpenCV/ArUco detection, PCA9685 servo control over I²C
- PID on both axes, gains tuned on hardware
- Automated re-acquisition when the marker leaves frame

---

### Gamma Shielding Test System
`Melagen Labs` · `2024` · `ANOVA` · `experiment design` · [**details →**](MELAGEN.md)

- Co-designed test fixture and experimental protocol for a melanin-HDPE composite against an aluminum reference, Cs-137 source
- Attenuation comparable to aluminum at roughly one-third the density
- Validated by ANOVA and regression in Python

---

## Capabilities

| | |
|---|---|
| **CAD & Design** | Autodesk Inventor · SolidWorks · Onshape · AutoCAD · GD&T (MMC/LMC) · worst-case tolerance stack-up · interference analysis · fixture design · P&ID development |
| **Fluid & Test Systems** | Hydraulic/pneumatic architecture · pressure regulation and relief · closed-loop recirculation · pump and chiller sizing · manifold design · pressure-decay and flow-based leak test |
| **Programming & Analysis** | Python (OpenCV, pandas) · C++ · MATLAB · ANOVA/regression · I²C and PWM · Raspberry Pi · Arduino |
| **Manufacturing & Quality** | FDM/SLA printing · mechanical prototyping · dimensional inspection and metrology · failure analysis · root-cause investigation · FMEA · validation and test documentation |

---

## Contact

[LinkedIn](https://www.linkedin.com/in/ibrahim-rogers/) · [rogers.ib@northeastern.edu](mailto:rogers.ib@northeastern.edu)
U.S. Citizen · Relocation possible
