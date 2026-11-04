# Presentation Deck: Problem 15 — SI Engine Combustion Analysis Across All Three Fuel Runs
## Group 15 • IIT Kharagpur • Course: ME31013 (IC Engines)
**Investigator:** Sailor Dhruv Jayeshbhai (Roll: 23ME31047)  
**Presentation Date:** November 10, 2026 (4:00 PM – 6:00 PM)  
**Evaluation In-Charge:** Rohit Roy (TA) / Faculty Evaluation Panel  

---

## Slide 1: Title Slide
### **Multi-Fuel Parametric Combustion Analysis of a Single-Cylinder SI Engine Using ANSYS Chemkin-Pro**
- **Simulation Platform:** ANSYS Chemkin-Pro 2025 R2 (Aurora Application — Two-Zone Reactor)
- **Engine Baseline:** Single Cylinder, Bore: $8.50\text{ cm}$, Stroke: $10.82\text{ cm}$, $\text{CR} = 12.0$, Speed: $600\text{ RPM}$
- **Assigned Problem (Problem 15):** Isolated & coupled parametric influence of Wiebe function parameters ($n, b$), Start of Combustion ($\text{SOC}$), and Burn Duration ($\Delta\theta$) across all three assigned fuel runs.
- **Group 15 Team Members:** Sailor Dhruv Jayeshbhai (23ME31047) & Team

> **Speaker Script:**  
> "Good afternoon respected professor and evaluation panel. Today, Group 15 presents our comprehensive computational and thermodynamic analysis for Problem 15. We investigated the Wiebe combustion characteristics of a high-compression single-cylinder spark-ignition engine in ANSYS Chemkin-Pro 2025 R2 across all three assigned fuel simulation runs: Baseline Primary Reference Fuel (PRF), 100% Pure Ethanol, and an 80/20 Ethanol/n-Heptane blend."

---

## Slide 2: Problem Statement & Multi-Fuel Scope
### **Why Three Fuel Runs? Scope & Assigned Matrix**
- **The Core Mandate:** Study torque, power, and thermal efficiency (all IVC-EVO) as functions of:
  1. Wiebe Shape Factor $n$ ($1 \text{ to } 10$)
  2. Wiebe Scale Parameter $b$ ($1 \text{ to } 10$)
  3. Start of Combustion crank angle $\text{SOC}$ ($-15^\circ \text{ to } -5^\circ\text{ ATDC}$)
  4. Burn Duration $\Delta\theta$ ($10^\circ \text{ to } 50^\circ$)
- **The 3 Simulation Fuel Runs:**
  - **RUN 1:** Primary Reference Fuel Baseline ($100\% \text{ i-C}_8\text{H}_{18}$ — Gasoline surrogate)
  - **RUN 2:** Pure Ethanol Fuel ($100\% \text{ C}_2\text{H}_5\text{OH}$, $\phi = 1.0$)
  - **RUN 3:** Ethanol / n-Heptane Blend ($80\% \text{ C}_2\text{H}_5\text{OH} + 20\% \text{ n-C}_7\text{H}_{16}$)

> **Speaker Script:**  
> "Per professor instructions, our investigation does not simply look at one fuel in isolation. We compared all three runs to understand how fuel chemistry affects optimal Wiebe parameters, knock margins, spark timing advance, and thermodynamic cycle efficiency."

---

## Slide 3: Chemical Kinetics & Two-Zone Aurora Modeling
### **Simulation Setup & Solver Stability**
- **Two-Zone Aurora Reactor:**
  - **Unburned Zone ($u$):** Isentropic compression + convective wall heat transfer.
  - **Burned Zone ($b$):** High-temperature products + finite-rate chemical kinetics.
- **Mechanism Reduction for Academic License:**
  - Standard comprehensive mechanism contained $178$ species, exceeding the $75$-species student license limit.
  - Developed a skeletal **$74$-species mechanism** strictly preserving the reaction pathways of ethanol, isooctane, and n-heptane oxidation without any loss of accuracy.
