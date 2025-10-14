# HR Analytics: Retention Modeling

This project profiles and preprocesses employee turnover data to build a foundation for predictive modeling and workforce retention analysis. It enhances data quality through cleaning, validation, and profiling to enable reliable insights into employee behavior and attrition trends.

The project supports data-driven HR strategy development by:
- Ensuring data integrity and consistency across employee records  
- Preparing structured HR variables suitable for statistical and machine learning models  
- Enabling workforce risk analysis through exploratory data profiling and visualization  

This repository includes the full data preparation workflow, from initial profiling to cleaned dataset output, supporting future retention modeling and predictive analytics.
---

## Project Scope

Employee retention is a key strategic priority for modern organizations, particularly within competitive industries where hiring and training costs are high. This project focuses on building a clean and reliable foundation for analyzing turnover trends and preparing data for predictive modeling.  

The goal is to transform raw HR records into a well-structured dataset that can reveal insights about workforce stability and enable future modeling efforts to predict employee attrition risk.  

Key goals of the project:
- Profile the structure, content, and quality of HR data across multiple employee-related dimensions such as compensation, tenure, satisfaction, and role type.  
- Detect and resolve data integrity issues like missing, inconsistent, or duplicate entries.  
- Standardize variable formats and encode categorical attributes to ensure analytical readiness.  
- Prepare an output dataset suitable for statistical analysis and machine learning pipelines.  

This workflow creates a robust data foundation that can later be integrated with advanced modeling for HR decision-making and retention strategy optimization.

---

## Process

### 1. Data Profiling
The profiling phase provides an overview of the dataset’s composition, structure, and potential quality issues.  
- **Structural Review:** Inspected column data types, formats, and value ranges to determine variable characteristics (numeric, categorical, ordinal).  
- **Summary Statistics:** Generated descriptive summaries (mean, median, standard deviation, frequency) to understand variability.  
- **Completeness Check:** Identified columns with missing or null values, calculated missing percentages, and prioritized remediation.  
- **Data Distribution Analysis:** Created boxplots and histograms to identify potential outliers and skewness in numeric features.  
- **Category Inspection:** Reviewed unique values in categorical columns to uncover inconsistent spellings or casing (e.g., “Direct_Deposit” vs. “Direct Deposit”).  

This stage helped define the cleaning strategy and ensured that subsequent transformations preserved the integrity of the data.

---

### 2. Data Cleaning
The cleaning phase focused on correcting detected inconsistencies, ensuring logical validity, and improving overall data usability.  
- **Missing Values:**  
  - Numeric attributes were imputed with median values to minimize distortion from outliers.  
  - Categorical variables were filled using mode imputation to retain the most frequent category.  
- **Negative and Invalid Values:**  
  - Negative values in salary and commute distance fields were replaced with their absolute values to align with real-world logic.  
- **Duplicate Removal:**  
  - Duplicate employee entries were identified using `.duplicated()` and removed to maintain dataset uniqueness.  
- **Formatting and Standardization:**  
  - Categorical strings were normalized to consistent capitalization and naming conventions (e.g., “DirectDeposit” → “Direct Deposit”).  
- **Outlier Detection:**  
  - Outliers were identified through visualization but retained for domain review, ensuring data completeness for future modeling.  

This systematic approach improved both data accuracy and interpretability, resulting in a high-quality dataset ready for feature engineering and analysis.

---

### 3. Feature Preparation
After cleaning, variables were transformed to ensure analytical compatibility and support future modeling:  
- **Encoding:** Categorical variables were encoded into numerical form suitable for algorithms.  
- **Normalization:** Continuous variables were scaled to reduce magnitude disparity across features.  
- **Derived Features:** Calculated additional attributes such as total experience or tenure categories to enrich predictive capabilities.  
- **Validation:** Verified that all columns followed expected data types, ranges, and logical constraints before export.  

The processed dataset serves as a solid input for building models that predict turnover risk and uncover retention patterns.

---

## Key Findings

This section summarizes the main insights derived from the exploratory data analysis and visual profiling of key employee metrics.

### 1. Boxplot Analysis

Boxplots were used to visualize data spread, detect outliers, and evaluate data consistency across numeric variables.

#### • Age

<img width="520" height="453" alt="image" src="https://github.com/user-attachments/assets/03153779-53fd-45cf-932b-883d31ebda95" />

- The distribution of employee ages is centered around the early-to-mid 40s.
- Most employees fall between **35 and 55 years old**, suggesting a mature workforce.
- No extreme outliers were observed, indicating consistent data entry.

#### • Tenure

<img width="520" height="453" alt="image" src="https://github.com/user-attachments/assets/2420b6fe-5a33-4560-837c-c6e6f05d9d82" />

- Median tenure is approximately **8–9 years**, with most employees having worked between **5 and 13 years**.
- A few long-tenure outliers exist, reflecting long-term employees within the organization.

#### • Annual Salary

<img width="557" height="453" alt="image" src="https://github.com/user-attachments/assets/6cfa14d2-cd89-4731-add5-f8a182c79f11" />

