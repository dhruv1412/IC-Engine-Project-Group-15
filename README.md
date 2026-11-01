# IC Engine Project — Problem 15: Ethanol SI Engine Study
**Department of Mechanical Engineering, IIT Kharagpur**  
**Group 15** | Presentation Date: November 10, 2026 | Submission Date: November 10, 2026  

---

## 📌 Project Overview & Key Findings

This project investigates the closed-cycle performance of a four-stroke Spark-Ignition (SI) engine fueled with pure ethanol ($\text{C}_2\text{H}_5\text{OH}$, $\phi = 1.0$) at a compression ratio of $\text{CR} = 12.0$ using **ANSYS Chemkin-Pro 2025 R2** (Aurora Two-Zone SI Engine Model).

1. **Wiebe Shape Exponent ($n$):** Increasing $n$ from $1.0 \rightarrow 5.0$ increases indicated torque from $30.25 \rightarrow 38.17\text{ N}\cdot\text{m}$ and efficiency from $14.88\% \rightarrow 18.78\%$ by preventing negative compression work.
2. **Wiebe Completeness ($b$):** Identified solver singularity at $b=2.0$ ($13.5\%$ unburned fuel causes energy discontinuity). Peak indicated work occurs at $b=3.0\text{--}5.0$.
3. **Start of Combustion ($\text{SOC}$):** **Maximum Brake Torque (MBT)** timing is achieved at $\mathbf{-10.0^\circ\text{ ATDC}}$ ($38.58\text{ N}\cdot\text{m}$, $18.98\%$ efficiency).
4. **Burn Duration ($\Delta\theta$):** Fast burns at $\Delta\theta \le 10^\circ$ trigger **severe endgas knock** ($T_{\text{endgas}} > 1200\text{ K}$ at $4.42^\circ\text{ ATDC}$). Optimal safe burn duration is $\Delta\theta \approx 45.6^\circ$.
5. **Otto Cycle Comparison:** The ideal Otto cycle efficiency is $58.09\%$ ($\gamma = 1.35$) vs $18.98\%$ actual indicated efficiency. The difference is primarily due to convective wall heat loss at 600 RPM ($\sim 24\%$), finite burn duration ($\sim 6.5\%$), and dissociation ($\sim 5\%$).

---

## 📁 Repository Structure

```
├── Project_Report.md           # Comprehensive Technical Report (Markdown)
├── Presentation_Slides.md      # Slide-by-slide bullet points, speaking script & viva prep
├── chemkin_screenshots/        # Screenshots of CHEMKIN-Pro GUI configuration panels
├── chemkin_student_mech/       # 74-species reduced chemical kinetics mechanism (mech, therm, trans)
├── plot_comprehensive_summary.png  # Master 4-in-1 executive summary plot
├── plot_perf_vs_*.png          # Individual parameter sensitivity plots
├── plot_wiebe_*.png            # Theoretical Wiebe mass fraction & burn rate plots
└── Pressure_Unburned_Zone...   # Chemkin in-cylinder P-theta indicator diagram
```


