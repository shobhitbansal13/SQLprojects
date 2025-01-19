### **Scenario 1: Heart Attack Likelihood vs. BMI & Stress Levels**

**SQL Query Task 1:**

- Retrieve the average BMI and stress levels for individuals with a positive heart attack likelihood, group by heart attack likelihood

**Sample Output:**
| Heart Attack Likelihood | Average BMI | Average Stress Level |
|-------------------------|-------------|----------------------|
| Yes | 28.5 | 7.3 |
| No | 24.2 | 5.1 |

**SQL Query Task 2:**

- Retrieve the count of individuals with a BMI above 30 and stress level is high, grouped by heart attack likelihood.

**Sample Output:**
| Heart Attack Likelihood | Count of High BMI & Stress |
|-------------------------|----------------------------|
| Yes | 85 |
| No | 45 |



### **Scenario 2: Cholesterol and Physical Activity**

**SQL Query Task 1:**

- Retrieve the average cholesterol level and moderate physical activity level for individuals with different heart attack likelihoods.

**Sample Output:**
| Heart Attack Likelihood | Average Cholesterol Level | Average Physical Activity |
|-------------------------|---------------------------|---------------------------|
| Yes | 250 | 2.5 |
| No | 210 | 4.1 |

**SQL Query Task 2:**

- Retrieve the count of individuals with high cholesterol (above 240) and their corresponding physical activity levels.

**Sample Output:**
| Physical Activity Level | Count of High Cholesterol |
|-------------------------|---------------------------|
| Low | 30 |
| Medium | 60 |
| High | 45 |


### **Scenario 3: Socioeconomic Status and Stress Levels**

**SQL Query Task 1:**

- Retrieve the average stress level for individuals, grouped by their socioeconomic status.

**Sample Output:**
| Socioeconomic Status | Average Stress Level |
|----------------------|----------------------|
| Low | 6.1 |
| Medium | 5.4 |
| High | 4.7 |

**SQL Query Task 2:**

- Retrieve the count of individuals in each socioeconomic status category who have high stress levels .

**Sample Output:**
| Socioeconomic Status | Count of High Stress |
|----------------------|----------------------|
| Low | 75 |
| Medium | 50 |
| High | 30 |



### **Scenario 4: Heart Attack Likelihood by Region**

**SQL Query Task 1:**

- Retrieve the number of individuals in each region with heart attack likelihood (Yes/No).

**Sample Output:**
| Region | Heart Attack Likelihood (Yes) | Heart Attack Likelihood (No) |
|---------|-------------------------------|------------------------------|
| North | 120 | 300 |
| South | 80 | 220 |
| East | 60 | 180 |
| West | 90 | 210 |

**SQL Query Task 2:**

- Retrieve the average age of individuals with a positive heart attack likelihood, grouped by region.

**Sample Output:**
| Region | Average Age (Yes) |
|---------|-------------------|
| North | 45 |
| South | 42 |
| East | 40 |
| West | 43 |



---

### **Scenario 5: Age Group and Heart Attack Risk (Advanced)**

**SQL Query Task 1:**

- Retrieve the age group, gender, and  stress level for individuals 
  Additionally, for each group, calculate the number of individuals whose stress levels are in high and  low
  Return the results in a table sorted by age group and gender.

**Sample Output:**
| Age Group | Gender | Heart Attack Likelihood |  Stress Level | Top 25% Stress Count | Bottom 25% Stress Count |
|-----------|--------|-------------------------|----------------------|----------------------|-------------------------|
| 18-25 | Male | Yes | 7.5 | 15 | 5 |
| 18-25 | Female | Yes | 6.2 | 10 | 7 |
| 26-30 | Male | No | 4.8 | 30 | 4 |
| 26-30 | Female | No | 5.1 | 25 | 6 |

**SQL Query Task 2:**

- Retrieve the total count of individuals in each age group who exhibit a high stress level , segmented by gender and heart attack likelihood. Include the percentage of total individuals in each group with high stress.

