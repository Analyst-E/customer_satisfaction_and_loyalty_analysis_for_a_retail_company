# Technical Document: Customer Satisfaction and Loyalty Analysis for a Retail Company

## 1.0. Project Overview
In this portfolio project, I acted as the Data Analyst for a retail company. The management's objective was to understand the relationship between customer satisfaction across various aspects (product quality, service speed, and pricing) and key loyalty indicators: likelihood to repurchase and willingness to recommend. The goal was to derive actionable insights that could inform decision-making and enhance customer retention strategies.

To achieve this, a structured questionnaire was designed to capture customer satisfaction levels and loyalty indicators. The dataset consisted of 238 survey responses, including demographic information such as age group and gender.

## 2.0. Survey Demographics
The breakdown of the demographics is as follows:

1. Age Distribution
The respondents were distributed across four age groups:

![image](https://github.com/user-attachments/assets/11a246f0-4e6b-4484-9605-60e6cdc5cde0)

2. Gender Distribution
Out of the 238 respondents:
- 124 (52%) were female
- 114 (48%) were male

## 3.0. Analysis Framework
The analysis involved five variables:
1. Dependent Variables (Loyalty Indicators):
- Likelihood to Repurchase
- Willingness to Recommend
- Independent Variables (Customer Satisfaction Factors):

2. Product Quality
- Service Speed
- Pricing

The relationship between these variables was explored to uncover key insights into customer loyalty.

## 4.0. Data Transformation
### 4.1. Why Transformation is Necessary

Before proceeding with statistical analysis, the variables were transformed to ensure compatibility with the analytical methods. This step was crucial because:
- The data collected was ordinal, meaning it had a rank order (e.g., Strongly Agree > Agree > Neutral), but the intervals between ranks were not necessarily equal.
- Using inappropriate transformations (e.g., mean) could introduce bias, as the mean assumes equal intervals between response categories.

### 4.2. Median Transformation
The median was used to transform the data instead of the mean for the following reasons:

The median captures the central tendency of ordinal data better by identifying the middle value in the distribution.
- It is robust to outliers, which is particularly important for skewed responses often seen in survey data.
- Avoids assumptions about equal intervals between Likert scale options.

The data was transformed using SPSS's built-in transform feature to create variables that better represent the central tendency of responses for each factor.

## 5.0. Parametric and Non-Parametric Tests
### 5.1. The Case Against Parametric Tests

While parametric tests are often preferred for their statistical power, they require several key assumptions, including:

1. **Normality**: The data should follow a normal distribution.
2. **Interval Scale Data**: The differences between values must be equal and meaningful.

Since Likert scale data is ordinal and does not meet these assumptions, parametric tests like linear regression or Pearson’s correlation are not suitable.

### 5.2. Non-Parametric Alternatives
Non-parametric methods were employed to handle the ordinal nature of the data:

1. **Spearman’s Rank Correlation**

- Measures the strength and direction of the relationship between variables.
- Suitable for ordinal data without requiring normality.

2. **Ordinal Logistic Regression**

- Used to predict the likelihood of an outcome based on multiple independent variables.
- Handles ordinal dependent variables effectively by considering their rank-order structure.

## 6.0. Why Normality Tests Were Skipped
Performing normality tests (e.g., Shapiro-Wilk or Kolmogorov-Smirnov) is standard practice in many analyses to check if the data satisfies the assumptions for parametric tests. However, in this case:

- **Ordinal Data Limitation**: Likert scale data is inherently non-normal and ordinal, making the results of normality tests irrelevant.
- **Focus on Robust Methods**: The analysis prioritized robust non-parametric techniques that do not depend on normality assumptions

## 7.0. Likelihood to Repurchase

### 7.1. Ordinal Logistic Regression Analysis
The initial analysis used ordinal logistic regression to explore the relationship between satisfaction factors (Product Quality, Service Speed, and Pricing) and Likelihood to Repurchase. Ordinal logistic regression assumes the proportional odds assumption, meaning that the relationship between predictors and the dependent variable is consistent across all levels of the dependent variable.

#### 7.1.1. Model Fitting Information
The model-fitting table indicates the model’s statistical significance, with a chi-square test value of 34.863 and a p-value < 0.05, suggesting that the model provides a better fit than the null (intercept-only) model. This indicates that at least one predictor significantly affects the likelihood to repurchase. This is shown in the table below
![image](https://github.com/user-attachments/assets/815c64c8-74ff-4067-843a-ce261693ad97)

#### 7.1.2. Goodness-of-Fit Test
This test evaluates how well the model fits the data, using Pearson and Deviance chi-square statistics. Results indicate:
![image](https://github.com/user-attachments/assets/abc0ccf8-3898-4034-9a25-1117c956bcf4)
Both tests have p-values < 0.05, suggesting poor model fit. This indicates that the current model may not adequately describe the observed data.

#### 7.1.3. Test of parralel lines
The proportional odds assumption is evaluated using the test of parallel lines. The test results are:
![image](https://github.com/user-attachments/assets/c7bb862d-7b05-4e54-ac46-cc5a8cdbb986)
The p-value = 0.004 rejects the null hypothesis, confirming that the proportional odds assumption is violated. Consequently, ordinal logistic regression is unsuitable for this data.

### 7.2 Multinomial Logistic Regression Analysis
Since the ordinal logistic regression violated key assumptions, multinomial logistic regression was used as an alternative. Multinomial regression does not assume proportional odds and is appropriate for categorical dependent variables with more than two levels. To simplify the analysis, the dependent variable (Likelihood to Repurchase) was re-categorized into three levels:

1. Low: Satisfaction scores 1–2
2. Neutral: Score 3
3. High: Scores 4–5

#### 7.2.1 Model Fitting Information for Multinomial Logistic Regression
![image](https://github.com/user-attachments/assets/58df5390-25d1-4849-b456-b65f105d3215)

The p-value < 0.05 confirms the statistical significance of the predictors in explaining the dependent variable.

#### 7.2.2. Goodness-of-Fit Test for Multinomial Logistic Regression
Results indicate:
![image](https://github.com/user-attachments/assets/22147050-c7fe-4e2d-99af-c070a617064a)

Both tests have p-values > 0.05, suggesting that the model fits the data well.

#### 7.2.3. Parameter Estimates
The parameter estimates table allows for interpretation of the predictors:
![image](https://github.com/user-attachments/assets/cd42d5e0-bca2-4f39-97ae-0468c30dfd8a)

**I. Product Quality (M_PQ):**
- For Neutral:  𝐵 = 13.813, 𝑝 = 0.980, Exp(𝐵) = 997, 427.417
- For High: 𝐵 = 14.112, 𝑝 = 0.979, Exp(𝐵) = 1,345,564.333

While the odds ratios suggest a strong association between product quality and higher likelihood to repurchase, the high p-values (> 0.05) indicate no statistical significance.

**II. Service Speed (M_SS):**
- For Neutral: 𝐵 = 13.015, 𝑝 = 0.000, Exp(𝐵) = 449,006.619
- For High: 𝐵 = 13.884, Exp(𝐵) = 1,071,261.868

Service speed shows a statistically significant effect on the likelihood to repurchase in the Neutral category (p = 0.000) and a strong effect in the High category (missing p-value).

**III. Pricing (M_PC):**
- For Neutral: 𝐵 = 0.586, 𝑝 = 0.999, Exp(𝐵)= 1.797
- For High: 𝐵 = 1.030, 𝑝 = 0.999, Exp(𝐵) = 2.800

Pricing shows minimal influence on likelihood to repurchase, with no statistical significance in either category.

**Interpretation**
The results suggest:

- Service Speed has a statistically significant impact on customers’ likelihood to repurchase, emphasizing the importance of timely service delivery.
- While Product Quality and Pricing appear to have large odds ratios, their effects are not statistically significant, possibly due to limited variability or other factors in the data.

## 8.0 Likelihood to recommend
### 8.1. Ordinal Regression Interpretation

#### 8.2. Model Fit:
The Model Fitting Information table shows the model fits the data:
![image](https://github.com/user-attachments/assets/4e5a58b6-1146-48d1-b059-a870b29439b7)


A significant Chi-Square value (𝑝 = 0.000) suggests the model is better than the null model.

![image](https://github.com/user-attachments/assets/17ffa40e-2d1e-4022-a32e-c053ac72ff82)

However, the Goodness-of-Fit table indicates a poor fit (𝑝 = 0.002 for Pearson and 𝑝 = 0.017 for Deviance). This indicates the model does not capture all variability in the data, necessitating further consideration of model diagnostics.

#### 8.3. Parallel Lines Test:
As seen in the earlier test for the Likelihood to repurchase variable, the violation of the parallel lines assumption for the Likelihood to recommend variable (𝑝 < 0.05) suggests that Multinomial Logistic Regression is more appropriate for this data.

#### 8.4. Multinomial Logistic Regression Results (Likelihood to Recommend)
![image](https://github.com/user-attachments/assets/53887f67-616e-423f-ba2c-c2e3c60ff65d)

**Category: Low (Compared to High)**

None of the predictors (Product Quality, Service Speed, or Pricing) are statistically significant for predicting the "Low" category:

- M_PQ (Product Quality): 𝑏 = −22.351, 𝑝 = 0.999
- M_SS (Service Speed): 𝑏 = −22.021, 𝑝 = 0.999
- M_PC (Pricing): 𝑏 = −0.920, 𝑝 = 1.000

Conclusion: None of the predictors influence the likelihood of falling into the "Low" recommendation category compared to "High."

**Category: Neutral (Compared to High)**
Intercept: 𝑏 = 4.368, 𝑝 = 0.020
Statistically significant, suggesting the "Neutral" category has a distinct baseline likelihood compared to "High."

**I. M_PQ (Product Quality):**
- 𝑏 = − 0.875, 𝑝 = 0.010
- A one-unit increase in Product Quality reduces the odds of being in the "Neutral" category by 58.3% compared to "High."

**II. M_SS (Service Speed):**
- 𝑏 = −0.910, 𝑝 = 0.008
- A one-unit increase in Service Speed reduces the odds of being in the "Neutral" category by 59.7% compared to "High."

**III. M_PC (Pricing):**
- 𝑏 = 0.088, 𝑝 = 0.794
- Not significant. Pricing has no meaningful impact on distinguishing between "Neutral" and "High" likelihood to recommend.

Conclusion: Product Quality and Service Speed are significant factors in predicting whether customers rate their recommendation as "Neutral" instead of "High."

### 9.0. Spearman Rank Correlation
![image](https://github.com/user-attachments/assets/6aab5e7e-f8dc-492c-98f8-9002b76b9775)

**Summary:**
- Strongest Correlations:
- - M_RP (Recommendation Probability) and M_RC (Recommendation Clarity):  𝑟𝑠 = 0.257, 𝑝 < 0.01
- - - This emphasizes the importance of clear communication in driving customer recommendations.

- - M_PC (Pricing) and M_RP (Recommendation Probability): 𝑟𝑠 = 0.242, 𝑝 < 0.01

- Significant Positive Relationships:
- - All predictors (Product Quality, Service Speed, Pricing) show positive relationships with Recommendation Probability and Clarity, though the strength varies.

**Interpretation:**
- Product Quality and Service Speed consistently show moderate to strong effects on recommendation-related variables.
- Pricing plays a less dominant but still relevant role in shaping customer perceptions.
