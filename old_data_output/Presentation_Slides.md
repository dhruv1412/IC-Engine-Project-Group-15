# Presentation Slide Deck: Problem 15
## Ethanol SI Engine: Study of Wiebe Function Parameters & Combustion Phasing

**Course:** Internal Combustion Engines  
**Presentation Date:** November 3, 2026 (4:00 PM – 6:00 PM)  
**Presenter:** Sailor Dhruv Jayeshbhai (Roll No: 23ME31047) | Group 15  
**Department:** Mechanical Engineering, IIT Kharagpur  

---

### Slide 1: Title & Project Overview
- **Title:** Parametric Investigation of Wiebe Heat Release and Combustion Phasing in an Ethanol-Fueled SI Engine
- **Tool:** ANSYS Chemkin-Pro 2025 R2 (Two-Zone SI Engine Zonal Model)
- **Key Focus:**
  - Influence of Wiebe shape factor $n$ ($1.0$ to $5.0$)
  - Influence of Wiebe completeness factor $b$ ($2.0$ to $10.0$)
  - Start of Combustion ($\text{SOC}$) sweep ($-15^\circ$ to $-5^\circ$) $\rightarrow$ Finding **MBT Timing**
  - Burn Duration ($\Delta\theta$) sweep ($10^\circ$ to $50^\circ$) $\rightarrow$ Identifying the **Knock Limit**
  - First-principles comparison with ideal air-standard Otto Cycle

> **🗣️ Speaking Script (30 sec):**  
> *"Good afternoon professors and fellow classmates. Today, I am presenting Group 15's project on the influence of Wiebe function heat release parameters on an ethanol-fueled spark-ignition engine using ANSYS Chemkin-Pro 2025 R2. We will look at how the mathematical parameters of the Wiebe function translate directly to in-cylinder thermodynamics, torque production, thermal efficiency, and knocking limits."*

---

### Slide 2: Engine Geometry & Kinetics Mechanism
- **Engine Architecture:**
  - Bore = $85\text{ mm}$, Stroke = $108.2\text{ mm}$
  - Displacement = $614\text{ cm}^3$, Compression Ratio ($\text{CR}$) = $12.0$
  - Engine Speed = $600\text{ RPM}$, Connecting rod ratio ($L/R$) = $3.3$
- **Fuel & Chemistry:**
  - Fuel: Pure Ethanol ($\text{C}_2\text{H}_5\text{OH}$, $\phi = 1.0$, stoichiometric)
  - Kinetics Mechanism: Reduced chemical mechanism tailored for student license constraints ($74\text{ species}$, $341\text{ elementary reactions}$)
  - Heat Transfer: Woschni convective wall correlation active

> **🗣️ Speaking Script (45 sec):**  
> *"Our engine has a compression ratio of 12:1 and operates at 600 RPM. We modeled pure ethanol combustion under stoichiometric conditions using a 74-species, 341-reaction chemical kinetics mechanism in Chemkin-Pro. The closed-cycle simulation runs from Intake Valve Closure at -120.2° ATDC to Exhaust Valve Opening at +139.8° ATDC."*

---

### Slide 3: Baseline Cylinder Indicator Diagram ($P$-$\theta$)
- **Baseline Conditions:** $n = 4.0$, $b = 7.0$, $\text{SOC} = -14.5^\circ\text{ ATDC}$, $\Delta\theta = 45.6^\circ$
- **Peak Cylinder Pressure:** $46.5\text{ atm}$ ($47.1\text{ bar}$) at $20.0^\circ\text{ ATDC}$
- **Key Metrics (IVC to EVO):**
  - Indicated Work: $0.4734\text{ kJ}$ ($473.4\text{ J/cycle}$)
  - IMEP: $7.710\text{ bar}$
  - Indicated Power: $2.367\text{ kW}$
  - Indicated Torque: $37.67\text{ N}\cdot\text{m}$
  - Indicated Thermal Efficiency: $18.53\%$
  - $50\%$ Mass Burned ($\text{CA}_{50}$): $14.22^\circ\text{ ATDC}$

