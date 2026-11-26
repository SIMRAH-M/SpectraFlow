# SpectraFlow
**Cyber-physical microplastic filtration and optical sensing system mitigating neuro-inflammatory water exposure through crop-waste bio-coagulation filters, a 45-degree LED/UV dark-box, Arduino turbidity control, OpenCV particle segmentation, and Random Forest optimization.**

* **Researcher & Developer:** [Simrah]
* **Domains:** Electrical Engineering | Robotics & Embedded Systems | Computer Science | Preventive Neurobiology
* **Location:** Karachi, Pakistan

---

### 1. Problem Statement & Scientific Motivation
Recent peer-reviewed studies have confirmed that microplastics and nanoplastics can cross the human blood-brain barrier, accumulate in neural tissue, and trigger microglial neuroinflammation, oxidative stress, and neurotransmitter disruption. Because removing nanoplastics once they enter human tissue is currently impossible, **intercepting microplastics in household drinking water before ingestion** is the most scalable preventive intervention.

However, existing detection methods (FTIR spectroscopy, fluorescence microscopy) and removal systems (Reverse Osmosis) require expensive laboratory equipment, high energy consumption, and significant water waste—making them inaccessible to low-income communities.

**SpectraFlow** addresses both halves of this problem in one low-cost cyber-physical system:
1. **Frugal Optical Detection:** Replaces expensive microscopes with a controlled 45-degree LED/UV optical dark-box and smartphone macro-imaging analyzed via an automated **OpenCV computer vision pipeline**.
2. **Biodegradable Agricultural-Waste Filtration:** Combines fibrous crop waste (**sugarcane bagasse** and **coconut coir**) with natural electrostatic bio-coagulants (**crushed *Moringa oleifera* seeds** and **okra mucilage**) to trap microplastics for under $0.35 per cartridge.

---

### 2. System Architecture (4 Integrated Modules)

| Module | Engineering Domain | Repository File / Component | Technical Function |
| :--- | :--- | :--- | :--- |
| **Module 1: Optical Dark-Box & Auto-Valve** | Electrical Eng. & Robotics | Hardware Rig *(In Fabrication)* | 45-degree incident illumination chamber eliminating ambient glare; optional Arduino/ESP32 LDR turbidity sensor and servo diversion valve. |
| **Module 2: Computer Vision Particle Counter** | Computer Science (`OpenCV`) | `01_particle_counter.ipynb` | Converts macro filter-paper images to HSV color space, applies morphological noise filtering, segments microplastic contours, and computes pixel area distributions. |
| **Module 3: ML Filtration Optimizer** | Machine Learning (`scikit-learn`) | `02_filtration_predictor.ipynb` | Random Forest Regressor trained on multi-variable filtration trials (`bagasse_g`, `moringa_g`, `flow_rate_ml_min`) to predict optimal microplastic removal efficiency (%). |
| **Module 4: Neuro-Exposure Risk Model** | Computational Health (`Python`) | `03_neuro_risk_model.ipynb` | Models annual microplastic particle ingestion prevented per individual and household based on local baseline water contamination and measured filter efficiency. |

---

### 3. Repository Structure & File Guide

* **`01_particle_counter.ipynb`** — End-to-end computer vision notebook initialized with a synthetic calibration benchmark (28 randomized microplastic particles on filter paper) demonstrating HSV color segmentation, contour extraction, and automated visual annotation. Ready to ingest real macro camera captures (`sample.jpg`).
* **`02_filtration_predictor.ipynb`** — Machine learning regression pipeline (`RandomForestRegressor`, `n_estimators=100`) trained on pilot calibration benchmarks across varying bio-fiber masses, *Moringa* coagulant dosages, and flow rates to forecast removal efficiency before physical prototyping.
* **`03_neuro_risk_model.ipynb`** — Quantitative exposure-reduction simulator and `matplotlib` visualization generator comparing annual unfiltered drinking-water particle intake against SpectraFlow-filtered water.

---

### 4. How to Run the Code (Zero Local Setup)
All three notebooks are self-contained and executable directly in **Google Colab**:
1. Open any `.ipynb` file above in [Google Colab](https://google.com).
2. Run all cells (`Runtime -> Run all`). No external datasets are required for initial calibration runs.
3. To test with custom experimental photos in `01_particle_counter.ipynb`, upload your macro image as `sample.jpg` and replace the synthetic image generator block with `img = cv2.imread('sample.jpg')`.

---

### 5. Current Validation & Next Engineering Milestones
* **Completed Software & Calibration Pipeline:** Built and validated the OpenCV particle-segmentation algorithm, Random Forest filtration predictor, and neuro-exposure risk simulator using synthetic optical calibration images and pilot benchmark datasets.
* **Optical Dark-Box & Wet-Lab Validation (In Progress):** Assembling the fixed-focal-length smartphone macro-imaging enclosure (45-degree LED/395nm UV illumination) to execute 25 standardized filtration trials across sugarcane bagasse, coconut coir, *Moringa oleifera*, and okra bio-filters.
* **Closed-Loop Embedded Control (Next Phase):** Integrating an Arduino/ESP32 optical turbidity feedback loop to automate valve diversion upon cartridge saturation.

---

### License
This project is open-source under the **MIT License**—free to use, test, and build upon with attribution.

