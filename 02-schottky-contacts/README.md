# Module 02: Si and SiC Schottky diodes and Au/GaAs contacts in TCAD

[Full report (PDF)](report.pdf) · May 2026

## A. Lab: silicon and silicon-carbide Schottky diodes

The goal is to compare a Si diode with a wide-bandgap SiC diode and extract their barrier and doping parameters.

1. We measured I–V on a Peltier stage from 15 °C to 70 °C, with LabVIEW running the sweeps.
2. A Shockley fit at each temperature gives η(T) and I<sub>S</sub>(T).
3. On a Richardson plot of ln(I<sub>S</sub>/T²) against q/kT, the slope gives the Schottky barrier height.
4. We measured C–V at 1 MHz and fitted 1/C² against V. The x-intercept gives V<sub>bi</sub> and the slope gives the doping, and from both we computed the effective area.
5. The impedance phase stays near −90° over the whole bias range, so the diodes respond as pure capacitances.

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

### Results

| Parameter | Si | SiC |
|---|---|---|
| Built-in potential V<sub>bi</sub> | 0.40 V | 2.86 V |
| Mott–Schottky slope | 8.85×10<sup>21</sup> F<sup>-2</sup>V<sup>-1</sup> | 6.11×10<sup>19</sup> F<sup>-2</sup>V<sup>-1</sup> |
| Doping N<sub>D</sub> | 1.67×10<sup>15</sup> cm<sup>-3</sup> | 5.93×10<sup>15</sup> cm<sup>-3</sup> |
| Effective area | 0.09 mm² | 0.63 mm² |

The SiC diode has a much higher barrier than the Si diode, as its wider bandgap predicts. For both devices 1/C² is linear in deep reverse bias, which means the doping is uniform.

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

## B. TCAD: Au/GaAs junction in Sentaurus

Gold has a work function of 5.47 eV. On n-type GaAs the bands bend upward, a Schottky barrier forms and the I–V rectifies. On p-type GaAs the holes see no significant barrier and the I–V is linear. The same metal gives a rectifying or an ohmic contact depending on the doping type.

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

The simulated capacitance falls with reverse bias and 1/C² is linear, as expected for uniform doping. At 10<sup>20</sup> cm<sup>-3</sup> with the tunnelling model on, the depletion width, which scales as 1/√N, becomes thin enough for field emission. The contact then turns ohmic even with a high-work-function metal. Real ohmic contacts rely on the same effect.

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

Authors: L. Ferrari, A. Maghsoud, S. Sbrescia
