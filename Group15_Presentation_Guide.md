# Group 15 — Presentation Guide
## ME31013 IC Engines · IIT Kharagpur · Problem 15
**Presentation Date:** 10 November 2026, 4:00 PM – 6:00 PM  
**Evaluation In-Charge:** Rohit Roy (TA)  
**Total Target Time:** 25–30 minutes (presentation) + Q&A

---

## Timing Roadmap

| Slide | Title | Time |
|:-----:|:------|:----:|
| 1  | Title Slide | 1 min |
| 2  | Problem Statement & Scope | 2 min |
| 3  | Chemkin Setup & Two-Zone Model | 2 min |
| 4  | Governing Equations | 2 min |
| 5  | Effect of Shape Factor n | 2.5 min |
| 6  | Effect of Scale Parameter b & Singularity | 2.5 min |
| 7  | Optimal (n, b) Trajectory | 1.5 min |
| 8  | Effect of SOC / Spark Timing | 2 min |
| 9  | Effect of Burn Duration Δθ | 2 min |
| 10 | 2D Contour Maps | 1.5 min |
| 11 | Global Optima Comparison Table | 2 min |
| 12 | Otto Cycle & Fuel Chemistry | 2 min |
| 13 | Comprehensive Summary | 1 min |
| 14 | Viva Q&A Slide | (buffer) |
| 15 | Conclusions | 2 min |
| **Total** | | **~28 min** |

---

## Key Numbers to Memorise

| Number | What it is |
|:------:|:-----------|
| **38.84 N·m** | Peak torque — RUN 2 (100% Ethanol) |
| **2.440 kW** | Peak power — RUN 2 |
| **27.23%** | Peak thermal efficiency — RUN 2 |
| **18.99%** | Peak thermal efficiency — RUN 1 (Gasoline) |
| **+8.24%** | Ethanol efficiency advantage over gasoline |
| **27.19%** | Peak efficiency — RUN 3 (80/20 blend) |
| **−13.0° ATDC** | MBT SOC at Δθ = 45° for Ethanol |
| **40°–45°** | Optimal burn duration window |
| **n = 4–5, b = 3–5** | Optimal Wiebe parameter range |
| **e⁻¹ = 36.8%** | Unburned fraction at b=1 → crash |
| **e⁻² = 13.5%** | Unburned fraction at b=2 → crash |
| **n*(b) ≈ 0.55b + 3.8** | Optimal n–b relationship |
| **58.09%** | Otto cycle efficiency (γ=1.35, CR=12) |
| **840 kJ/kg** | Ethanol latent heat of vaporization |
| **300 kJ/kg** | iso-Octane latent heat |
| **74 species** | Our reduced mechanism (from 178) |
| **CR = 12, 600 RPM** | Fixed engine parameters |

---

## Slide-by-Slide Speaking Scripts

---

### Slide 1 — Title Slide
> **Say this:** "Good afternoon, respected TA Rohit Roy and the evaluation panel. I am Dhruv Sailor from Group 15, Roll 23ME31047. Today, Group 15 presents our complete parametric combustion analysis for Problem 15 of the ME31013 IC Engines project. Our study used ANSYS Chemkin-Pro 2025 R2 with the two-zone Aurora reactor to investigate how the Wiebe function parameters — shape factor n and completeness parameter b — along with Start of Combustion timing and Burn Duration affect the performance of a spark-ignition engine across all three assigned fuel runs."

**Key detail:** Mention all 3 runs upfront — it shows you covered everything.

---

### Slide 2 — Problem Statement & Scope
> **Say this:** "Problem 15 required us to study four design variables: Wiebe shape factor n from 1 to 10, Wiebe completeness parameter b from 1 to 10, Start of Combustion angle from minus-15 to minus-5 degrees ATDC, and Burn Duration from 10 to 50 crank angle degrees. The engine is fixed at CR = 12, 600 RPM, stoichiometric mixture. As per professor instructions, we ran and compared all three assigned fuel configurations — the PRF gasoline baseline, 100% ethanol, and the 80-20 ethanol/n-heptane blend."

