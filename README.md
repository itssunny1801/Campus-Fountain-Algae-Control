# Analysis of Campus Fountain Algae Mitigation using Hydrodynamic Modelling

## 📌 Project Overview
This project develops and analyzes a mathematical model to simulate **algal biomass growth** within a campus fountain. [cite_start]Using established surface water-quality modeling frameworks (referencing Steven C. Chapra), the study identifies key environmental drivers of algal proliferation—specifically **light intensity, temperature, and pH**[cite: 453, 454, 455].

[cite_start]The model was parameterized using **experimental data** collected from the IIT Kanpur campus fountain, including microscopic species identification and nutrient analysis[cite: 456, 457]. [cite_start]The simulation, implemented in **MATLAB**, successfully predicts the initial rapid growth phase of algal blooms, aligning with real-world observations[cite: 458, 459].

---

## 🔬 Experimental Methodology

### 1. Water Quality Analysis
* **Nutrient Testing:** Water samples were analyzed for nitrates and phosphates using **ion chromatography**. [cite_start]Results consistently showed negligible nutrient concentrations, leading to the exclusion of nutrient limitation factors ($f(v)$) from the initial model[cite: 500, 501, 560].
* **Species Identification:** Microscopic analysis identified the dominant algal species as **Spirulina** and *Phormidium Ambiguum*. [cite_start]This allowed for the selection of species-specific growth parameters ($\mu_{max}$, optimal temperature) from literature[cite: 504, 506, 573].

### 2. Data Collection
* [cite_start]**Light Intensity ($g(I)$):** Solar irradiance data for Kanpur was sourced from the **NASA Power Data Access Viewer**[cite: 564].
* [cite_start]**Temperature ($h(T)$):** Modeled using half-day average temperatures with an optimal growth temperature ($T_{opt}$) set to **33°C**[cite: 566].
* [cite_start]**pH Levels ($i(pH)$):** Weekly pH measurements were interpolated to estimate daily fluctuations, influencing the metabolic limitations of the algae[cite: 568, 569].

---

## 🧮 Mathematical Framework
[cite_start]The core model describes the change in algal biomass concentration $B$ ($g/m^3$) over time using the differential equation[cite: 479]:

$$\frac{\partial B}{\partial t} = (P - B_M - P_R)B + \frac{\partial}{\partial z}(w_s B) + \frac{B_L}{V}$$

Given the shallow depth and lack of external loading, the equation simplifies to focus on **Net Production Rate ($P$)**:

$$P = P_{max} \cdot f(v) \cdot g(I) \cdot h(T) \cdot i(pH)$$

Where limitation functions ($0 \le \text{func} \le 1$) account for:
* [cite_start]**Light:** Monod-type saturation kinetics ($g(I) = I^m / (I^m + K_I^m)$)[cite: 575].
* [cite_start]**Temperature:** Quadratic inhibition around $T_{opt}$[cite: 575].
* [cite_start]**pH:** Ionization-based inhibition curve dependent on $[H^+]$ concentration[cite: 576].

---

## 📊 Simulation Results
[cite_start]The differential equation was solved using **MATLAB's `ode45` solver** over a 30-day period (June 23 - July 23)[cite: 562, 626].

* [cite_start]**Initial Growth:** The model correctly predicted an **exponential bloom** in the first week, matching visual evidence from the fountain[cite: 628, 633].
* **Long-term Behavior:** The simulation predicted a peak around **Day 10** followed by a decline ($0.55 \to 0.40 g/m^3$). In contrast, observed algae levels stagnated at high concentrations. [cite_start]This discrepancy is attributed to **interpolated pH inaccuracies** and potential unmeasured **nutrient recycling**[cite: 629, 630, 636].

---

## 🚀 Key Takeaways & Future Work
* [cite_start]**Valid Framework:** The hydrodynamic approach successfully models the onset of algal blooms based on physical parameters[cite: 634].
* [cite_start]**pH Sensitivity:** Algal growth was found to be highly sensitive to pH fluctuations; higher-resolution pH logging is recommended for future iterations[cite: 638, 639].
* [cite_start]**Nutrient Cycling:** Future models should incorporate internal nutrient recycling mechanisms to better predict steady-state population density[cite: 641].

---

## 👨‍💻 Contributors
* **Sunny Kumar**
* **Harshvardhan Agarwal**
* **Mentor:** Prof. Akash Chaudhary

---

### 📚 References
* Chapra, S. C. *Surface Water-Quality Modeling*.
* NASA Power Data Access Viewer (Solar/Meteorological Data).