> **🗣️ Speaking Script (45 sec):**  
> *"Here is our baseline in-cylinder pressure curve extracted directly from the Chemkin visualizer. Compression starts at 1 atm, reaches 22 atm at TDC, and combustion ramps cylinder pressure to a peak of 46.5 atm at 20° ATDC. Baseline thermal efficiency is 18.53% with CA50 at 14.22° ATDC."*

---

### Slide 4: Parameter Sensitivity — Executive Summary (4-in-1 Master Plot)
*(Display `plot_comprehensive_summary.png` on this slide)*

- **Panel (a) Wiebe $n$:** Torque rises from $30.25$ to $38.17\text{ N}\cdot\text{m}$ ($\eta: 14.88\% \rightarrow 18.78\%$)
- **Panel (b) Wiebe $b$:** Failure at $b=2.0$; peaks at $b=3.0$ ($38.49\text{ N}\cdot\text{m}$) and gently declines at higher $b$
- **Panel (c) SOC:** Classic parabola; peaks precisely at **$\text{SOC} = -10.0^\circ\text{ ATDC}$** ($38.58\text{ N}\cdot\text{m}$, $18.98\%$)
- **Panel (d) Burn Duration:** Severe **knocking at $\Delta\theta = 10^\circ$**; optimum smooth operation at $\Delta\theta \approx 45.6^\circ$

> **🗣️ Speaking Script (1 min):**  
> *"This master plot summarizes our four core findings. As we see in panel (a), increasing the Wiebe exponent n shifts heat release away from pre-TDC compression into early expansion, boosting efficiency. In panel (b), we discovered a numerical boundary at b=2, while b=3 to 5 gives peak torque. Panel (c) clearly identifies our MBT spark timing at -10° ATDC. In panel (d), fast burns below 20° trigger endgas knock, while 45° yields maximum safe torque."*

---

### Slide 5: Deep Dive — Shape Exponent $n$ & Combustion Phasing
- **The Equation:** $x_b = 1 - \exp[-b ((\theta - \theta_0)/\Delta\theta)^{n+1}]$
- **Why $n=1$ fails:** 
  - $\text{CA}_{50} = -0.15^\circ\text{ ATDC}$! Half the fuel burns before TDC!
  - Creates severe **negative compression work** (piston fights expanding gas).
- **Why $n=4\text{--}5$ excels:** 
  - Produces an S-curve delay. $\text{CA}_{50}$ occurs at $+14^\circ\text{ to }+16^\circ\text{ ATDC}$.
  - Peak pressure occurs when crank arm is perpendicular to connecting rod, maximizing crank torque.

---

### Slide 6: Deep Dive — Parameter $b$ & The $b=2.0$ Singularity
- **Combustion Completeness:** $x_b(\text{end}) = 1 - e^{-b}$
  - $b = 2.0 \implies 86.47\%$ burned ($13.5\%$ unburned fuel remaining)
  - $b = 5.0 \implies 99.33\%$ burned
  - $b = 7.0 \implies 99.91\%$ burned
- **The Solver Failure:** 
  - At $b=2.0$, terminating the flame with $13.5\%$ unburned fuel creates a mass/energy discontinuity in Chemkin's two-zone solver, returning `NaN` / `Infinity`.
- **The Physical Optimum:** 
  - $b=3.0$ gives highest torque ($38.49\text{ N}\cdot\text{m}$) because lower peak temperatures reduce wall heat losses.

---

### Slide 7: Spark Timing ($\text{SOC}$) & MBT Optimization
- **Sweep Range:** $-15^\circ, -12^\circ, -10^\circ, -8^\circ, -5^\circ\text{ ATDC}$
- **Optimal MBT Timing:** **$\text{SOC} = -10.0^\circ\text{ ATDC}$**
  - Indicated Work = $0.4848\text{ kJ}$
  - Indicated Torque = $38.58\text{ N}\cdot\text{m}$
  - Indicated Thermal Efficiency = $18.98\%$
  - $\text{CA}_{50} = +20.71^\circ\text{ ATDC}$
