# Organization-Vita-Track-Wellness-Power-BI-Dashboard

An interactive, multi-page Power BI dashboard engineered for **VitaTrack Wellness** (headquartered in FitZone) to analyze user health metrics, evaluate lifestyle balances, identify chronic risk parameters, and segment the user population for proactive healthcare interventions.

## 🚀 Live Visuals Overview
The repository contains a fully polished 3-page interactive report layout:
1. **The Lifestyle Balance Tracker:** Analyzes daily step metrics, caloric tracking budgets, and non-linear physical recovery behaviors.
2. **Heart Risk Analysis:** Evaluates vital metrics, tobacco/substance impacts, and underlying diagnostic cross-tabulations.
3. **The Demographic Explorer:** Uncovers body mass variations by demographic slices and structures populations into operational strategic groups.

---

## 🛠️ Key Technical Implementations

### 1. Data Pipeline & Transformations (Power Query M-Code Logic)
*   **Vitals Parsing:** Dynamically split the composite string column `Blood_Pressure` using the custom delimiter `/` into separate standalone numeric features: `Systolic_BP` and `Diastolic_BP`.
*   **Schema Bucketization:** Engineered custom conditional schemas to group continuous variables into operational analytics buckets (`Age_Group` and `BMI_Category`).

### 2. Core Business Intelligence Formulas (DAX Implementation)
The analytics and population aggregations are powered by robust backend DAX calculations:

```dax
// 1. Compute overall clinical heart disease baseline
Heart Disease Rate = 
DIVIDE(
    CALCULATE(COUNT(health_activity_data[ID]), health_activity_data[Heart_Disease] = "Yes"),
    COUNT(health_activity_data[ID]),
    0
)

// 2. Behavioral cohort segmentation logic (Calculated Column)
Activity Segment = 
SWITCH(
    TRUE(),
    health_activity_data[Daily_Steps] >= 10000 && health_activity_data[Exercise_Hours_per_Week] >= 5, "Active Lifesters",
    health_activity_data[Daily_Steps] >= 5000 && health_activity_data[Daily_Steps] < 10000, "Moderate Processors",
    "Sedentary Group"
)
```

---

## 📊 Core Data Insights & Analytics Discoveries

*   **The Youth Activity Imbalance:** While the tracking population shows solid general baselines (**10.72K steps / 2.33K calories**), **Young Adults (<30)** demonstrate systemic energetic imbalance, failing to balance high calorie intake volumes with proportional movement compared to the **Middle Aged** peak cohort (**11.3K steps**).
*   **The Overtraining Trap:** Multi-dimensional scatter tracking explicitly exposes an inverse recovery pattern. High-volume fitness trackers (**8–10 exercise hours/week**) hit a strict physical recovery bottleneck, tightly locked within a restricted **4–6 hour sleep window**.
*   **Vitals Stress Matrix:** Comparative substance tracking confirms distinct cardiovascular loads; active smokers register elevated baseline vital baselines, elevating average resting parameters to **85.19 bpm** alongside heightened systemic blood pressure tracks.
*   **High-Risk Population Priority:** Cohort segmentation isolates the **Sedentary Group** as VitaTrack's primary clinical risk profile—encompassing **454 unique users** suffering from compressed rest profiles (**6.86 sleep hours**) and the highest aggregate population **Heart Disease Rate of 10.35%**.

---

## 🎨 Dashboard Design Framework & UX Polish
*   **Unified Brand Palette:** Implemented premium healthcare amber and clean charcoal tones to optimize accessibility and focus user tracking visual flows.
*   **Conditional Dynamic Alerting:** Programmed advanced native callout value logic to automatically toggle structural component backgrounds based on medical goal compliance targets.
*   **Web-App Architecture Integration:** Embedded synchronized page navigator modules to simulate standard corporate application interfaces across multi-page layouts.

---

## 📥 Project Structural Contents
*   `VitaTrack_Wellness_Dashboard.pbix` - The complete completed Power BI dataset model, canvas layouts, and functional configurations.
*   `health_activity_data.csv` - The underlying 1,000 unique anonymized clinical user records tracking matrix.