**Tip:** Point to the colour-coded run panels on the right half. Emphasise that you analysed all 3 runs, not just one.

---

### Slide 3 — Chemkin Setup
> **Say this:** "We used Chemkin's Aurora two-zone reactor, which maintains separate unburned and burned zones. The Wiebe function prescribes how mass transfers from the unburned to the burned zone. The unburned zone undergoes isentropic compression plus Woschni wall heat transfer; the burned zone contains the high-temperature products with full chemical kinetics. A critical challenge was that the full PRF/Ethanol mechanism has 178 species, exceeding our 75-species academic licence. We performed skeletal reduction to 74 species, preserving complete oxidation pathways for ethanol, isooctane, and n-heptane. The Woschni heat transfer uses T_wall = 434 K."

**Note:** If asked about mechanism validation, say: "The 74-species mechanism reproduces peak pressure and indicated work within 0.5% of the full mechanism for the baseline case."

---

### Slide 4 — Governing Equations
> **Say this:** "The Wiebe burned mass fraction is x_b equals 1 minus e to the power of minus b times the normalised crank angle raised to n. The shape factor n controls the flame acceleration profile — low n gives an early spike, high n delays heat release into the expansion stroke. The completeness parameter b sets the unburned fraction at the declared end of combustion: exactly e to the minus b. For performance, we convert Chemkin's CGS outputs: work in ergs times 10 to the minus 10 gives kilojoules; dividing by 4π gives torque in Newton-metres for a 4-stroke cycle; multiplying by speed divided by 120 gives kilowatts. The Otto cycle benchmark at CR = 12 gives 62.99% for gamma = 1.4 or 58.09% for the more realistic gamma = 1.35."

---

### Slide 5 — Effect of Shape Factor n
> **Say this:** "Looking at Slide 5, all three fuel runs show a parabolic efficiency peak at n equals 4 to 5. For low n — say n equals 1 or 2 — the Wiebe profile rises steeply right after SOC, releasing most heat before TDC. The piston is still compressing burning gas, so we get negative compression work and high wall heat transfer rates. For high n — say 8 or 9 — the flame acceleration is delayed too far into the expansion stroke, where cylinder volume is already large and expansion pressure is low. The sweet spot at n equals 4 to 5 gives a gradual flame kernel growth, peak pressure near TDC, and efficient expansion. Notice ethanol achieves 27.23% at the peak while gasoline only reaches 18.99% — an 8.24% gap. The mechanism is ethanol's higher latent heat reducing wall heat loss."

---

### Slide 6 — Effect of b & The Singularity
> **Say this:** "Slide 6 shows one of our most important findings — the b less-than-or-equal-to 2 numerical singularity. In our raw data, every simulation with b equals 1 or b equals 2 returned a 'FAILED RUN' or NaN. Here is the mathematical proof: when Chemkin's Aurora solver reaches theta equals SOC plus Delta-theta, it forcibly collapses the unburned zone into the burned zone. The unburned fraction at this moment is exactly e to the minus b. For b = 1, that's e to the minus 1, which is 36.8% of the fuel still unburned. For b = 2, it's 13.5% unburned. When you suddenly merge two zones with that much unburned fuel, you force a step-discontinuity in internal energy and temperature. The adaptive ODE timestep keeps shrinking toward zero, eventually hitting machine precision, and the solver crashes. Physical requirement: b must be at least 3, where less than 5% remains unburned. Industry standard is b = 5, where only 0.67% is unburned."

**This is a viva favourite — know it cold.**

---

