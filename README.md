# Student Productivity and Distraction Analysis

## Project Motivation

Student productivity is a critical factor in academic success. This project investigates the relationship between various behavioral and lifestyle factors—including study habits, sleep patterns, phone usage, exercise, and stress levels—and overall productivity scores.

By leveraging machine learning and the CRISP-DM methodology, this analysis aims to:
- Identify which factors most strongly influence student productivity
- Build a predictive model to estimate productivity based on student behavior

## Libraries Used

### Data Analysis & Visualization
- **pandas** - Data manipulation and analysis
- **numpy** - Numerical computing
- **matplotlib** - Data visualization
- **seaborn** - Statistical data visualization

### Machine Learning
- **scikit-learn** - Machine learning models and preprocessing
  - `RandomForestRegressor` - Main predictive model
  - `StandardScaler` - Feature scaling
  - `train_test_split` - Data splitting
  - Metrics: `mean_squared_error`, `r2_score`, `mean_absolute_error`

### Model Interpretability
- **shap** - SHAP values for model explanation

## Repository Structure

```
blog/
├── blog.ipynb                                    # Main analysis notebook
├── student_productivity_distraction_dataset_20000.csv  # Dataset (20,000 student records)
└── README.md                                     # This file
```

### Files Description

**`blog.ipynb`** - Jupyter notebook containing the complete CRISP-DM analysis:
1. **Phase 1: Exploratory Data Analysis (EDA)**
   - Data overview and basic statistics
   - Distribution analysis (histograms, skewness, kurtosis)
   - Missing value detection
   - Correlation analysis with target variable
   - Outlier detection using IQR method
   - Data quality assessment

2. **Phase 2: Model Training & Evaluation**
   - Data quality assessment
   - Train-test split (80-20)
   - Feature scaling with StandardScaler
   - Random Forest model training
   - Performance metrics: R², RMSE, MAE
   - Feature importance analysis
   - Actual vs Predicted visualization
   - Residual analysis
   - SHAP explainability plots

3. **Phase 3: Inference**
   - Creating a scenario
   - Inference for this scenario


**`student_productivity_distraction_dataset_20000.csv`** - Dataset containing:
- **20,000 student records** with 19 features
- **Target variable:** `productivity_score` (continuous, 0-100)
- **Feature categories:**
  - Demographics: age, gender
  - Study habits: study_hours_per_day, attendance_percentage, assignments_completed
  - Sleep & exercise: sleep_hours, exercise_minutes
  - Digital distractions: phone_usage_hours, social_media_hours, youtube_hours, gaming_hours
  - Health: coffee_intake_mg, stress_level
  - Academic outcomes: focus_score, final_grade
  - Routine: breaks_per_day

## Analysis Results Summary

### Key Findings

**1. Top Predictive Features** (from Random Forest Feature Importance)
   - Study hours per day - Strong positive correlation
   - Sleep hours - Moderate positive correlation
   - Stress level - Negative correlation with productivity
   - Exercise minutes - Positive correlation
   - Phone usage hours - Negative correlation (distraction)

**2. Model Performance**
   - **Random Forest Regressor**
     - Test R² Score: 0.95+ (explains ~95% of productivity variance)
     - Test RMSE: ~2.5 points
     - Test MAE: ~2 points
   - Model successfully predicts student productivity based on behavioral factors

**3. Data Quality**
   - No missing values in dataset
   - No duplicate records
   - All features within logical bounds
   - 20,000 valid student records analyzed


### Insights & Recommendations

1. **Study Hours Matter Most** - Students with consistent daily study routines show highest productivity
2. **Sleep is Critical** - 6-8 hours of sleep correlates with optimal productivity
3. **Manage Digital Distractions** - Phone usage inversely correlates with productivity
4. **Stress Management** - Students with lower stress levels are more productive
5. **Active Lifestyle** - Regular exercise correlates with higher productivity scores

## CRISP-DM Methodology

This analysis follows the **Cross-Industry Standard Process for Data Mining (CRISP-DM)**:

1. **Business Understanding** ✓ - Identified the need to understand productivity drivers
2. **Data Understanding** ✓ - Explored dataset characteristics and distributions
3. **Data Preparation** ✓ - Cleaned data
4. **Modeling** ✓ - Trained and optimized Random Forest model
5. **Evaluation** ✓ - Assessed model performance with multiple metrics
6. **Deployment** - Model ready for predicting student productivity

## How to Use

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn scikit-learn shap
```

### Run the Analysis
1. Open `blog.ipynb` in Jupyter Notebook
2. Ensure `student_productivity_distraction_dataset_20000.csv` is in the same directory
3. Run cells sequentially from top to bottom

### Making Predictions
```python
# Load the trained model and make predictions on new students
student_data = pd.DataFrame({
    'age': [22],
    'study_hours_per_day': [6],
    'sleep_hours': [7],
    'phone_usage_hours': [2],
    # ... other features
})

predicted_productivity = model.predict(student_data)
```

## Acknowledgments

- **Dataset Source**: Student Productivity and Distraction Dataset (20,000 records)
- **CRISP-DM Methodology**: Industry standard for data mining and machine learning projects
- **Libraries**: Built with open-source Python libraries (pandas, scikit-learn, matplotlib)
- **Inspiration**: Understanding factors that influence student academic success and well-being

## License

This project is part of the Udacity Data Science Nanodegree program.

## Contact & Questions

For questions about this analysis, please refer to the notebook documentation or review the SHAP explainability plots for model interpretation.

---

**Last Updated**: March 10, 2026
**Dataset Size**: 20,000 records
**Model Type**: Random Forest Regression