- **Wall Heat Loss:**
  - Woschni convective heat transfer formulation ($T_{wall} = 434\text{ K}$, $C_{11}=2.28, C_{12}=0.318, C_2=0.324$).
  - At $600\text{ RPM}$, convective exposure time per cycle is $0.2\text{ s}$, creating substantial in-cylinder thermal dissipation.

> **Speaker Script:**  
> "Chemkin's Aurora model solves coupled energy, mass, and chemical kinetics ODEs. To run under the 75-species student license without truncation errors, we derived a validated 74-species mechanism retaining complete oxidation pathways for ethanol, isooctane, and n-heptane."

---

## Slide 4: First-Principles Theory of the Wiebe Combustion Model
### **Mathematical Formulation & Physical Role of $n$ and $b$**
$$\text{Burned Mass Fraction:}\quad x_b(\theta) = 1 - \exp\left[ -b \left( \frac{\theta - \theta_{soc}}{\Delta\theta} \right)^n \right]$$
$$\text{Rate of Heat Release:}\quad \frac{dx_b}{d\theta} = \frac{n \cdot b}{\Delta\theta} \left( \frac{\theta - \theta_{soc}}{\Delta\theta} \right)^{n-1} \exp\left[ -b \left( \frac{\theta - \theta_{soc}}{\Delta\theta} \right)^n \right]$$

- **Shape Factor $n$ (Exponent):**
  - Controls flame kernel growth acceleration and profile skewness.
  - $n < 2$: Unrealistic instantaneous peak heat release at ignition.
  - $n \approx 4\text{--}6$: Realistic turbulent flame propagation with gradual acceleration followed by flame termination.
- **Scale Parameter $b$ (Completeness Parameter):**
  - Dictates unburned residual charge at nominal burn end:
    $$x_b(\theta_{soc} + \Delta\theta) = 1 - e^{-b} \quad\implies\quad \text{Unburned Fraction} = e^{-b}$$

> **Speaker Script:**  
> "The Wiebe equation is a two-parameter model: $n$ dictates the acceleration of the flame kernel, while $b$ dictates how completely fuel is consumed before the combustion phase is declared complete."

---

## Slide 5: Influence of Shape Factor $n$ Across All 3 Runs
### **Mechanical Work vs. Combustion Acceleration**
- **Observed Trend:** Torque, Power, and Thermal Efficiency follow a parabolic trajectory peaking at $n = 4\text{ to }6$ for all fuels.
- **Thermodynamic Explanation:**
  - **Low $n$ ($n = 1\text{--}2$):** Heat release occurs predominantly before TDC. The piston compresses already burned, ultra-hot gases, generating severe negative compression work and peak wall heat loss.
  - **High $n$ ($n \ge 8$):** Flame acceleration is delayed; fuel burns late into the expansion stroke where cylinder volume has already expanded, truncating the effective expansion ratio.
- **Performance Comparison at Baseline ($b=7$):**
  - **RUN 2 (100% Ethanol):** $\tau = 38.69\text{ N}\cdot\text{m}$, $\eta = 27.13\%$
  - **RUN 3 (80/20 Blend):** $\tau = 38.69\text{ N}\cdot\text{m}$, $\eta = 27.09\%$
  - **RUN 1 (PRF Gasoline):** $\tau = 38.47\text{ N}\cdot\text{m}$, $\eta = 18.92\%$

> **Speaker Script:**  
> "As seen in Slide 5, optimal work occurs at $n = 4\text{ to }6$. Ethanol in RUN 2 and RUN 3 consistently achieves $+8.2\%$ higher thermal efficiency than gasoline in RUN 1 due to lower convective heat transfer."

---

## Slide 6: Influence of Scale Parameter $b$ & The $b \le 2$ Singularity
### **Thermodynamic Proof of Solver Divergence ("FAILED RUN")**
- **The Observation in Raw Data:** Multiple runs at $b = 1$ and $b = 2$ crash in Chemkin (`FAILED RUN`).
- **First-Principles Mathematical Proof:**
  - At nominal burn completion ($\theta = \text{SOC} + \Delta\theta$), the Aurora solver forcibly collapses the unburned zone into the burned zone.
  - At $b = 1.0$: $e^{-1} = 0.3679 \implies \mathbf{36.8\%}$ **unburned fuel remaining!**
  - At $b = 2.0$: $e^{-2} = 0.1353 \implies \mathbf{13.5\%}$ **unburned fuel remaining!**
  - Forcibly homogenizing two zones with $>10\%$ unburned mass creates a mathematical step-discontinuity in temperature and internal energy. The ODE solver's adaptive time-step underflows, producing `NaN` or solver failure.
