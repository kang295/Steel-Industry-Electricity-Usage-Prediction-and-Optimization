# Steel Industry Electricity Usage Prediction and Optimization

## 🔹Project Overview  
This project aims to **predict electricity consumption** in the steel industry using machine learning models. By analyzing key factors influencing power usage, we strive to **enhance energy efficiency, reduce costs, and lower CO₂ emissions**.  

--------

## 1. Data Exploration & Preprocessing  

### Target Variable: Electricity Usage  
- Electricity consumption typically ranges from **3 to 55 kWh**, with **spikes during heavy-load operations**.  
- The factory primarily consumes electricity for **light-load tasks**, but demand increases significantly for **heavy-load work**.  

### Feature Analysis & Selection  

#### Categorical Features (3)  
- **Workload Type & Electricity Usage:**  
  - Light-load tasks dominate.  
  - Medium/heavy tasks occur mostly on weekdays for operational stability.  
- **Distribution Analysis:**  
  - **QQ plot confirms non-normal distribution**, increasing sensitivity to outliers.  
- **Statistical Validation:**  
  - **Box-Cox & log transformation results (p-value < 0.05) indicate variance-based normalization is ineffective.**  
  - **Kruskal-Wallis test confirms all categorical features are statistically significant (p-value = 0).**  

#### Numerical Features (6)  
- **Feature Scaling:**  
  - **Violin plots** reveal different scales → **MinMax Scaling applied**.  
- **Feature Correlation & Reduction:**  
  - **Correlation heatmap** detects **highly correlated features (~0.9)** → Removing redundant variables.  
  - **Variance Inflation Factor (VIF) analysis** confirms feature selection choices.  

--------

## 2. Feature Transformation  
- **MinMax Scaling** applied to numerical features.  
- **One-hot encoding** applied to categorical features.  

--------

## 3. Model Development & Performance Evaluation  

### 🔹Machine Learning Models (Random Forest & XGBoost)  
- **Hyperparameter tuning** performed using **Optuna BayesSearchCV**.  
- **Model Performance (Root Mean Squared Error - RMSE):**  
  - ✅ **Random Forest RMSE: 3.19**  
  - ✅ **XGBoost RMSE: 3.15**  
- **Best Model:** **XGBoost**, which outperformed Random Forest with the lowest RMSE.  

### Feature Importance Analysis  
**Key drivers of electricity usage:**  
1️⃣ **CO₂ Emissions** → Higher emissions result from increased electricity usage, mainly due to **coal, natural gas, and coke combustion**.  
2️⃣ **Lagging_Current_Reactive_Power_kVarh** → Represents **extra energy needed to sustain electromagnetic fields** in steel plant machinery.  
3️⃣ **Load_Type_Light_Load** → Indicates that **most energy is consumed during light-load operations**.  

### Linear Regression Benchmark  
- After **scaling numerical features** and **encoding categorical variables**, a **linear regression model** was tested.  
- **Linear regression underperformed** compared to ensemble models (**RMSE: 3.85**), confirming that non-linear models are more effective for this problem.  

--------

## 4. Conclusion & Business Impact  
✅ **XGBoost provided the best predictive accuracy**, making it the most reliable model for forecasting electricity usage.  
✅ **Feature importance insights** can guide **energy optimization strategies** and **CO₂ reduction efforts** in the steel industry.  
✅ Findings can help steel plants **implement data-driven energy management**, reducing **costs** and **enhancing sustainability**.  