**Sample Output:**
| Age Group | Gender | Heart Attack Likelihood | High Stress Count | Total Count | High Stress Percentage |
|-----------|--------|-------------------------|-------------------|-------------|------------------------|
| 18-25 | Male | Yes | 25 | 40 | 62.5% |
| 18-25 | Female | No | 10 | 30 | 33.3% |
| 26-30 | Male | Yes | 20 | 50 | 40% |
| 26-30 | Female | No | 12 | 45 | 26.7% |


---

### **Scenario 6: Gender and Heart Attack Likelihood (Advanced)**

**SQL Query Task 1:**

- Retrieve the average BMI for males and females with positive heart attack likelihood, segmented by age group, and calculate the correlation coefficient between BMI and cholesterol levels for each gender.

**Sample Output:**
| Age Group | Gender | Average BMI | Cholesterol Correlation Coefficient |
|-----------|--------|-------------|-------------------------------------|
| 18-25 | Male | 29.5 | 0.75 |
| 18-25 | Female | 27.8 | 0.63 |
| 26-30 | Male | 31.1 | 0.85 |
| 26-30 | Female | 28.4 | 0.72 |

**SQL Query Task 2:**

- Calculate the relative risk of heart attack (using a formula) based on BMI, cholesterol levels, and gender, and categorize individuals into "High Risk","medium risk", "Low Risk" groups. Retrieve the count of individuals in each risk group, segmented by age and gender.

**Sample Output:**
| Age Group | Gender | Risk Group | Count |
|-----------|--------|--------------|-------|
| 18-25 | Male | High Risk | 15 |
| 18-25 | Female | medium Risk | 20 |
| 26-30 | Male | High Risk | 35 |
| 26-30 | Female | Low Risk | 10 |



### **Scenario 7: Physical Activity and Heart Attack Risk (Advanced)**

**SQL Query Task 1:**

Question: Calculate the number of individuals in each screen time category (low, moderate, high) who have a positive heart attack likelihood. For each category, calculate the standard deviation.

Screen Time Categories:

Low: Less than 3 hours per day
Moderate: 4 to 7 hours per day
High: More than 7 hours per day.

**Sample Output:**
| Physical Activity Category | Heart Attack Likelihood | Median Activity | Activity Std Dev |
|----------------------------|-------------------------|-----------------|------------------|
| Low | Yes | 1.5 | 0.7 |
| Moderate | Yes | 3.2 | 1.1 |
| High | Yes | 5.0 | 1.5 |

**SQL Query Task 2:**

- For individuals with high physical activity levels, retrieve the average cholesterol level, segmented by age group and heart attack likelihood, and calculate the variance for each group.

**Sample Output:**
| Age Group | Heart Attack Likelihood | Average Cholesterol Level | Cholesterol Variance |
|-----------|-------------------------|---------------------------|----------------------|
| 18-25 | Yes | 250 | 45 |
| 26-30 | Yes | 275 | 55 |
| 31-40 | No | 210 | 30 |


---

### **Scenario 8: Family History of Heart Disease and Heart Attack Likelihood (Advanced)**

**SQL Query Task 1:**

- Retrieve the percentage of individuals with a family history of heart disease who have a positive heart attack likelihood, segmented by age group, and also return the percentage of individuals with high cholesterol levels (above 240).

**Sample Output:**
| Age Group | Family History | Heart Attack Likelihood (%) | High Cholesterol (%) |
|-----------|----------------|-----------------------------|----------------------|
| 18-25 | Yes | 65 | 40 |
| 26-30 | Yes | 80 | 50 |
| 31-40 | No | 30 | 25 |

**SQL Query Task 2:**

- Calculate the odds ratio of having a family history of heart disease for individuals who have a positive heart attack likelihood compared to those with negative likelihood, segmented by gender.

**Sample Output:**
| Gender | Odds Ratio (Family History & Heart Attack) |
|--------|--------------------------------------------|
| Male | 2.4 |
| Female | 1.8 |



### **Scenario 9: Blood Pressure and Heart Attack Risk (Advanced)**

**SQL Query Task 1:**

- Retrieve the average systolic and diastolic blood pressure for individuals with a heart attack risk, segmented by age group, and calculate the blood pressure range (max-min) for each group.

