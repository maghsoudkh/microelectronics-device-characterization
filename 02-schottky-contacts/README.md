# 02 — Metal–Semiconductor Contacts: Si/SiC Schottky Diodes and Au/GaAs TCAD

[Full report (PDF)](report.pdf) · May 2026

## A. Lab: silicon vs silicon-carbide Schottky diodes

**Goal:** compare a Si and a wide-bandgap SiC Schottky diode and extract their barrier and doping parameters.

**Method**
1. Measure I–V on a Peltier-controlled stage across temperature (automated LabVIEW sweeps).
2. Fit the Shockley equation at each temperature to get η(T) and I<sub>S</sub>(T).
3. Build a **Richardson plot**, ln(I<sub>S</sub>/T²) against q/kT. Its slope gives the Schottky barrier height (SBH).
4. Measure C–V at 1 MHz, then use a **Mott–Schottky** (1/C² vs V) fit. The x-intercept gives V<sub>bi</sub> and the slope gives the doping, which together give the effective device area.
5. Check that the impedance phase stays near −90° (pure capacitive response) across the bias range.

**Results**

| Parameter | Si | SiC |
|---|---|---|
| Built-in potential V<sub>bi</sub> | 0.40 V | 2.86 V |
| Mott–Schottky slope | 8.85×10<sup>21</sup> F<sup>-2</sup>V<sup>-1</sup> | 6.11×10<sup>19</sup> F<sup>-2</sup>V<sup>-1</sup> |
| Doping N<sub>D</sub> | 1.67×10<sup>15</sup> cm<sup>-3</sup> | 5.93×10<sup>15</sup> cm<sup>-3</sup> |
| Effective area | 0.09 mm² | 0.63 mm² |

- The SiC diode has a much higher barrier height than the Si diode, in line with its wide bandgap.
- 1/C² is linear in deep reverse bias for both devices, which indicates uniform doping.

![Richardson plot](figures/lab-richardson-sbh.png)
![Mott–Schottky analysis](figures/lab-mott-schottky.png)
![Ideality factor and saturation current](figures/lab-ideality-saturation.png)

## B. TCAD: Au/GaAs metal–semiconductor junction

- **n-type GaAs + Au (φ<sub>m</sub> = 5.47 eV):** upward band bending forms a Schottky barrier, and the I–V is clearly rectifying.
- **p-type GaAs + Au:** no significant barrier for holes, and the I–V is linear (ohmic). The same metal gives opposite contact types depending on the semiconductor's doping type.
- **C–V:** capacitance falls with reverse bias, and 1/C² is linear for uniform doping.
- **Heavy doping (10<sup>20</sup> cm<sup>-3</sup>) with tunnelling enabled:** the depletion width (W ∝ 1/√N) becomes thin enough for field emission. The contact turns ohmic even with a high-work-function metal, which is the physics behind real ohmic contacts.

![n-MS rectifying contact](figures/tcad-n-ms-rectifying.png)
![Tunnelling at high doping](figures/tcad-tunnelling.png)
![TCAD C–V](figures/tcad-cv.png)

**Authors:** L. Ferrari, A. Maghsoud, S. Sbrescia
