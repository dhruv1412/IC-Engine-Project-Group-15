# Group 15: IC Engine Problem 15 — Complete Multi-Run Dataset & Analysis

**Course:** ME31013 (Internal Combustion Engines), IIT Kharagpur  
**Investigator:** Sailor Dhruv Jayeshbhai (Roll: 23ME31047) & Group 15  
**Presentation Date:** November 10, 2026 (4:00 PM – 6:00 PM)  

---

## 📂 Directory Contents

This folder contains the complete solution to **Problem 15** incorporating **all three simulation runs**:
- **RUN 1:** Baseline PRF (100% Isooctane — Gasoline surrogate)
- **RUN 2:** 100% Pure Ethanol ($\text{C}_2\text{H}_5\text{OH}$)
- **RUN 3:** 80% Ethanol + 20% n-Heptane Blend

---

### 1. Reports & Presentation Materials
- **`Project_Report_All_Runs.md`**: Complete markdown technical report with all derivations, tables, and first-principles thermodynamic explanations.
- **`Project_Report_All_Runs.html`**: Print-ready, responsive, beautifully styled HTML report with all 8 publication figures and Chemkin setup screenshots embedded via Base64.
  - *To convert to PDF:* Open `Project_Report_All_Runs.html` in Chrome or Edge and click the floating **"🖨️ Print to PDF"** button (or press `Ctrl+P`).
- **`Presentation_Slides_All_Runs.md`**: 13-slide presentation deck complete with speaker notes and **Viva Defense Q&A** covering professor and TA cross-examination questions.

---

### 2. High-Resolution Publication Figures (300 DPI)
1. **`plot_all_runs_perf_vs_n.png`**: Multi-panel comparison of Torque, Power, and Thermal Efficiency vs Wiebe Shape Factor $n \in [1, 10]$ across fuels at $b = 3, 5, 7$.
2. **`plot_all_runs_perf_vs_b.png`**: Maximum attainable performance vs Scale Parameter $b \in [1, 10]$ across fuels, with the shaded $b \le 2$ solver singularity zone.
3. **`plot_all_runs_optimal_n_vs_b.png`**: Locus of optimal Wiebe shape parameter $n^*(b)$ showing the linear trajectory $n^*(b) \approx 0.55b + 3.8$.
4. **`plot_all_runs_perf_vs_SOC.png`**: Performance vs Start of Combustion ($\text{SOC} \in [-15^\circ, -5^\circ\text{ ATDC}]$) across fuels for burn durations $\Delta\theta = 20^\circ, 35^\circ, 45^\circ$.
5. **`plot_all_runs_perf_vs_BD.png`**: MBT performance vs Burn Duration ($\Delta\theta \in [10^\circ, 50^\circ]$) highlighting the knock limit at $10^\circ$ and heat loss limit at $50^\circ$.
6. **`plot_all_runs_2D_contour.png`**: 2D contour landscapes of Torque and Thermal Efficiency on the $(\text{SOC}, \Delta\theta)$ plane for RUN 1, RUN 2, and RUN 3.
7. **`plot_all_runs_fuel_comparison.png`**: First-principles chemical thermodynamics comparison (LHV, latent heat of vaporization, charge cooling, mixture energy density, and thermal efficiency).
8. **`plot_all_runs_comprehensive_summary.png`**: Master infographic combining Otto cycle efficiency comparisons, MBT trajectories, and optimal Wiebe locus.

---

### 3. Source Scripts
- **`generate_all_runs_data_and_plots.py`**: Python script that parses `PROJECT DATAS.xlsx`, `ANALYSIS.xlsx`, and `ANALYSIS 2.xlsx`, performs unit conversions, and generates all 8 publication figures.
- **`compile_report.py`**: Python script that compiles both `Project_Report_All_Runs.md` and `Project_Report_All_Runs.html`.

---

## 🔑 Key Deliverables Summary for Evaluation

| Parameter / Metric | RUN 1 (PRF Baseline) | RUN 2 (100% Ethanol) | RUN 3 (80/20 Blend) |
| :--- | :---: | :---: | :---: |
| Peak Indicated Torque | $38.60\text{ N}\cdot\text{m}$ | **$38.84\text{ N}\cdot\text{m}$** | **$38.83\text{ N}\cdot\text{m}$** |
| Peak Indicated Power | $2.425\text{ kW}$ | **$2.440\text{ kW}$** | **$2.439\text{ kW}$** |
| Peak Thermal Efficiency | $18.99\%$ | **$27.23\%$** | **$27.19\%$** |
| Optimal SOC Phasing | $-13.5^\circ\text{ ATDC}$ | $-13.0^\circ\text{ ATDC}$ | $-13.0^\circ\text{ ATDC}$ |
| Optimal Burn Duration $\Delta\theta$ | $45.0^\circ$ | $45.0^\circ$ | $45.0^\circ$ |
| Optimal Wiebe Parameters | $n = 4.0,\; b = 3\text{--}5$ | $n = 4.0,\; b = 3\text{--}5$ | $n = 4.0,\; b = 3\text{--}5$ |
| Air-Standard Otto Efficiency | $58.09\%$ ($\gamma=1.35$) | $58.09\%$ ($\gamma=1.35$) | $58.09\%$ ($\gamma=1.35$) |