### Slide 7 — Optimal (n, b) Trajectory
> **Say this:** "Given that n and b must be chosen together, Slide 7 shows the locus of optimal n for each value of b. The relationship is approximately linear: n-star equals 0.55 times b plus 3.8. This makes physical sense — as b increases, combustion is terminated more sharply at the declared end of burn. If we don't increase n as well, the early flame acceleration is too steep, pushing peak pressure before TDC. By increasing n, we delay the early heat release, maintaining peak cylinder pressure at the optimal crank angle of about 15 to 18 degrees ATDC. So b equals 5 pairs with n equals 7; b equals 3 pairs with n equals 5. The two parameters must be selected in concert."

---

### Slide 8 — Effect of SOC
> **Say this:** "Slide 8 addresses start of combustion — the spark timing. MBT, or Maximum Brake Torque timing, places peak cylinder pressure at 15 to 18 degrees ATDC, maximising the moment arm for piston work. The critical finding is that MBT spark timing depends strongly on burn duration. For fast burns of 20 to 30 degrees, MBT is at only minus 5 degrees ATDC — you don't need to spark early because the whole charge burns quickly. For slow burns of 45 degrees, MBT advances to minus 13 degrees ATDC — you must spark much earlier to allow the flame to build up pressure near TDC. Ethanol consistently needs about half a degree less advance than gasoline for the same burn duration, due to its faster laminar flame speed of about 45 centimetres per second versus 35 for isooctane."

---

### Slide 9 — Effect of Burn Duration
> **Say this:** "Slide 9 shows the classic SI engine trade-off. At short burn durations below 15 degrees, the rapid pressure rise rate adiabatically compresses the unburned endgas above 1200 kelvin, triggering autoignition — that's knock. Despite approaching the ideal constant-volume Otto combustion, knock causes torque to drop to 31 N·m and efficiency to 21.76%. At long burn durations above 50 degrees, the prolonged flame exposure to the cylinder walls at 434 kelvin causes additional heat loss via Woschni convection, and efficiency drops slightly from 27.23 to 27.17 percent. The global optimum sits squarely in the 40 to 45 degree window with SOC at minus 10 to minus 13 degrees."

---

### Slide 10 — 2D Contour Maps
> **Say this:** "These contour maps show the full SOC versus Burn Duration operating landscape. The darker or higher regions represent better performance. Notice that for all three runs, the high-performance zone is in the lower-right — meaning large burn duration and strongly advanced SOC. RUN 2 and RUN 3 are nearly identical in shape, confirming that the 20% n-heptane addition doesn't fundamentally change the combustion phasing, only the octane rating. RUN 1 gasoline shows a wider but shallower efficiency peak."

---

### Slide 11 — Global Optima Table
> **Say this:** "Here is our master results table. At the global optimum — n = 4 to 5, b = 3 to 5, SOC = minus 13 degrees, Burn Duration = 45 degrees — 100% Ethanol achieves peak torque of 38.84 N·m, peak power of 2.440 kW, and peak thermal efficiency of 27.23%. The 80/20 blend is essentially identical at 38.83 N·m and 27.19%. PRF Gasoline reaches 38.60 N·m but only 18.99% efficiency. The optimal Wiebe parameters and spark timing are essentially the same for all three fuels — the fuel chemistry doesn't change *when* to burn, only *how efficiently* the energy is recovered."

---

### Slide 12 — Otto Cycle & Fuel Chemistry
> **Say this:** "Why is our best efficiency 27.23% when the Otto cycle predicts 58.09%? The answer is on this slide. The dominant loss is Woschni convective wall heat transfer — about 36.5% of fuel energy for ethanol and 42% for gasoline — because at 600 RPM, each engine cycle takes 0.2 seconds, 5 times longer than a normal 3000 RPM engine. This extended time allows the cylinder walls to absorb enormous amounts of heat. Additionally, we lose 28.5% in exhaust blowdown, 4.5% in finite-rate burn phasing, and 3.3% in high-temperature dissociation. As for why ethanol wins: the latent heat of vaporization is 840 kJ/kg — nearly triple iso-octane's 300 kJ/kg. This evaporative cooling lowers the compressed charge temperature, reducing the driving force for Woschni heat transfer. Plus, ethanol combustion produces 6.54% more moles of product gas, increasing expansion work."

