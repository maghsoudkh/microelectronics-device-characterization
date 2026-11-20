# 02 — Metal–Semiconductor Contacts: Si/SiC Schottky Diodes and Au/GaAs TCAD

[Full report (PDF)](report.pdf) · May 2026

## A. Lab: silicon vs silicon-carbide Schottky diodes

**Goal:** compare a Si and a wide-bandgap SiC Schottky diode and extract their barrier and doping parameters.

**Method**
1. Measure I–V on a Peltier-controlled stage from 15 °C to 70 °C (automated LabVIEW sweeps).
2. Fit the Shockley equation at each temperature to get η(T) and I<sub>S</sub>(T).
3. Build a **Richardson plot**, ln(I<sub>S</sub>/T²) against q/kT. Its slope gives the Schottky barrier height (SBH).
4. Measure C–V at 1 MHz, then use a **Mott–Schottky** (1/C² vs V) fit. The x-intercept gives V<sub>bi</sub> and the slope gives the doping, which together give the effective device area.
5. Check that the impedance phase stays near −90° (pure capacitive response) across the bias range.

<table>
<tr>
<td width="50%"><img src="figures/lab-si-iv-vs-temperature.png" alt="Si Schottky I–V vs temperature"></td>
<td width="50%"><img src="figures/lab-sic-iv-vs-temperature.png" alt="SiC Schottky I–V vs temperature"></td>
</tr>
<tr>
<td align="center">Si diode, 15–70 °C</td>
<td align="center">SiC diode, 15–70 °C</td>
</tr>
<tr>
<td width="50%"><img src="figures/lab-richardson-si.png" alt="Richardson plot Si"></td>
<td width="50%"><img src="figures/lab-richardson-sic.png" alt="Richardson plot SiC"></td>
</tr>
<tr>
<td align="center">Richardson plot, Si</td>
<td align="center">Richardson plot, SiC</td>
</tr>
</table>

**Results**

| Parameter | Si | SiC |
|---|---|---|
| Built-in potential V<sub>bi</sub> | 0.40 V | 2.86 V |
| Mott–Schottky slope | 8.85×10<sup>21</sup> F<sup>-2</sup>V<sup>-1</sup> | 6.11×10<sup>19</sup> F<sup>-2</sup>V<sup>-1</sup> |
| Doping N<sub>D</sub> | 1.67×10<sup>15</sup> cm<sup>-3</sup> | 5.93×10<sup>15</sup> cm<sup>-3</sup> |
| Effective area | 0.09 mm² | 0.63 mm² |

- The SiC diode has a much higher barrier height than the Si diode, in line with its wide bandgap.
- 1/C² is linear in deep reverse bias for both devices, which indicates uniform doping.

<table>
<tr>
<td width="50%"><img src="figures/lab-cv-si-vs-sic.png" alt="C–V at 1 MHz"></td>
<td width="50%"><img src="figures/lab-mott-schottky.png" alt="Mott–Schottky plot"></td>
</tr>
<tr>
<td align="center">C–V at 1 MHz</td>
<td align="center">Mott–Schottky (1/C²) fits</td>
</tr>
<tr>
<td width="50%"><img src="figures/lab-si-ideality-saturation.png" alt="Si ideality and saturation current"></td>
<td width="50%"><img src="figures/lab-impedance-phase.png" alt="Impedance phase"></td>
</tr>
<tr>
<td align="center">Si: η and I<sub>S</sub> vs temperature</td>
<td align="center">Impedance phase at 1 MHz</td>
</tr>
</table>

## B. TCAD: Au/GaAs metal–semiconductor junction (Synopsys Sentaurus)

- **n-type GaAs + Au (φ<sub>m</sub> = 5.47 eV):** upward band bending forms a Schottky barrier, and the I–V is clearly rectifying.
- **p-type GaAs + Au:** no significant barrier for holes, and the I–V is linear (ohmic). The same metal gives opposite contact types depending on the semiconductor's doping type.

<table>
<tr>
<td width="50%"><img src="figures/tcad-n-gaas-band-diagram.png" alt="n-GaAs band diagram"></td>
<td width="50%"><img src="figures/tcad-n-gaas-iv.png" alt="n-GaAs I–V"></td>
</tr>
<tr>
<td align="center">Au / n-GaAs: band diagram</td>
<td align="center">Au / n-GaAs: rectifying I–V</td>
</tr>
<tr>
<td width="50%"><img src="figures/tcad-p-gaas-band-diagram.png" alt="p-GaAs band diagram"></td>
<td width="50%"><img src="figures/tcad-p-gaas-iv.png" alt="p-GaAs I–V"></td>
</tr>
<tr>
<td align="center">Au / p-GaAs: band diagram</td>
<td align="center">Au / p-GaAs: ohmic I–V</td>
</tr>
</table>

- **C–V:** capacitance falls with reverse bias, and 1/C² is linear for uniform doping.
- **Heavy doping (10<sup>20</sup> cm<sup>-3</sup>) with tunnelling enabled:** the depletion width (W ∝ 1/√N) becomes thin enough for field emission. The contact turns ohmic even with a high-work-function metal, which is the physics behind real ohmic contacts.

<table>
<tr>
<td width="50%"><img src="figures/tcad-mott-schottky.png" alt="Simulated Mott–Schottky"></td>
<td width="50%"><img src="figures/tcad-tunnelling-iv.png" alt="Tunnelling I–V"></td>
</tr>
<tr>
<td align="center">Simulated 1/C² vs V</td>
<td align="center">I–V with and without heavy doping (tunnelling)</td>
</tr>
</table>

**Authors:** L. Ferrari, A. Maghsoud, S. Sbrescia
