
## 🧾 BRFSS 2021 Health Analysis

### **Overview**

This project explored data from the **2021 Behavioral Risk Factor Surveillance System (BRFSS)** to examine relationships between key health indicators and lifestyle factors among U.S. adults. The goal was to identify patterns in general health outcomes using real-world public health data and apply practical data cleaning, visualization, and regression modeling techniques in R.

---

### **Part 1 – Data Exploration and Cleaning**

We began by selecting and cleaning three variables:

* **FRUIT2** (frequency of fruit consumption)
* **CHECKUP1** (time since last medical checkup)
* **GENHLTH** (self-reported general health)

Missing values, “don’t know,” and “refused” responses were removed to ensure data integrity. The resulting dataset (`brf_Q2`) contained over **431,000 valid cases**. Early analysis revealed that most respondents reported “Good” or “Very Good” health, with regular checkups and moderate fruit intake.

---

### **Part 2 – Extended Variable Analysis**

For the second stage, four new variables were selected to deepen the analysis:

* **_BMI5CAT** (Body Mass Index category – response variable)
* **_AGE_G** (six-level age group)
* **EXERANY2** (exercise in past 30 days)
* **EDUCA** (education level)

Since the dataset lacked pre-calculated BMI values, BMI was **computed manually** using respondents’ `HEIGHT3` and `WEIGHT2` values. After deriving and categorizing BMI, all variables were cleaned to replace missing or refused responses with `NA`, and only complete observations were retained for analysis.

---

### **Part 3 – Exploratory Analysis**

A series of **ggplot2 visualizations** were created, including bar plots and boxplots, to display variable distributions and relationships:

* Younger, more educated, and physically active respondents were more likely to fall in normal BMI categories.
* Older adults and those with lower education levels showed higher obesity prevalence.
* Exercise and education together appeared to play an important role in maintaining healthy BMI levels.

Descriptive statistics confirmed these patterns, highlighting central tendencies and variation across BMI categories.

---

### **Part 4 – Regression Modeling**

Three multinomial logistic regression models were built to predict BMI category based on different predictors:

1. **Model 1:** Age group only
2. **Model 2:** Age + Exercise
3. **Model 3:** Age + Exercise + Education + Interaction

Model performance was compared using **AIC** and **pseudo-R²**.
✅ **Model 3** performed best, showing that **exercise and education together significantly influence BMI**, and their interaction suggests that education enhances the benefits of physical activity on maintaining healthy weight.

---

### **Part 5 – Model Prediction**

Using the final model, predictions were made for three hypothetical individuals:

| Case | Age Group | Exercise | Education        | Predicted BMI |
| ---- | --------- | -------- | ---------------- | ------------- |
| 1    | 25–34     | Yes      | College graduate | Normal Weight |
| 2    | 55–64     | No       | High school      | Obese         |
| 3    | 65+       | Yes      | Elementary       | Overweight    |

Predicted probabilities reflected realistic public health trends:

* Younger, active, and educated individuals had the healthiest BMI outcomes.
* Inactivity and lower education levels correlated with obesity risk.
* Exercise mitigated some, but not all, age-related effects.

---

### **Conclusions**

This project provided meaningful insight into the interplay between **education, exercise, and BMI** as measures of health behavior and outcomes.

* The BRFSS dataset proved invaluable for public health analytics.
* The analysis reinforced established health trends: lifestyle choices and education level are key predictors of weight and wellness.
* While predictive accuracy was moderate, the model effectively captured broad behavioral relationships.

Future work could incorporate **dietary variables**, **income**, or **regional factors** to refine prediction accuracy and expand the health profile analysis.

---
