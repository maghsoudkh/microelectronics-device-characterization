# Semiconductor Device Characterization — TCAD Simulation and Lab Measurement

Coursework portfolio from the **Microelectronics** course, M.Sc. in Electronic Engineering, Università degli Studi di Padova (A.Y. 2025/2026).

Each module pairs a **Synopsys Sentaurus TCAD simulation** (Sentaurus Structure Editor, Sentaurus Device, Inspect) of a device with a **laboratory measurement** of a real device of the same kind. The work covers the main device structures behind modern electronics: the PN junction, the metal–semiconductor (Schottky) contact and the MOSFET. In each case we extract physical parameters from the data and check them against theory.

## Key results

| Module | Device | Method | Extracted result |
|---|---|---|---|
| [01](01-pn-junction/) | Si PN diode | Temperature-dependent I–V (25–70 °C), Shockley fit, Arrhenius analysis of I<sub>S</sub>(T) | **E<sub>g</sub> = 1.152 eV** (Si reference 1.12 eV, ~3 % deviation); ideality factor η = 1.00–1.015 |
| [02](02-schottky-contacts/) | Si and SiC Schottky diodes; Au/GaAs contacts (TCAD) | I–V(T), Richardson plot, C–V / Mott–Schottky at 1 MHz | SiC: **V<sub>bi</sub> = 2.86 V**, N<sub>D</sub> ≈ 5.9×10<sup>15</sup> cm<sup>-3</sup>; Si: V<sub>bi</sub> = 0.40 V, N<sub>D</sub> ≈ 1.7×10<sup>15</sup> cm<sup>-3</sup>; rectifying → ohmic transition via tunnelling |
| [03](03-mosfet/) | n-MOSFET / MOS capacitor | TCAD sweeps of N<sub>sub</sub> and t<sub>ox</sub>; measured DC, transconductance, C–V, G–V and C–V hysteresis | **V<sub>th</sub> = 3.07 V**, R<sub>ON</sub> = 9.1 Ω, SS = 237.5 mV/dec, **t<sub>ox</sub> = 22.8 nm**, **N<sub>A</sub> = 2.5×10<sup>17</sup> cm<sup>-3</sup>** |

## Skills demonstrated

- **TCAD device simulation (Synopsys Sentaurus):** building 1D/2D device structures, band diagrams, carrier and field profiles, and parametric sweeps (doping, geometry, material, oxide thickness, tunnelling models).
- **Electrical characterization:** temperature-controlled I–V (Peltier stage, automated LabVIEW sweeps), C–V and G–V at several frequencies, impedance-phase checks, hysteresis.
- **Parameter extraction:** Shockley fitting, Arrhenius / Richardson analysis, Mott–Schottky (1/C²) analysis, threshold-voltage extrapolation, subthreshold slope, on-resistance, transconductance, oxide thickness and substrate doping from C–V.
- **Data analysis:** MATLAB fitting and plotting, and comparison of extracted values with analytical device models.

## Repository structure

```
01-pn-junction/          Bandgap extraction (lab) + PN junction TCAD study
02-schottky-contacts/    Si/SiC Schottky diodes (lab) + Au/GaAs MS junction TCAD study
03-mosfet/               MOSFET DC/AC characterization (lab) + MOSFET TCAD study
```

Each folder holds the full report (`report.pdf`), a `README.md` with the method and results, and the key figures.

## Authors

Group 25, working together on all modules:

- **Amirkhashayar Maghsoud**
- Simone Sbrescia
- Lorenzo Ferrari (modules 02 and 03)

The reports were written for course assessment and are shared here as a record of the work.