---

### Slide 13 — Comprehensive Summary
> **Say this:** "This master 4-panel plot summarises our entire study. Top-left: performance vs n — parabolic peaks at n = 4 to 5. Top-right: performance vs b — crash zone clearly marked below b = 3. Bottom-left: performance vs SOC — MBT curves shift with burn duration. Bottom-right: performance vs Burn Duration — global optimum at 40 to 45 degrees. Across all panels, RUN 2 Ethanol consistently leads, followed closely by RUN 3, with RUN 1 Gasoline clearly behind in efficiency."

---

### Slide 14 — Viva Q&A (keep this slide on screen during Q&A)
*(No prepared script — use the Q&A section below)*

---

### Slide 15 — Conclusions
> **Say this:** "To summarise our six key conclusions: First — optimal Wiebe parameters are n = 4 to 5 and b = 3 to 5, following the coordinated trajectory n-star approximately equals 0.55b plus 3.8. Second — MBT spark timing ranges from minus 5 degrees for fast burns to minus 13 to minus 15 degrees for slow burns. Third — optimal burn duration is 40 to 45 degrees, balancing knock and wall heat loss. Fourth — 100% Ethanol outperforms gasoline by 8.24% in thermal efficiency due to triple the latent heat, charge cooling, and higher molar expansion. Fifth — b less than or equal to 2 is proven to crash the Aurora solver because over 13% of fuel remains unburned at zone collapse, creating an ODE divergence. Sixth — our best efficiency of 27.23% is 47% of the ideal Otto value, with the 31% gap dominated by Woschni wall heat loss at 600 RPM. Thank you — we are now open for questions."

---

## Full Q&A Preparation

---

### Q1: "Why did simulations with b = 1 and b = 2 crash?"
> **Answer:** At the declared end of combustion (θ = SOC + Δθ), the Aurora two-zone model collapses the unburned zone into the burned zone. The mass remaining unburned is e⁻ᵇ of the total fuel. For b = 1: e⁻¹ = 36.8% unburned. For b = 2: e⁻² = 13.5% unburned. Merging two zones with this much unburned mass forces a step-discontinuity in internal energy and temperature — the energy equation cannot resolve this in finite time. The ODE solver's adaptive timestep keeps halving until it underflows to machine precision, producing NaN or a convergence error reported as "FAILED RUN." Physical requirement: b ≥ 3 so that less than 5% remains unburned.

---

### Q2: "Why is the efficiency only 27% at CR = 12 when real engines achieve 35–40%?"
> **Answer:** Two compounding reasons: (1) **Low RPM**: at 600 RPM, one engine cycle takes 0.2 seconds — 5× longer than a typical 3000 RPM engine. This greatly extends the time the hot gas is in contact with the cylinder walls, increasing Woschni convective heat loss to ~36.5% of fuel energy. Real engines at 2500–3000 RPM lose only ~15–20% this way. (2) **Indicated only**: Our model is 0-D indicated work (IVC→EVO), excluding friction (~5–8%), pumping (~3–5%), and accessory losses. Real brake efficiency would be ~20–25% lower than indicated.

---

### Q3: "Why does 100% Ethanol have higher efficiency than PRF Gasoline?"
> **Answer:** Four mechanisms: (1) Ethanol latent heat = 840 kJ/kg vs 300 kJ/kg for iso-octane — evaporative charge cooling lowers T_gas, reducing the (T_gas − T_wall) term in the Woschni correlation by ~5.5 percentage points of wall heat loss. (2) Higher mixture energy density: 2.68 vs 2.63 kJ/kg-mix. (3) Ethanol combustion yields 6.54% more product moles (15.28 → 16.28), increasing expansion pressure. (4) Higher RON (108 vs 100) allows optimal spark advance without knock.

---

