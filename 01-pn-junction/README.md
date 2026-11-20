# 01 — PN Junction: Silicon Bandgap Extraction and TCAD Study

[Full report (PDF)](report.pdf) · April 2026

## A. Lab: extracting the silicon bandgap from diode I–V(T)

**Goal:** measure the energy gap of silicon using only the electrical response of a diode.

**Method**
1. Measure forward and reverse I–V of a Si diode at six temperatures from 25 °C to 70 °C.
2. Fit the Shockley equation, I = I<sub>S</sub>(e<sup>qV/ηkT</sup> − 1), in the linear semilog region (0.20–0.35 V) to get I<sub>S</sub> and η at each temperature.
3. Use the model I<sub>S</sub> = B·T<sup>3+γ/2</sup>·exp(−qE<sub>g</sub>/kT) and fit ln I<sub>S</sub> against 1/kT. The slope gives E<sub>g</sub>.

<table>
<tr>
<td width="50%"><img src="figures/lab-iv-vs-temperature.png" alt="I–V at different temperatures"></td>
<td width="50%"><img src="figures/lab-shockley-fits.png" alt="Shockley fits in the exponential region"></td>
</tr>
<tr>
<td align="center">Measured I–V from 25 °C to 70 °C</td>
<td align="center">Shockley fits between 0.20 V and 0.35 V</td>
</tr>
</table>

**Results**

| T [°C] | I<sub>S</sub> [A] | η |
|---|---|---|
| 25.0 | 3.59×10<sup>-14</sup> | 1.015 |
| 36.0 | 1.80×10<sup>-13</sup> | 1.007 |
| 46.9 | 8.90×10<sup>-13</sup> | 1.005 |
| 56.9 | 3.59×10<sup>-12</sup> | 1.003 |
| 66.8 | 1.16×10<sup>-11</sup> | 1.000 |
| 70.0 | 1.86×10<sup>-11</sup> | 1.001 |

- **E<sub>g</sub> ≈ 1.152 eV**, about 3 % above the textbook 1.12 eV for silicon.
- η stays close to 1 at every temperature, so transport is dominated by diffusion, as expected for an ideal Si diode.

<table>
<tr>
<td width="50%"><img src="figures/lab-bandgap-extraction.png" alt="Bandgap extraction"></td>
<td width="50%"><img src="figures/lab-ideality-saturation.png" alt="Ideality factor and saturation current"></td>
</tr>
<tr>
<td align="center">Arrhenius fit of I<sub>S</sub>: E<sub>g</sub> = 1.152 eV</td>
<td align="center">Ideality factor and saturation current vs temperature</td>
</tr>
</table>

## B. TCAD: PN junction physics (Synopsys Sentaurus)

- **Equilibrium:** carrier densities, electric field and electrostatic potential across the junction. The field peaks in the depletion region.
- **Band diagram:** built-in potential and space-charge-region width read from the simulation and compared with analytical expressions.

<table>
<tr>
<td width="33%"><img src="figures/tcad-carrier-density.png" alt="Electron and hole density"></td>
<td width="33%"><img src="figures/tcad-electric-field.png" alt="Electric field"></td>
<td width="33%"><img src="figures/tcad-band-diagram.png" alt="Band diagram"></td>
</tr>
<tr>
<td align="center">Carrier densities</td>
<td align="center">Electric field</td>
<td align="center">Band diagram</td>
</tr>
</table>

- **I–V:** exponential forward current; series resistance bends the semilog curve near 0.7–0.8 V.
- **Parametric study:** effect of doping level, device length and material (Si vs Ge). Ge's smaller bandgap gives a higher intrinsic carrier density, so it has a lower forward voltage and a higher current.

<table>
<tr>
<td width="50%"><img src="figures/tcad-iv-semilog.png" alt="I–V semilog"></td>
<td width="50%"><img src="figures/tcad-iv-si-vs-ge.png" alt="Si vs Ge"></td>
</tr>
<tr>
<td align="center">Simulated I–V, semilog scale</td>
<td align="center">Silicon vs germanium</td>
</tr>
<tr>
<td width="50%"><img src="figures/tcad-iv-doping.png" alt="Doping dependence"></td>
<td width="50%"><img src="figures/tcad-iv-geometry.png" alt="Geometry dependence"></td>
</tr>
<tr>
<td align="center">Doping dependence</td>
<td align="center">Geometry (W<sub>n</sub>) dependence</td>
</tr>
</table>

**Authors:** A. Maghsoud, S. Sbrescia