- **Trade-offs:**
  - $\text{SOC} < -10^\circ$ (Over-advanced): Increased compression work & heat loss.
  - $\text{SOC} > -10^\circ$ (Retarded): Heat released late into expanding volume; lost expansion ratio.

---

### Slide 8: Burn Duration ($\Delta\theta$) & The Knock Limit
- **Knock Detection at $\Delta\theta = 10^\circ$:**
  - Chemkin output: `ENDGAS KNOCKING INFORMATION: Thermal ignition CA = 4.416° ATDC (T > 1200 K)`.
  - Flash-combustion before TDC forces endgas temperature past autoignition limit.
  - Efficiency plummets to $12.79\%$.
- **Normal Flame Regime ($\Delta\theta \ge 20^\circ$):**
  - Smooth flame propagation without knock.
  - Optimum at $\Delta\theta = 45.6^\circ$ ($38.58\text{ N}\cdot\text{m}$, $18.98\%$).

---

### Slide 9: Comparison with Ideal Otto Cycle
- **Air-Standard Otto Cycle ($\text{CR} = 12$):**
  - $\gamma = 1.40\text{ (Cold air)} \implies \eta_{\text{Otto}} = \mathbf{62.99\%}$
  - $\gamma = 1.35\text{ (Combustion mixture)} \implies \eta_{\text{Otto}} = \mathbf{58.09\%}$
- **Simulated Indicated Efficiency:** $\mathbf{18.98\%}$
- **First-Principles Loss Breakdown:**
  1. **Wall Heat Losses ($\sim 24\%$):** Low speed (600 RPM) gives large residence time for Woschni convective cooling.
  2. **Finite Burn Duration ($\sim 6.5\%$):** Heat added during expansion rather than isochorically at TDC.
  3. **High-Temperature Dissociation ($\sim 5.0\%$):** Endothermic dissociation ($\text{CO}_2 \rightleftharpoons \text{CO} + \frac{1}{2}\text{O}_2$) at $T > 2200\text{ K}$.
  4. **Variable Specific Heats ($\sim 3.6\%$):** $\gamma$ decreases from $1.4$ to $\sim 1.28$ during combustion.

---

### Slide 10: Conclusions & Optimal Operating Point
- **Final Recommended Operating Parameters:**
  - **Wiebe Form Factor:** $n = 4.0\text{ to }5.0$
  - **Wiebe Completeness:** $b = 3.0\text{ to }5.0$
  - **Start of Combustion:** $\text{SOC} = -10.0^\circ\text{ ATDC}$ (MBT)
  - **Burn Duration:** $\Delta\theta = 45.6^\circ$
  - **Delivered Output:** $W_i = 0.485\text{ kJ}$, $\tau_i = 38.58\text{ N}\cdot\text{m}$, $P_i = 2.42\text{ kW}$, $\eta_i = 18.98\%$

---

### Slide 11: Expected Viva Questions & Model Answers

**Q1: Why did your simulation crash / give NaN at $b = 2.0$?**  
*Answer:* The Wiebe burned fraction at the end of duration is $1 - e^{-b}$. At $b=2.0$, only $86.5\%$ of fuel is burned, leaving $13.5\%$ unburned reactant. Chemkin's two-zone solver cannot collapse a non-empty unburned zone into the expansion phase without an energy discontinuity, resulting in division by zero.

**Q2: Why did $\Delta\theta = 10^\circ$ knock while $\Delta\theta = 40^\circ$ did not?**  
*Answer:* A 10° burn releases almost all fuel energy before TDC, creating an extreme pressure and temperature spike that adiabatically compresses the unburned endgas above its 1200 K autoignition threshold, triggering thermal knock.

**Q3: Why is actual thermal efficiency ~19% when Otto efficiency is ~58%?**  
*Answer:* Three major thermodynamic realities: first, our simulation runs at 600 RPM, giving a long residence time (200 ms/cycle) that causes enormous convective wall heat losses (~24%); second, finite burn duration loses work compared to instantaneous isochoric combustion; third, high-temperature dissociation of $\text{CO}_2$ and $\text{H}_2\text{O}$ absorbs energy endothermically.