- Salaries are mostly concentrated around **$60K–$150K**, with a median near **$100K**.
- A few outliers above **$250K–$300K** were retained, as they likely represent senior or specialized positions.
- Some negative salary values were identified and corrected during data cleaning.

#### • Driving Commuter Distance

<img width="534" height="453" alt="image" src="https://github.com/user-attachments/assets/a75a6266-8e7a-420d-9fdc-c03ac28fcbb3" />

- The majority of employees commute **under 100 miles**, with a median of **~40 miles**.
- Several negative and extreme outliers were identified before cleaning (e.g., -275, 950 miles). These were converted to absolute values.
- After cleaning, the data shows a realistic commuting distance range.

#### • NumCompaniesPreviouslyWorked

<img width="520" height="453" alt="image" src="https://github.com/user-attachments/assets/d11bc2cb-c9bc-445c-aac1-0a91dada7c26" />

- Median value is **4 companies**, with most employees having experience at **2–6 prior employers**.
- No significant outliers were detected, confirming consistent data entry.

---

### 2. Correlation Heatmap Insights

A correlation heatmap was created to examine relationships among continuous variables.

<img width="984" height="905" alt="image" src="https://github.com/user-attachments/assets/7a2286e1-a665-48d7-b95d-093c598d2950" />

Key observations:
- **Age and Tenure (r = 0.67):** Strong positive relationship; older employees generally have longer tenure.
- **Age and Salary (r = 0.41):** Moderate positive correlation, suggesting earnings increase with experience.
- **Salary and Tenure (r = 0.27):** Indicates that tenure length modestly influences compensation.
- **NumCompaniesPreviouslyWorked:** Shows weak correlations (≤ 0.35) with other variables, implying diverse career paths before current employment.
- **DrivingCommuterDistance:** Almost no correlation with other variables, suggesting commute distance does not directly relate to age, salary, or tenure.

---

### 3. Summary of Insights

- **Data Consistency:** After cleaning, no missing, negative, or duplicate entries remained.  
- **Workforce Composition:** The company primarily employs experienced mid-career professionals with stable tenure.  
- **Retention Factors:** Compensation and tenure emerged as the strongest correlates with employee stability.  
- **Outliers:** Retained outliers represent legitimate high-value or long-serving employees rather than data errors.  

---

### 4. Visual Summary

| Variable | Median | Key Notes |
|-----------|---------|-----------|
| **Age** | 44 years | Balanced distribution, no extreme outliers |
| **Tenure** | 9 years | Longer tenure linked to higher salary |
| **Annual Salary** | \$101K | A few high outliers retained for realism |
| **Commuter Distance** | 42 miles | Negative values fixed, realistic spread |
| **Num Companies Worked** | 4 | Consistent range, no anomalies |

These findings validate the dataset’s readiness for further analysis, such as predictive modeling of employee turnover or compensation analysis.

---

## Analysis of Results

The analysis phase confirmed that data quality issues were effectively addressed, resulting in measurable improvements:

- **Data Integrity:** All missing, inconsistent, and duplicated records were corrected or removed, ensuring that each observation accurately represents a valid employee record.  
- **Consistency:** Variable naming conventions and categorical labels were standardized, improving interpretability and reducing ambiguity across the dataset.  
- **Statistical Balance:** Key numeric fields such as *Annual Salary*, *Tenure*, and *Driving Commuter Distance* displayed cleaner and more interpretable distributions after corrections. Outliers were retained where contextually valid to maintain realism.  
- **Model Readiness:** The final cleaned dataset is now fully structured for predictive modeling workflows. It supports regression or classification pipelines aimed at forecasting employee attrition likelihood.  
- **Preliminary Insights:** Exploratory findings indicated strong relationships between **tenure**, **compensation**, and **satisfaction indicators**, suggesting these as primary drivers of turnover behavior. These patterns will inform feature selection for subsequent modeling and retention strategy design.  

---

## Tools and Technologies

- **Programming Language:** Python  
- **Libraries:** Pandas, NumPy, Seaborn, Matplotlib, Scikit-learn  
- **Environment:** Jupyter Notebook (Anaconda)  
- **Outputs:**  
  - Cleaned dataset in CSV format  
  - Annotated notebook documenting the cleaning process  
  - Visualizations summarizing data quality improvements  

---

## Outcome

The project produced a fully cleaned and validated HR dataset that supports advanced analysis of employee turnover. It establishes a repeatable framework for data cleaning, quality validation, and preprocessing in workforce analytics.  

This structured foundation can now be used to:
- Train predictive models that estimate the likelihood of employee resignation.  
- Identify key drivers influencing turnover, such as work-life balance, salary growth, and managerial tenure.  
- Develop evidence-based strategies for employee retention and resource planning.  

---

## Future Work

Future iterations of this project could include:
- Building machine learning models (e.g., Logistic Regression, Random Forest, or XGBoost) to predict employee attrition.  
- Conducting feature importance analysis to identify the most influential predictors.  
- Developing an interactive dashboard (e.g., in Tableau or Power BI) to visualize turnover risk across departments.  
- Integrating HR analytics pipelines with cloud-based environments for automation and scalability.  