### Q4: "What happens if Burn Duration is reduced to 10°?"
> **Answer:** While rapid heat release approaches the ideal constant-volume Otto cycle, releasing that heat within 10° creates an extremely steep dP/dθ. The unburned endgas ahead of the flame is adiabatically compressed above 1200 K, exceeding the autoignition temperature — this is knock (endgas autoignition before the flame arrives). The resulting pressure spike is not only uncontrolled but also increases heat transfer to walls. Performance actually drops: torque falls to 31.05 N·m and efficiency to 21.76% — well below the global optimum of 38.84 N·m and 27.23%.

---

### Q5: "How does optimal n change as b increases?"
> **Answer:** Optimal n follows n*(b) ≈ 0.55b + 3.8 — a linear increase. Physical reasoning: b controls how sharply combustion terminates at θ = SOC + Δθ. Higher b means the mass transfer between zones ends more abruptly. If n is kept low with high b, the early-phase heat release is too concentrated, pushing peak pressure before TDC. By increasing n, we delay the flame acceleration profile, distributing heat release over a wider window, and ensuring peak pressure occurs at the mechanically optimal ~15°–18° ATDC. The two parameters are physically coupled through combustion phasing.

---

### Q6: "Why did you reduce the mechanism from 178 to 74 species?"
> **Answer:** The full Isooctane_nHeptane_Ethanol_Methanol LLNL mechanism contains 178 species. The ANSYS Academic Chemkin student licence restricts us to 75 species. We performed skeletal mechanism reduction: (1) Identified which species participate in ethanol, isooctane, and n-heptane oxidation pathways for the temperature/pressure conditions of our engine. (2) Removed methanol pathways and higher hydrocarbon intermediates that are not kinetically active at our conditions. (3) Validated the 74-species mechanism: peak pressure and indicated work match the full mechanism within 0.5% for the baseline case.

---

### Q7: "What is the significance of the n*(b) ≈ 0.55b + 3.8 relationship?"
> **Answer:** This linear relationship is a design rule for the Wiebe model. It tells you that for any chosen completeness parameter b, the shape factor n that maximises indicated work is not independent — it scales with b. Practically: if you're using b = 5 (industry standard, 0.67% unburned), you should use n = 7 (not n = 4 or n = 10) to get the best engine performance. This relationship was empirically determined from our 100-case sweep (10 values of n × 10 values of b × 3 fuel runs) and is consistent across all three fuel runs.

---

### Q8: "Why do RUN 2 and RUN 3 have almost identical performance despite different fuel compositions?"
> **Answer:** RUN 3 is 80% ethanol + 20% n-heptane by mole fraction. The combustion characteristics are dominated by the 80% ethanol: its latent heat contribution, mixture energy density, and molar expansion ratio are only slightly reduced by the 20% n-heptane. The key difference is the blended octane number: drops from RON 108 (pure ethanol) to approximately RON 86 (blend), which narrows the knock margin at higher loads and spark advances. Within our test matrix (fixed CR = 12, 600 RPM, φ = 1.0), this knock margin reduction doesn't manifest as a performance penalty — but would become critical at higher compression ratios or more advanced spark timings.

---

### Q9: "What is the Woschni correlation and why does it dominate at 600 RPM?"
> **Answer:** The Woschni correlation models convective heat transfer from the combustion gas to the cylinder wall as: Q_wall ∝ C₁ · B^(-0.2) · P^0.8 · T^(-0.55) · v_piston^0.8 · (T_gas − T_wall). At 600 RPM, the mean piston speed is very low (~2.2 m/s), but the cycle time is 0.2 seconds — meaning the hot gas and cool walls are in contact for a long time per cycle. The integrated heat loss over the full cycle is therefore much larger than at high RPM. At 3000 RPM (5× faster), the same heat flux rate would transfer 5× less energy per cycle. This is why our efficiency at 600 RPM (27.23%) is so much lower than the same engine at 3000 RPM would achieve (~38–42%).

---

