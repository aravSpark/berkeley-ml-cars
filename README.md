Berkeley AI/ML course assignment, used car price analysis

### Problem statement

A used-car dealership wants to know what attributes influence the listing price and understand what consumers value in a used car so they can fine tune their inventory 

### Dataset

The dataset was a subset (426K records) of the used cars dataset from Kaggle. The dataset include listing price and serveral attributes of the vehicles such as year, mileage, condition, fuel type, drive type, and manufacturer.

### Link to notebook
https://github.com/aravSpark/berkeley-ml-cars/blob/main/prompt_II.ipynb

### Methodology

CRISP-DM framework was used to predict used car prices based on attributes such as vehicle age, mileage, condition, fuel type, drive type, and manufacturer. 

The following activities were undertaken:
- Explore the data to understand distributions and missing data
- Identify a few features 
- Visualize categorical and numerical features
- Build and compare multiple models
- Use cross-validation and simple hyperparameter tuning
- Provide clear findings and recommendations

### Modelling

- Baseline model: Median predictor.  
- Tested models:  
  - Linear Regression  
  - Ridge Regression  
  - Lasso Regression  
  - Gradient Boosting  
  - Random Forest  
- Hyperparameter tuning via **GridSearchCV** (Random Forest).  
- Cross-validation with multiple metrics: **MAE, RMSE, R²**.

### Model Evaluation
- **Best model:** Tuned Random Forest.  
- Results:  
  - **MAE ≈ \$3,441** → typical error per car.  
  - **RMSE ≈ \$6,395** → controls large mispricing errors.  
  - **R² = 0.82** → explains 82% of price variation.  
- Compared to baseline MAE (~\$11k), the model reduces errors by **~70%**.

| Model               | MAE ($) | RMSE ($) | R²    |
|---------------------|---------|----------|-------|
| Baseline (Median)   | 11,330  | 15,455   | -0.054|
| Linear Regression   | 5,908   | 9,465    | 0.605 |
| Ridge Regression    | 5,908   | 9,465    | 0.605 |
| Lasso Regression    | 5,906   | 9,466    | 0.605 |
| Gradient Boosting   | 5,316   | 8,699    | 0.665 |
| Random Forest       | 4,725   | 7,775    | 0.733 |
| **Tuned Random Forest** | **3,441** | **6,395** | **0.820** |

### Findings and recommendations:

Mileage and age are the biggest drivers of price, followed by cylinders, condition, drive type, and fuel.  

- Vehicle's Age and Mileage are the two main drivers of price
- Condition of the vehicle matters however it is secondary to vehicle's age and mileage
- Cars with larger engines (more cylinders) and 4WD options tend to command higher prices
- Vehicle type does influence resale prices, pickups and SUVs typically sell for more than sedans. Larger vehicles - trucks and SUV etain more value than sedans   
- For fuel type, Gasoline dominates the market, but diesel vehicles generally carry a relative premium compared to gas

**Model**

We tested several approaches to predict prices. The tuned **Random Forest model** predicts car prices within **≈ \$3,500 error on average**. The model explains **82% of price variation**, providing strong confidence in its predictions.  

**Recommendations**

- Focus inventory on **low-mileage, newer vehicles** as they retain the strongest resale value.  
- **Pickups, SUVs, and 4WD/AWD** vehicles command higher prices and should be prioritized.  
- Diesel vehicles often sell at higher median prices but with wider spreads.  
