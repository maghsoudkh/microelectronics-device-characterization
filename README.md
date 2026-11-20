# Semiconductor device characterization: TCAD simulation and lab measurement

Coursework from the Microelectronics course, M.Sc. in Electronic Engineering, University of Padova, academic year 2025/2026.

Each module pairs a Synopsys Sentaurus TCAD simulation of a device with a laboratory measurement of a real device of the same type. The modules cover the PN junction, the metal–semiconductor Schottky contact and the MOSFET. In each one we extract physical parameters from the data and compare them with analytical models.

## Main results

| Module | Device | Method | Result |
|---|---|---|---|
| [01](01-pn-junction/) | Si PN diode | I–V from 25 to 70 °C, Shockley fit, Arrhenius fit of I<sub>S</sub>(T) | E<sub>g</sub> = 1.152 eV against the 1.12 eV reference for Si. Ideality factor between 1.000 and 1.015. |
| [02](02-schottky-contacts/) | Si and SiC Schottky diodes, Au/GaAs contacts in TCAD | I–V(T), Richardson plot, C–V and Mott–Schottky at 1 MHz | SiC: V<sub>bi</sub> = 2.86 V, N<sub>D</sub> ≈ 5.9×10<sup>15</sup> cm<sup>-3</sup>. Si: V<sub>bi</sub> = 0.40 V, N<sub>D</sub> ≈ 1.7×10<sup>15</sup> cm<sup>-3</sup>. Heavy doping turns the Au/GaAs contact ohmic through tunnelling. |
| [03](03-mosfet/) | n-MOSFET and MOS capacitor | TCAD sweeps of N<sub>sub</sub> and t<sub>ox</sub>. Measured DC, transconductance, C–V, G–V and C–V hysteresis | V<sub>th</sub> = 3.07 V, R<sub>ON</sub> = 9.1 Ω, SS = 237.5 mV/dec, t<sub>ox</sub> = 22.8 nm, N<sub>A</sub> = 2.5×10<sup>17</sup> cm<sup>-3</sup> |

## Methods used

- Sentaurus TCAD: building 1D and 2D device structures, then simulating band diagrams, carrier and field profiles, and sweeps of doping, geometry, material, oxide thickness and tunnelling models.
- Electrical characterization: I–V on a Peltier temperature stage driven by LabVIEW, C–V and G–V at several frequencies, impedance phase and C–V hysteresis.
- Parameter extraction: Shockley, Arrhenius and Richardson fits, Mott–Schottky analysis, threshold voltage, subthreshold slope, on-resistance, transconductance, and oxide thickness and substrate doping from C–V.
- MATLAB for fitting and plotting.

## Repository layout

```
01-pn-junction/          Bandgap extraction in the lab, PN junction in TCAD
02-schottky-contacts/    Si and SiC Schottky diodes in the lab, Au/GaAs junction in TCAD
03-mosfet/               MOSFET DC and AC characterization in the lab, MOSFET in TCAD
```

Each folder has the full report as `report.pdf`, a README with the method and results, and the figures.

## Authors

Group 25 worked on all modules together:

- Amirkhashayar Maghsoud
- Simone Sbrescia
- Lorenzo Ferrari, modules 02 and 03

We wrote the reports for course assessment and share them here as a record of the work.

## License

The reports, figures and text are licensed under [CC BY 4.0](LICENSE). You may reuse them with credit to the authors listed above. The University of Padova logos on the report slides belong to the university and are not covered by this license.