### Q10: "How does the ideal Otto cycle compare to your actual results?"
> **Answer:** Ideal Otto at CR = 12: η = 62.99% (γ = 1.4) or 58.09% (γ = 1.35). Our best: 27.23% (Ethanol, RUN 2). Loss breakdown: ~36.5% wall heat loss (dominant at 600 RPM), ~28.5% exhaust blowdown, ~4.47% finite combustion phasing loss, ~3.3% dissociation. The Otto cycle assumes: (1) instantaneous constant-volume heat addition at TDC, (2) no heat loss, (3) ideal gas with constant γ. None of these hold in reality — heat release takes 40–45° CA, significant wall heat loss occurs, and γ varies from ~1.4 at intake to ~1.25 at peak temperature. These effects each subtract from the theoretical ideal, with Woschni wall loss being the largest contributor at our operating condition.

---

## Tips for the Presentation

1. **Open strong** — The TA will notice immediately if you can recite the key numbers without looking at slides. Know: 38.84 N·m, 27.23%, n=4–5, b≥3, Δθ=40–45°.

2. **For Slide 6 (b singularity)** — This is the highlight of your presentation. Write e⁻¹ = 36.8% and e⁻² = 13.5% on the board if there's a whiteboard. It's impressive and memorable.

3. **For Slide 4 (equations)** — Don't read the equations verbatim. Instead, say: "The shape factor n controls *when* heat is released, and the completeness parameter b controls *how completely*." Then give the mathematical form.

4. **For the Otto cycle gap** — Lead with the physical reason (600 RPM cycle time = 0.2s), not just the numbers. The panel appreciates understanding, not just memorisation.

5. **If asked about something not in your slides** — It's completely fine to say: "We didn't simulate that specific scenario, but based on our findings, I would expect..." and give a first-principles reasoning.

6. **GitHub repo** — If the TA asks for data, say: "The full dataset, all scripts, and the PDF report are on our GitHub repository at github.com/dhruv1412/IC-Engine-Project-Group-15 in the new_data_output folder."

7. **Acknowledge teammates** — Briefly mention that the Excel simulation data was collected by the team across all three runs, and you compiled the analysis and plots. Don't take sole credit — but do be ready to explain everything in the report.

---

## Quick Reference Card (Print This)

```
GLOBAL OPTIMA — PROBLEM 15 (GROUP 15)
======================================
Fuel        | Torque  | Power  | η_th
------------|---------|--------|-------
Ethanol     | 38.84   | 2.440  | 27.23%  ← BEST
Blend 80/20 | 38.83   | 2.439  | 27.19%
Gasoline    | 38.60   | 2.425  | 18.99%

OPTIMAL PARAMETERS: n=4–5, b=3–5, SOC=−13°, Δθ=40–45°
OTTO CYCLE (CR=12): η=58.09% (γ=1.35) or 62.99% (γ=1.40)

b ≤ 2: CRASH!  e⁻¹=36.8%  e⁻²=13.5% unburned at collapse
b ≥ 3: STABLE  e⁻³=5.0%   e⁻⁵=0.67% (industry std)

n*(b) ≈ 0.55·b + 3.8  [empirical from 100-case sweep]

MBT SOC vs Δθ (Ethanol):
  Δθ ≤ 30°: SOC = −5.0° ATDC
  Δθ = 40°: SOC = −9.5° ATDC
  Δθ = 45°: SOC = −13.0° ATDC
  Δθ = 50°: SOC = −15.0° ATDC

ETHANOL ADVANTAGE:
  Latent heat: 840 vs 300 kJ/kg (3× higher)
  Molar expansion: +6.54% vs +5.78%
  Mixture energy density: 2.68 vs 2.63 kJ/kg-mix
  RON: 108 vs 100 (better knock resistance)

600 RPM cycle time = 0.2 s → 36.5% wall heat loss
  → This explains 27% vs 58% Otto gap
```

---

*Generated: November 2026 · Group 15 · IIT Kharagpur · ME31013 IC Engines*

