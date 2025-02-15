# Steel-Industry-Electricity-Usage-Prediction-and-Optimization

## **Project Overview: Electricity Usage Prediction in Steel Industry**

### **1. Importing Libraries for EDA, Statistical Analysis, and Modeling**

### **2. Data Preprocessing**

- Loaded dataset, performed exploratory data analysis (EDA), and handled missing values.

### **3. Exploratory Data Analysis (EDA) & Feature Selection**

### **Target Variable (Electricity Usage)**

- Electricity usage mostly ranged from **3 to 55 kWh**, with some significant outliers.
- Factory primarily consumes electricity for **light-load tasks**, but demand spikes for **heavy-load operations**.

### **Categorical Features (3)**

- Electricity usage patterns align with workload types: **light-load tasks dominate**, while **heavy/medium tasks occur mainly on weekdays** for operational continuity.
- **QQ plot confirms target variable is not normally distributed**, making it sensitive to outliers and potentially distorting model predictions.
- **Box-Cox & log transformation results (p-value < 0.05) confirm variance analysis is not valid** for target normalization → X Anova test
- **Kruskal-Wallis test confirms all categorical features are statistically significant (p-value = 0).**

### **Numerical Features (6)**

- **Violin plots reveal varying scales among numerical features**, necessitating **MinMax Scaling**.
- **Correlation heatmap identifies highly correlated features (~0.9), leading to feature reduction** (e.g., dropping `Lagging_Current_Power_Factor`).
- **VIF analysis confirms redundant features, supporting feature selection process**.

### **4. Feature Transformation**

- **MinMax Scaling** applied to numerical features.
- **One-hot encoding** applied to categorical features.

### **5. Machine Learning Modeling (Random Forest & XGBoost)**

- **Hyperparameter tuning using Optuna BayesSearchCV**.
- **Model Performance (RMSE values):**
    - **Random Forest RMSE: 3.19**
    - **XGBoost RMSE: 3.15**
- **XGBoost outperformed Random Forest**, achieving the lowest RMSE.

### **6. Feature Importance Analysis**

- Key drivers of electricity usage:
    - `CO2`(resulting from coal, natural gas, and coke combustion).
    - `Lagging_Current_Reactive_Power_kVarh` (extra energy required to sustain electromagnetic fields in steel plant equipment)
    - `Load_Type_Light_Load`(indicating dominant usage patterns of light load work).

### **7. Linear Regression Performance Check**

- After **scaling numerical features and encoding categorical variables**, a **linear regression model was tested**.
- **Linear regression underperformed** compared to Random Forest and XGBoost, with **higher RMSE (3.85) values**.

### **Conclusion**

- **XGBoost demonstrated the best predictive performance**, making it the optimal model for forecasting electricity consumption.
- Insights gained from **feature importance** can help optimize energy usage and CO₂ emissions in industrial operations.
