# HR Attrition & Tenure Analysis
### A Power BI Report | Turki Almutairi

---

## Overview

This report analyzes employee attrition and tenure patterns using the **IBM HR Analytics Employee Attrition dataset** (1,470 employees). The goal is to identify who is leaving, where attrition is most concentrated, and what factors drive it — providing actionable insights for HR decision-makers.

The report was built entirely in **Power BI** using DAX measures, conditional formatting, and interactive cross-filtering across three pages.

---

## Dataset

- **Source:** [IBM HR Analytics Employee Attrition & Performance](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)
- **Size:** 1,470 employees, 35 columns
- **Type:** Real-world inspired synthetic dataset
- **Key columns used:** `Attrition`, `YearsAtCompany`, `JobRole`, `JobLevel`, `OverTime`, `MonthlyIncome`, `MaritalStatus`, `BusinessTravel`, `YearsSinceLastPromotion`, `Department`

---

## Report Structure

### Page 1 — Employees Attrition & Tenure Overview
A high-level snapshot of the company's retention state.

![Overview](images/1-%20overview.png)

**Key Metrics:**
- 1,470 total employees
- 237 employees left the company
- 162 employees left within 5 years
- 16.12% overall attrition rate

**Visuals:**
- Tenure Distribution — shows the concentration of employees in the first 5 years
- Tenure by Department — Sales retains longest (7.28 years), R&D shortest (6.86 years)

**Key Finding:**
> 53% of the workforce have 5 or fewer years of tenure with the company.

---

### Page 2 — Attrition Analysis: Sales Representatives
A deep-dive into why attrition is so high in Sales Representative roles specifically.

![Analysis-1](images/2-%20analysis%201.png)

**Key Metrics:**
- Sales Representatives have a 40% attrition rate — the highest of any role
- Research Directors have a 2.5% attrition rate — despite similar headcount
- SR average monthly pay is $2.6K vs company average of $6.5K
- SR employees average 2.19 years since last promotion

**Visuals:**
- Attrition Rate by Role — with conditional formatting highlighting SR as the outlier
- Distribution of Job Level — SR is dominated by Level 1 (entry-level) employees
- Average Monthly Pay card — SR is significantly below company average
- Average Years Since Promotion card

**Key Finding:**
> Sales Representatives leave at 16x the rate of Research Directors despite similar team sizes. SR employees are predominantly entry-level, underpaid, and infrequently promoted — three factors strongly associated with high attrition.

---

### Page 3 — Attrition Analysis: General Factors
A broader look at company-wide factors that drive attrition regardless of role.

![Analysis-2](images/3-%20analysis%202.png)

**Visuals:**
- Overtime Effect — employees working overtime leave at 31% vs 10% for non-overtime workers
- Marital Status Effect — single employees leave at 26% vs 12% for married employees
- Attrition Rate by Monthly Pay — attrition drops sharply above $5K monthly income
- Attrition Rate by Business Travel — frequent travelers leave at 25% vs 8% for non-travelers

**Key Findings:**
> Overtime workers leave at 3x the rate of non-overtime workers.
> Single employees leave at more than double the rate of married and divorced employees.
> Frequent travelers leave at 3x the rate of non-travelers.
> Employees earning under $5K monthly are significantly more likely to leave.

---

## Tools & Skills Used

| Tool | Usage |
|---|---|
| Power BI Desktop | Report building, data modeling, visualization |
| DAX | Custom measures for attrition rate, early attrition, tenure segmentation |
| Power Query | Data cleaning, column type correction, value replacement |
| Conditional Formatting | Highlighting outlier bars in job role chart |
| Cross-filtering | Interactive exploration across all visuals |

---

## DAX Measures Built

```
Total Attrition = 
COUNTROWS(FILTER('dataset',
'dataset'[Attrition] = "Yes"))

Attrition Rate = 
DIVIDE([Total Attrition], [Total Employees], 0)

Early Attrition = 
COUNTROWS(FILTER('dataset',
'dataset'[Attrition] = "Yes" &&
'dataset'[YearsAtCompany] <= 5))
```

---

## Recommendations

Based on the findings in this report, the following actions are suggested for HR leadership:

1. **Review Sales Representative compensation** — SR average pay of $2.6K is significantly below the company average. A salary review for Level 1 SR employees could directly reduce the 40% attrition rate.

2. **Reduce overtime dependency in customer-facing roles** — overtime workers leave at 3x the rate of others. Redistributing workload or hiring additional SR staff could reduce burnout-driven attrition.

3. **Accelerate promotion timelines for SR** — with an average of 2.19 years since last promotion, SR employees may feel stagnant. A clearer career progression path could improve retention.

4. **Target early-tenure employees** — 53% of the workforce has 5 or fewer years of tenure. Onboarding programs and early engagement initiatives should be prioritized for the first 3 years.

5. **Review business travel policies** — frequent travelers leave at 25% vs 8% for non-travelers. Reducing unnecessary travel or providing better compensation for travel-heavy roles could improve retention.

---

**Author:** Turki Almutairi
**Contact:** Turkinayyaf@proton.me