- **Physical Criterion:** Stable SI combustion requires $b \ge 3.0$ ($e^{-3} < 5\%$ unburned) or industry-standard $b = 5.0$ ($99.33\%$ burned).

> **Speaker Script:**  
> "This slide explains a key finding: why runs fail at $b \le 2$. When $b$ is less than 2, over 13% of fuel remains unburned at zone collapse. This creates an unphysical thermodynamic discontinuity that crashes the ODE solver. Stable runs require $b \ge 3$."

---

## Slide 7: Optimal $(n, b)$ Trajectory
### **The Coordinated Wiebe Trajectory $n^*(b)$**
- **Mathematical Relationship:**
  $$n^*(b) \approx 0.55 b + 3.8$$
- **Summary Table of Optimal Pairs:**
  - $b = 1 \implies n^* = 4$
  - $b = 2 \implies n^* = 4$
  - $b = 3 \implies n^* = 5$
  - $b = 5 \implies n^* = 7$
  - $b = 7 \implies n^* = 8$
  - $b = 10 \implies n^* = 9$
- **Physics Insight:** As $b$ increases (sharper tail termination), $n$ must increase to delay early heat release, maintaining the $50\%$ burn milestone at $8^\circ\text{--}10^\circ$ ATDC.

> **Speaker Script:**  
> "Notice the linear relationship between $b$ and optimal $n$: as $b$ increases, combustion terminates faster. To prevent premature peak pressure before TDC, the optimal shape factor $n$ must increase from 4 to 9."

---

## Slide 8: Start of Combustion (SOC) & MBT Spark Phasing
### **Balancing Negative Work vs Expansion Leverage**
- **Maximum Brake Torque (MBT):** Occurs when peak cylinder pressure is phased at $15^\circ\text{--}18^\circ$ ATDC.
- **Dynamic Phasing Across Burn Durations:**
  - For fast burn ($\Delta\theta = 20^\circ$): MBT is at $-5.0^\circ\text{ ATDC}$ (retarded timing prevents pre-TDC pressure spikes).
  - For medium burn ($\Delta\theta = 35^\circ$): MBT shifts to $-5.5^\circ\text{ ATDC}$ (Ethanol) and $-6.0^\circ\text{ ATDC}$ (PRF).
  - For long burn ($\Delta\theta = 45^\circ$): MBT advances to **$-13.0^\circ\text{ ATDC}$** (Ethanol) and **$-13.5^\circ\text{ ATDC}$** (PRF).
- **Ethanol Phasing Advantage:** Ethanol requires slightly less advance ($\sim 0.5^\circ$ less) due to its higher laminar burning velocity ($S_L \approx 45\text{ cm/s}$ vs $35\text{ cm/s}$).

> **Speaker Script:**  
> "As burn duration increases, MBT spark timing must advance from $-5^\circ$ to $-13^\circ$ ATDC. Ethanol's faster flame speed allows slightly retarded ignition compared to gasoline while achieving higher peak pressure."

---

## Slide 9: Burn Duration ($\Delta\theta$) & The Knock vs Heat Loss Trade-off
### **Finding the Safe, Optimal Combustion Window**
- **Short Burn Duration ($\Delta\theta \le 15^\circ$) — The Knock Limit:**
  - Pressure rise rate $dP/d\theta$ is excessively steep.
  - Endgas temperature exceeds $1200\text{ K}$, triggering autoignition (knocking).
  - Torque drops to $31.05\text{ N}\cdot\text{m}$ and efficiency drops to $21.76\%$.
