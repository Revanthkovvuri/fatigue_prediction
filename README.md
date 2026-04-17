- **Dataset:** Microsoft GeoLife Trajectory Dataset (1.2M+ points).
- **Core Model:** XGBoost Regressor.
- **Accuracy:** 0.28 RMSE (Root Mean Square Error) on a 100-point scale.

## 🧠 The Science: Feature Engineering
The model's high accuracy stems from integrating established sports science and physiological research:

### 1. Naismith’s Rule (Elevation Equivalence)
Using the 1892 Naismith’s Rule, the engine calculates **Effective Distance (ED)**. It treats every 120 meters of vertical ascent as 1 kilometer of flat walking.
> **Formula:** $ED = \text{Distance (km)} + \frac{\text{Elevation Gain (m)}}{120}$

### 2. Thermal Stress (Galloway & Maughan)
Based on environmental physiology research, the model applies a non-linear penalty for temperatures outside the "Optimal Performance Zone" (10°C – 20°C). 
- **Heat Strain:** $+1.3\%$ fatigue per degree above 20°C.
- **Cold Strain:** $+1.0\%$ fatigue per degree below 10°C.

### 3. Langmuir’s Group Corrections
Adjusts the pace and fatigue accumulation based on group size, accounting for social pacing and the "slowest member" rule in group expeditions.

## 🛠️ Technical Stack
- **Languages:** Python (Data Science Pipeline).
- **Libraries:** XGBoost, Pandas (Vectorized processing), NumPy, Scikit-learn, Matplotlib.
- **Data Sourcing:** Open-Meteo Historical Weather API integration.
- **Architecture:** Planned integration with Next.js & Supabase via a FastAPI microservice.

## 📊 Model Performance
The model was optimized using Gradient Boosting with early stopping to prevent overfitting.

| Metric | Value |
| :--- | :--- |
| **Best RMSE** | 0.2828 |
| **Optimization Rounds** | 199 Iterations |
| **Top Predictor** | Total Distance / Elevation Gain |