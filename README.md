# IC Engine Project — Problem 15: Multi-Fuel SI Engine Combustion Analysis
**Department of Mechanical Engineering, Indian Institute of Technology Kharagpur**  
**Group 15** | Presentation Date: November 10, 2026 (4:00 PM – 6:00 PM)  

---

## 📌 Project Overview & Multi-Run Study

This project investigates the closed-cycle performance of a single-cylinder four-stroke Spark-Ignition (SI) engine ($B=8.50\text{ cm}$, $S=10.82\text{ cm}$, $\text{CR}=12.0$, $600\text{ RPM}$) modeled in **ANSYS Chemkin-Pro 2025 R2** (Aurora Two-Zone IC Engine Model). 

Per evaluation instructions, the complete parameter study is conducted across **all three assigned fuel simulation runs**:
- **RUN 1:** Primary Reference Fuel Baseline ($100\% \text{ i-C}_8\text{H}_{18}$ — Gasoline surrogate, $\text{RON}=100$).
- **RUN 2:** 100% Pure Ethanol ($\text{C}_2\text{H}_5\text{OH}$, $\phi=1.0$, $\text{RON}=108$).
- **RUN 3:** Ethanol / n-Heptane Blend ($80\% \text{ C}_2\text{H}_5\text{OH} + 20\% \text{ n-C}_7\text{H}_{16}$).

### Key Performance Findings:
1. **Ethanol Performance Superiority:** Pure Ethanol (RUN 2) delivers **$27.23\%$ indicated thermal efficiency** and **$38.84\text{ N}\cdot\text{m}$ indicated torque** (Power: $2.44\text{ kW}$), outperforming gasoline (RUN 1: $18.99\%$ and $38.60\text{ N}\cdot\text{m}$) due to high latent heat of vaporization ($840\text{ kJ/kg}$) charge cooling and favorable molar expansion ($+6.54\%$).
2. **Blend Performance (RUN 3):** The 80/20 blend achieves **$27.19\%$ efficiency** and **$38.83\text{ N}\cdot\text{m}$ torque**, nearly matching pure ethanol while having lower autoignition resistance ($\text{RON} \approx 86$).
3. **Wiebe $b \le 2$ Solver Singularity:** Unburned residual fraction remaining at burn completion is $\exp(-b)$. At $b \le 2.0$, $>13.5\%$ unburned charge collapses instantaneously, producing infinite gradients that crash the adaptive ODE solver (`FAILED RUN`). Physically stable SI combustion requires $b \ge 3.0$ (or standard $b=5.0$).
4. **MBT Spark Timing:** Maximum Brake Torque timing advances progressively with burn duration: from $-5.0^\circ\text{ ATDC}$ for fast burns ($\Delta\theta \le 30^\circ$) to $-13.0^\circ\text{ ATDC}$ at $\Delta\theta = 45^\circ$.
5. **Knock vs Heat Loss Trade-off:** Fast burns ($\Delta\theta \le 15^\circ$) compress unburned endgas above $1200\text{ K}$ causing severe knock. Extended burns ($\Delta\theta \ge 50^\circ$) increase convective wall heat loss. Optimal safe operation is at $\Delta\theta = 40^\circ\text{--}45^\circ$.
6. **Otto Cycle Comparison:** Theoretical air-standard Otto efficiency is $58.09\%$ ($\gamma=1.35$) vs $27.23\%$ actual indicated efficiency, with the difference quantitatively audited into wall heat loss at 600 RPM ($36.5\%$), exhaust blowdown ($28.5\%$), finite burn duration ($4.5\%$), and dissociation ($3.3\%$).

---

## 📁 Repository Structure

```
├── new_data_output/                    # Complete 3-run study (PRF, 100% Ethanol, 80/20 Blend)
│   ├── Group 15 IC Engine Project Report — All Runs Analysis (Problem 15).pdf
│   ├── PROJECT DATAS.pdf               # Chemkin input parameters & baseline observation
│   ├── ANALYSIS.pdf                    # Sweeps of n for b=1..10 & optimal n vs b
│   ├── ANALYSIS 2.pdf                  # Sweeps of SOC (-15° to -5°) across BD (10° to 50°)
│   ├── Presentation_Slides_All_Runs.md # 13-slide presentation deck + viva Q&A
│   ├── README_ALL_RUNS.md              # Detailed documentation of all 3 runs
│   └── plot_all_runs_*.png             # 8 publication-grade comparison plots (300 DPI)
├── old_data_output/                    # Archived initial single-run study
│   ├── IC Engine Project Report — Group 15.pdf
│   ├── Presentation_Slides.md
│   └── plot_*.png
├── chemkin_screenshots/                # Screenshots of Chemkin-Pro GUI setup panels
├── chemkin_student_mech/               # 74-species student chemical mechanism (mech, therm, trans)
├── README.md                           # Master orientation guide
└── .gitignore                          # Clean repository rules
```