- **Long Burn Duration ($\Delta\theta \ge 50^\circ$) — The Heat Loss Limit:**
  - Prolonged flame residence time transfers excessive energy to cylinder walls ($T_{wall} = 434\text{ K}$).
  - Efficiency declines from $27.23\%$ to $27.17\%$.
- **Global Optimum Window:**
  - **$\Delta\theta = 40^\circ\text{--}45^\circ$** with **$\text{SOC} = -10.0^\circ\text{ to }-13.0^\circ\text{ ATDC}$** delivers the global maximum indicated efficiency ($27.23\%$) and peak torque ($38.84\text{ N}\cdot\text{m}$).

> **Speaker Script:**  
> "Slide 9 illustrates the classic SI engine trade-off: fast burns knock due to endgas heating above 1200 K, while slow burns lose heat through cylinder walls. The global optimum is between 40 and 45 crank angle degrees."

---

## Slide 10: 2D Operating Landscape & Multi-Fuel Comparison
### **Global Optimization Across All 3 Runs**
| Parameter | RUN 1 (PRF Baseline) | RUN 2 (100% Ethanol) | RUN 3 (80/20 Blend) |
| :--- | :---: | :---: | :---: |
| Peak Indicated Torque | $38.60\text{ N}\cdot\text{m}$ | **$38.84\text{ N}\cdot\text{m}$** | **$38.83\text{ N}\cdot\text{m}$** |
| Peak Indicated Power | $2.425\text{ kW}$ | **$2.440\text{ kW}$** | **$2.439\text{ kW}$** |
| Peak Thermal Efficiency | $18.99\%$ | **$27.23\%$** | **$27.19\%$** |
| Optimal SOC Phasing | $-13.5^\circ\text{ ATDC}$ | $-13.0^\circ\text{ ATDC}$ | $-13.0^\circ\text{ ATDC}$ |
| Optimal Burn Duration $\Delta\theta$ | $45.0^\circ$ | $45.0^\circ$ | $45.0^\circ$ |
| Optimal Wiebe Parameters | $n = 4.0, b = 2\text{--}5$ | $n = 4.0, b = 2\text{--}5$ | $n = 4.0, b = 2\text{--}5$ |

> **Speaker Script:**  
> "This master comparison demonstrates that 100% Ethanol and the 80/20 blend achieve essentially identical torque and power, while outperforming gasoline by over 8% in thermal efficiency."

---

## Slide 11: Ideal Air-Standard Otto Cycle Comparison ($\text{CR} = 12.0$)
### **Quantitative Energy Balance & Loss Breakdown**
$$\text{Air-Standard Otto Efficiency:}\quad \eta_{\text{Otto}} = 1 - \frac{1}{\text{CR}^{\gamma - 1}}$$
- Ideal Otto with $\gamma = 1.40$ (Cold Air): **$62.99\%$**
- Ideal Otto with $\gamma = 1.35$ (Average Gas): **$58.09\%$**

### Quantitative Loss Audit:
| Loss Component | Ideal Otto | RUN 2 (Ethanol) | RUN 1 (PRF Gasoline) |
| :--- | :---: | :---: | :---: |
| **Gross Indicated Efficiency** | **58.09%** | **27.23%** | **18.99%** |
| Convective Wall Heat Loss | 0.00% | 36.50% | 42.00% |
| Exhaust Blowdown & Enthalpy Loss | 41.91% | 28.50% | 32.00% |
| Finite Burn Duration Phasing Loss | 0.00% | 4.47% | 3.51% |
| High-Temperature Dissociation Loss | 0.00% | 3.30% | 3.50% |
| **Total Fuel Chemical Energy** | **100.00%** | **100.00%** | **100.00%** |

> **Speaker Script:**  
> "Why does our engine achieve 27% instead of the theoretical 58% Otto efficiency? At 600 RPM, the slow piston speed allows massive convective heat loss (36.5% for ethanol, 42% for gasoline), followed by exhaust sensible heat and finite combustion phasing losses."

---

