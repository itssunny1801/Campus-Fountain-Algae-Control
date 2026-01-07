# Hydrodynamic Modeling of Algal Bloom Mitigation

**Authors**: Sunny Kumar, Harshvardhan Agarwal  
**Mentor**: Prof. Akash Chaudhary  
**Institution**: IIT Kanpur  
**Timeline**: August 2025

---

## 📌 Project Overview
This project presents a mathematical model for simulating algal biomass growth in a campus fountain to understand the environmental drivers of proliferation. [cite_start]By adapting surface water-quality modeling frameworks (specifically **Chapra’s Hydrodynamic Models**), we formulated a differential equation to predict biomass concentration based on **Light Intensity**, **Temperature**, and **pH**[cite: 450, 453, 455].

[cite_start]The study combines **experimental biological analysis** with **computational simulation** to propose mitigation strategies for aesthetic and maintenance challenges in managed water bodies[cite: 463].

---

## 🔬 Experimental Approach & Data Acquisition

### 1. Microscopy & Organism Identification
To parameterize the model accurately, we performed species-specific identification:
* [cite_start]**Sampling**: Algal samples were collected directly from the fountain and prepared for microscopic observation[cite: 505].
* **Visual Analysis**: We compared sample structures against standard algal charts.
* **Identified Species**:
    * [cite_start]**_Spirulina Maxima_**: Identified by characteristic spiral structures (highlighted yellow in microscopy logs)[cite: 573].
    * [cite_start]**_Phormidium Ambiguum_**: Identified by filamentous structures (highlighted blue in microscopy logs)[cite: 573].
* [cite_start]**Impact on Model**: This identification allowed us to use literature-verified growth parameters (e.g., maximum growth rate $\mu_{max}$) specific to *Spirulina*[cite: 506].

### 2. Nutrient Analysis (Ion Chromatography)
We tested water samples to determine if Nitrogen (N) or Phosphorus (P) were limiting factors:
* [cite_start]**Method**: Ion Chromatography on three separate water samples[cite: 501, 559].
* **Analytes**: Chloride, Fluoride, Sulfate, Nitrates, and Phosphates.
* [cite_start]**Findings**: Nitrate and Phosphate concentrations were negligible/trace[cite: 501].
* [cite_start]**Conclusion**: The nutrient limitation factor $f(v)$ was excluded from the simplified model, assuming non-criticality for the observation period[cite: 502].

---

## 🧮 Mathematical Framework

The core of the project is a **first-order differential equation** describing biomass ($B$) evolution over time.

### Governing Equation
$$\frac{\partial B}{\partial t} = (P - R)B + \text{Transport Terms}$$

Given the fountain's shallow depth and lack of external loading, we simplified this to focus on **Net Production ($P$)** and **Respiration ($R$)**:
$$P = P_{max} \cdot g(I) \cdot h(T) \cdot i(pH)$$

### Environmental Limitation Functions
We modeled environmental constraints using values normalized between 0 and 1:
1.  [cite_start]**Light Limitation $g(I)$**: Modeled using **Monod kinetics** based on solar irradiance data from **NASA Power Data Access Viewer**[cite: 564, 575].
    $$g(I) = \frac{I^m}{I^m + K_I^m}$$
2.  [cite_start]**Temperature Limitation $h(T)$**: A quadratic function centered around an optimal temperature ($T_{opt} = 33^\circ C$)[cite: 566, 575].
    $$h(T) = 1 - \frac{(T - T_{opt})^2}{\Delta T^2}$$
3.  [cite_start]**pH Limitation $i(pH)$**: Dependent on hydrogen ion concentration $[H^+]$, accounting for the ionization states affecting algal metabolism[cite: 576].

---

## 💻 Simulation Details

* [cite_start]**Solver**: MATLAB `ode45` (Runge-Kutta method)[cite: 626].
* [cite_start]**Duration**: 30 Days (June 23rd – July 23rd)[cite: 562].
* [cite_start]**Time Step**: 12 hours (to approximate day/night cycles)[cite: 563].
* **Key Parameters**:
    * [cite_start]$\mu_{max} \approx 0.89$ per half-day[cite: 565].
    * [cite_start]Respiration rate function of temperature and dark/light volume ratio[cite: 570].

---

## 📊 Results & Discussion

### Key Findings
1.  [cite_start]**Growth Phase**: The model accurately predicted the initial **exponential bloom** observed immediately after fountain cleaning[cite: 628].
2.  [cite_start]**Peak & Decline**: The simulation showed a peak concentration at **Day 10**, followed by a gradual decline ($0.55 \to 0.40 g/m^3$)[cite: 629].
3.  **Observation Mismatch**: Real-world observation showed stagnation (high algae levels) rather than a decline.

### Limitations Identified
* **pH Interpolation**: We lacked daily pH logs and relied on interpolation. [cite_start]Since algae are highly pH-sensitive, this introduced error[cite: 638].
* [cite_start]**Nutrient Recycling**: The exclusion of nutrient recycling likely underestimated the system's capacity to sustain high biomass in the later stages[cite: 640].

---

## 📂 Repository Structure
* `/src`: MATLAB scripts for the differential equation and solver.
* `/data`: Raw data from NASA Power Viewer and Ion Chromatography results.
* `/docs`: Full project report and microscopy images.
