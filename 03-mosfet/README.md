# 03 — MOSFET: TCAD Design Study and Experimental DC/AC Characterization

[Full report (PDF)](report.pdf) · June 2026

## A. TCAD: 130 nm n-MOSFET (Synopsys Sentaurus)

- **Band diagrams** along vertical and horizontal cutlines at equilibrium, at V<sub>GS</sub> = 1.5 V / V<sub>DS</sub> = 0, and at V<sub>GS</sub> = V<sub>DS</sub> = 1.5 V. They show inversion forming, and the quasi-Fermi levels splitting once current flows.

<table>
<tr>
<td width="33%"><img src="figures/tcad-bands-equilibrium.png" alt="Bands at equilibrium"></td>
<td width="33%"><img src="figures/tcad-bands-vgs.png" alt="Bands at VGS = 1.5 V"></td>
<td width="33%"><img src="figures/tcad-bands-vgs-vds.png" alt="Bands at VGS = VDS = 1.5 V"></td>
</tr>
<tr>
<td align="center">Equilibrium</td>
<td align="center">V<sub>GS</sub> = 1.5 V, V<sub>DS</sub> = 0</td>
<td align="center">V<sub>GS</sub> = V<sub>DS</sub> = 1.5 V</td>
</tr>
</table>

- **Substrate doping sweep** (10<sup>17</sup>, 5×10<sup>17</sup>, 10<sup>18</sup> cm<sup>-3</sup>; L<sub>G</sub> = 130 nm, t<sub>ox</sub> = 2.5 nm): V<sub>th</sub> falls as N<sub>sub</sub> falls, because there is less bulk depletion charge and a smaller φ<sub>F</sub>.
- **Oxide thickness sweep** (2.5, 10, 20 nm): thicker oxide lowers C<sub>ox</sub> and weakens gate control. V<sub>th</sub> rises sharply and the subthreshold slope degrades.

Both trends are explained with V<sub>th</sub> = V<sub>FB</sub> + 2φ<sub>F</sub> + √(4ε<sub>Si</sub>qN<sub>sub</sub>φ<sub>F</sub>)/C<sub>ox</sub>.

<table>
<tr>
<td width="50%"><img src="figures/tcad-substrate-doping.png" alt="Substrate doping sweep"></td>
<td width="50%"><img src="figures/tcad-oxide-thickness.png" alt="Oxide thickness sweep"></td>
</tr>
<tr>
<td align="center">I<sub>D</sub>–V<sub>GS</sub> vs substrate doping</td>
<td align="center">I<sub>D</sub>–V<sub>GS</sub> vs oxide thickness</td>
</tr>
</table>

## B. Lab: experimental DC and AC characterization

**DC**

| Parameter | Method | Value |
|---|---|---|
| Threshold voltage V<sub>th</sub> | Linear extrapolation of I<sub>D</sub>–V<sub>G</sub> at V<sub>DS</sub> = 1 V | **3.068 V** |
| On-resistance R<sub>ON</sub> | Inverse slope of I<sub>D</sub>–V<sub>D</sub> in deep ohmic region (0–0.1 V, max V<sub>G</sub>) | **9.1 Ω** |
| Subthreshold slope SS | Semilog I<sub>D</sub>–V<sub>G</sub>, 2.1 V < V<sub>GS</sub> < 2.7 V | **237.5 mV/dec** |

<table>
<tr>
<td width="50%"><img src="figures/lab-id-vg-semilog.png" alt="ID–VG semilog"></td>
<td width="50%"><img src="figures/lab-id-vd-linear.png" alt="ID–VD linear"></td>
</tr>
<tr>
<td align="center">I<sub>D</sub>–V<sub>G</sub>, semilog</td>
<td align="center">I<sub>D</sub>–V<sub>D</sub>, linear</td>
</tr>
<tr>
<td width="50%"><img src="figures/lab-vth-extraction.png" alt="Threshold voltage extraction"></td>
<td width="50%"><img src="figures/lab-subthreshold-slope.png" alt="Subthreshold slope extraction"></td>
</tr>
<tr>
<td align="center">V<sub>th</sub> extraction</td>
<td align="center">Subthreshold slope extraction</td>
</tr>
</table>

Transconductance g<sub>m</sub> rises with V<sub>DS</sub> and then drops at high V<sub>GS</sub> because of mobility degradation (surface scattering in the strong vertical field).

**AC (MOS capacitor)**

- Multi-frequency C–V (1 kHz to 1 MHz) shows accumulation, depletion and inversion. G–V peaks near the depletion–inversion transition point to interface states and series resistance.
- **1 MHz C–V hysteresis:** a flat-band shift between forward and backward sweeps, caused by charge trapping at the Si/SiO₂ interface and in the oxide.
- **Parameter extraction** (effective area 0.003 cm²): C<sub>ox</sub> = 4.54×10<sup>-10</sup> F, C<sub>min</sub> = 2.29×10<sup>-10</sup> F → **t<sub>ox</sub> = 22.84 nm**, **N<sub>A</sub> = 2.54×10<sup>17</sup> cm<sup>-3</sup>**.

<table>
<tr>
<td width="50%"><img src="figures/lab-cv-multifrequency.png" alt="C–V at several frequencies"></td>
<td width="50%"><img src="figures/lab-gv-multifrequency.png" alt="G–V at several frequencies"></td>
</tr>
<tr>
<td align="center">C–V, 1 kHz to 1 MHz</td>
<td align="center">G–V, 1 kHz to 1 MHz</td>
</tr>
<tr>
<td width="50%"><img src="figures/lab-cv-hysteresis.png" alt="C–V hysteresis"></td>
<td width="50%"><img src="figures/lab-tox-na-extraction.png" alt="tox and NA extraction"></td>
</tr>
<tr>
<td align="center">Forward/backward sweep at 1 MHz</td>
<td align="center">t<sub>ox</sub> and N<sub>A</sub> extraction</td>
</tr>
</table>

**Authors:** L. Ferrari, A. Maghsoud, S. Sbrescia