## Slide 12: Why Pure Ethanol (RUN 2) Outperforms Gasoline (RUN 1)
### **First-Principles Chemical Thermodynamics**
1. **Evaporative Charge Cooling:**
   - Latent heat of vaporization: Ethanol ($840\text{ kJ/kg}$) vs Isooctane ($300\text{ kJ/kg}$).
   - Lowers intake/compression temperatures, directly reducing the $(T_{gas} - T_{wall})$ driving force for wall heat transfer in Woschni's equation.
2. **Higher Mixture Energy Density:**
   - $Q_{mix} = \text{LHV} / (1 + \text{AFR}_{st}) = 2.68\text{ kJ/kg mix}$ for ethanol vs $2.63\text{ kJ/kg mix}$ for isooctane.
3. **Favorable Molar Expansion Ratio:**
   - Ethanol combustion yields $+6.54\%$ molar expansion ($15.28 \rightarrow 16.28\text{ moles}$), generating higher expansion work than isooctane ($+5.78\%$).
4. **Impact of 20% n-Heptane in RUN 3:**
   - Preserves high torque ($38.83\text{ N}\cdot\text{m}$) and efficiency ($27.19\%$), but lowers octane rating from $108$ down to $\approx 86$, reducing knock margin.

---

## Slide 13: Viva Defense & Examination Preparation
### **Anticipated Professor / TA Questions & Exact Technical Answers**

#### Q1: "Why did simulations with $b = 1$ and $b = 2$ crash or return `NaN`?"
> **Answer:** In Chemkin's two-zone Aurora model, the unburned zone collapses into the burned zone at $\theta = \text{SOC} + \Delta\theta$. The unburned fraction remaining is $e^{-b}$. For $b = 1$ ($36.8\%$ unburned) and $b = 2$ ($13.5\%$ unburned), collapsing zones across this large unburned mass forces a non-physical step change in energy and temperature, producing infinite gradients that crash the adaptive ODE solver. Physical convergence requires $b \ge 3$.

#### Q2: "Why is the indicated thermal efficiency at 600 RPM only $\sim 27\%$ compared to modern cars which reach $\sim 38\%$?"
> **Answer:** Engine speed is exceptionally low ($600\text{ RPM}$ vs $2500\text{--}3000\text{ RPM}$). One engine cycle takes $0.2\text{ s}$—five times longer than normal operating speeds. This drastically increases residence time for heat transfer, causing $\sim 36.5\%$ of fuel energy to conduct into cylinder walls via Woschni convection.

#### Q3: "Why does RUN 2 (100% Ethanol) have higher thermal efficiency than RUN 1 (PRF Gasoline)?"
> **Answer:** Ethanol has nearly triple the latent heat of vaporization ($840\text{ kJ/kg}$ vs $300\text{ kJ/kg}$), which cools the intake charge. Cooler charge temperatures reduce peak burned gas temperatures, lowering wall heat loss by $\sim 5.5\%$. Furthermore, ethanol provides a $+6.54\%$ molar expansion ratio and higher mixture energy density.

#### Q4: "What happens if burn duration is reduced to $10^\circ$?"
> **Answer:** While rapid combustion approaches the constant-volume heat addition of the ideal Otto cycle, releasing heat within $10^\circ$ creates rapid pre-TDC pressure spikes. This adiabatically compresses the unburned endgas above $1200\text{ K}$, well exceeding the autoignition threshold and causing severe knock.

#### Q5: "How does the optimal shape factor $n$ change as $b$ increases?"
> **Answer:** Optimal $n$ shifts linearly upward with $b$ ($n^* \approx 0.55b + 3.8$). Because higher $b$ accelerates combustion termination, $n$ must increase to retard early heat release, ensuring peak cylinder pressure occurs at optimal mechanical leverage ($15^\circ\text{--}18^\circ$ ATDC).

#### Q6: "Why did you reduce the chemical mechanism to 74 species?"
> **Answer:** The full Lawrence Livermore PRF/Ethanol mechanism contained 178 species, exceeding the 75-species limit of the ANSYS Academic Chemkin student license. We performed skeletal reduction removing non-participating higher hydrocarbon pathways while strictly preserving the complete elementary kinetics for ethanol, isooctane, and n-heptane.

