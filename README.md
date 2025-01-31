# Capstone Project: Heart Attack Risk Prediction in Female Populations
🚧 In Progress

Developing a **Logistic Regression machine learning model to predict heart attack risk in female populations**. The focus is on identifying key predictive factors such as age, cholesterol, blood pressure, smoking, obesity, and stress and understanding their interrelationships.
Using a dataset from Kaggle, containing 8,763 patient entries, with 2,652 female patients, the goal is to accurately predict heart attack risk based on health metrics, lifestyle factors, and medical history.
The model is evaluated using Python, applying metrics such as accuracy, precision, recall, and F1-score, with cross-validation and hyperparameter tuning to optimize performance. By tailoring this model to women’s unique cardiovascular risk factors, this project seeks to improve early detection, personalized treatment, and clinical practices related to heart disease in women.

## Materials
You can access the materials by clicking
-[Python Notebook: Exploratory Data Analysis(EDA)](   )
-[Python Notebook: Machine Lerning (ML)](   )


📊 Project Visualization
![image](https://github.com/user-attachments/assets/43b4979f-ea8a-435c-b2c2-84231939164c)

📂 Dataset Information
Dataset Name: female_heart_df2
Source: [Kaggle] (https://www.kaggle.com/datasets/iamsouravbanerjee/heart-attack-prediction-dataset)

Y = Target Variable: Heart Attack Risk (1 = Yes, 0 = No)

X = Predictor Variables:

-**Health Metrics:** Cholesterol, Blood Pressure, Heart Rate, BMI, Triglycerides

-**Lifestyle Factors:** Smoking, Alcohol Consumption, Exercise Hours, Diet, Sleep Hours, Sedentary Hours

-**Medical History:** Diabetes, Previous Heart Problems, Medication Use, Family History

-**Demographics:** Age, Income, Country

📈 Key Insights from Exploratory Data Analysis (EDA)
-Seniors (59+) make up 41.25% of the dataset.
-**Smoking & Age show a strong correlation (0.81).**
-Cholesterol & Heart Attack Risk correlation is weak (0.04).
-Diabetes is present in 64.9% of the dataset but has weak correlation (0.03).
-49.9% of females in the dataset are obese.
-Physical Activity: Most engage in 1-3 days/week of exercise.
-Sedentary Behavior: 25% of female smokers sit for 9+ hours/day.
-Sleep Patterns: The majority sleep between 4-10 hours/day, with 8 hours being most common.
-Highest % of female smokers by region:
🌍 Africa (68.8%)
🌍 Europe (67.7%)
🌍 Asia/South America (65.7%)

Top 3 countries with most female smokers:
-🇮🇹 Italy (72.1%)
-🇿🇦 South Africa (70.9%)
-🇻🇳 Vietnam (70.3%)

🤖 Machine Learning Model Performance

🔍 Best Model Selection

Class 1 = Heart Attack Risk

✅ Best Model: Random Forest with SMOTE
## 🤖 Machine Learning Model Performance

| 🏷️ Model                                     | 📊 Accuracy | 🔍 Recall (Class 1) | 🎯 F1-Score (Class 1) | 📌 Interpretation |
|----------------------------------------------|------------|---------------------|----------------------|----------------------------------------------------------------|
| **Baseline Logistic Regression (With/Without PCA)** | 0.6667 | 0.01 | 0.02 | Highly biased towards Class 0; fails to detect high-risk individuals. |
| **Random Forest (PCA)**                     | 0.6478 | 0.07 | -- | Slight recall improvement but still too low to be useful. |
| **Decision Tree**                            | 0.6535 | 0.06 | -- | Slight recall improvement but not significantly better than Logistic Regression. |
| **Random Forest with SMOTE** ✅              | **0.6520** | **0.67** | **0.66** | Best model; SMOTE balancing improved recall significantly. |
| **Best GridSearch Random Forest**           | 0.6404 | 0.68 | -- | Best recall but lower accuracy; useful but less optimal. |
| **XGBoost** ❌                               | 0.5932 | 0.16 | -- | Worst model; low accuracy and recall. |
| **Tuned Random Forest**                     | 0.6629 | 0.03 | -- | Comparable accuracy to Logistic Regression but very low recall. |
| **Stacking Model**                           | **0.6681** | 0.03 | 0.05 | Higher accuracy but recall is too low to be useful. |


⚠️ Worst Models:

Logistic Regression → Fails to detect heart attack risk (Recall = 0.01).

XGBoost → Lowest accuracy (0.5932) and weak recall (0.16).

🔬 Alternative Choice:

Best GridSearch Random Forest if recall (0.68) is prioritized, but has slightly lower accuracy.

**Features Used in the Best Model (Random Forest with SMOTE)**

## 🔍 Feature Importance (Top 10 Features) 

| 🏷️ Original Feature          | 📊 Importance (%) |
|------------------------------|------------------|
| **Stress Level**             | 7.33%            |
| **Sleep Hours Per Day**      | 6.18%            |
| **Sedentary Hours Per Day**  | 6.17%            |
| **Previous Heart Problems**  | 5.95%            |
| **Alcohol Consumption**      | 5.91%            |
| **Cholesterol**              | 5.88%            |
| **Family History**           | 5.87%            |
| **Heart Rate**               | 5.66%            |
| **Obesity**                  | 5.56%            |
| **Diabetes**                 | 5.51%            |

#The top feature in dataset is Stress Level (7.33%), followed by Sleep Hours Per Day (6.18%) and Sedentary Hours Per Day (6.17%).
# Smoking is missing from the top-ranked features, meaning it was not selected as one of the most important predictors by  model.
#The lowest-ranked important features (Obesity: 5.56% and Diabetes: 5.51%) still have higher importance scores than Smoking.
#Yes, Smoking is correlated with Age, but it was not a direct driver of heart attack risk
#Smoking did not independently contribute enough predictive value compared to other health factors (e.g., Stress, Cholesterol, Sleep, Sedentary Behavior).
#Smoking may not directly impact heart attack risk as much as Stress Level, Cholesterol, or Family History.
#The dataset was transformed with PCA, which combined Smoking with other features into principal components.
#In SHAP Correlation only shows linear relationships, but Random Forest and tree-based models capture complex, nonlinear interactions.

📜 Conclusions & Recommendations
✅ Key Risk Factors: Stress Level, Sleep Hours per Day, Sedentary Hours Per Day, Previous Hert Probles.
✅ Lifestyle Modifications: Increasing physical activity, reducing sedentary hours, and managing stress can reduce heart attack risk.
✅ Further Research Needed: Explore genetic predisposition, diet, and medication use as additional predictors.
✅ Machine Learning Recommendations: Random Forest with SMOTE is the best-performing model. Further hyperparameter tuning could improve performance.

📌 Next Steps
🔍 Improve Model Performance: Hyperparameter tuning on Random Forest and ensemble learning.

📊 Feature Engineering: Create new features using domain knowledge.

📡 Deploy Model: Build an API or web app to make real-time heart attack risk predictions.