**Sample Output:**
| Age Group | Heart Attack Likelihood | Avg Systolic BP | Avg Diastolic BP | BP Range (Systolic) | BP Range (Diastolic) |
|-----------|-------------------------|-----------------|------------------|---------------------|----------------------|
| 18-25 | Yes | 145 | 90 | 30 | 15 |
| 26-30 | No | 120 | 75 | 20 | 10 |

**SQL Query Task 2:**

- For individuals with high blood pressure (systolic > 140), calculate the relative risk for heart attack, segmented by age group and gender. Return the total count of high blood pressure individuals in each group.

**Sample Output:**
| Age Group | Gender | Heart Attack Likelihood | High BP Count | Relative Risk |
|-----------|--------|-------------------------|---------------|---------------|
| 18-25 | Male | Yes | 10 | 2.1 |
| 26-30 | Female | Yes | 20 | 3.5 |
| 31-40 | Male | No | 15 | 1.3 |



### **Scenario 10: Weight and Heart Attack Risk (Advanced)**

**SQL Query Task 1:**

- Retrieve the weight distribution of individuals who are at risk for heart attacks, segmented by gender and age group.  

**Sample Output:**
| Age Group | Gender | Weight Distribution  |
|-----------|--------|------------------------------|
| 18-25 | Male | 0.45 |
| 18-25 | Female | 0.55 |
| 26-30 | Male | 0.32 |
| 26-30 | Female | 0.41 |

**SQL Query Task 2:**

- For individuals with a BMI greater than 30 (obese), calculate the average cholesterol levels and segment by gender and heart attack likelihood.

**Sample Output:**
| Age Group | Gender | Heart Attack Likelihood | Avg Cholesterol |
|-----------|--------|-------------------------|-----------------|
| 18-25 | Male | Yes | 250 |
| 18-25 | Female | No | 230 |
| 26-30 | Male | Yes | 270 |
| 26-30 | Female | No | 240 |


---

### **Scenario 11: Distribution of Age and Heart Attack Risk**

**SQL Query Task 1:**

- Retrieve the count of individuals in each age group with heart attack likelihood (Yes/No), grouped by age range (18-25, 26-30, 31-40, 41-50, 51+).

**Sample Output:**
| Age Group | Heart Attack Likelihood (Yes) | Heart Attack Likelihood (No) |
|-----------|-------------------------------|------------------------------|
| 18-25 | 40 | 120 |
| 26-30 | 60 | 100 |
| 31-40 | 80 | 150 |
| 41-50 | 70 | 130 |
| 51+ | 30 | 50 |

**SQL Query Task 2:**

- Retrieve the distribution of heart attack likelihood (Yes/No) for individuals with varying age groups (18-25, 26-30, etc.), including the average cholesterol level for each group.

**Sample Output:**
| Age Group | Heart Attack Likelihood | Average Cholesterol Level |
|-----------|-------------------------|---------------------------|
| 18-25 | Yes | 220 |
| 18-25 | No | 190 |
| 26-30 | Yes | 250 |
| 26-30 | No | 210 |
| ... | ... | ... |



### **Scenario 12: Stress Levels by Gender and Age**

**SQL Query Task 1:**

- Retrieve the count of stress levels for individuals segmented by gender and age group (18-25, 26-30, 31-40, 41-50, 51+).

**Sample Output:**
| Age Group | Gender | Average Stress Level |
|-----------|--------|----------------------|
| 18-25 | Male | 6.5 |
| 18-25 | Female | 7.2 |
| 26-30 | Male | 7.1 |
| 26-30 | Female | 6.9 |
| ... | ... | ... |

**SQL Query Task 2:**

- Retrieve the count of individuals with high stress levels  across different gender and age group combinations.

**Sample Output:**
| Age Group | Gender | Count of High Stress |
|-----------|--------|----------------------|
| 18-25 | Male | 20 |
| 18-25 | Female | 40 |
| 26-30 | Male | 25 |
| 26-30 | Female | 35 |
| ... | ... | ... |

