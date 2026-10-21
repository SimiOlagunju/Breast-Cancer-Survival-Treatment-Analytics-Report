# Breast Cancer Survival & Treatment Analytics Report
Power BI Project | Survival Analysis, Treatment Outcomes, Recurrence Patterns & Mortality Intelligence

### Table of Contents
* [Project Overview](#project-overview)
* [Tools Used](#tools-used)
* [Dataset Overview](#dataset-overview)
* [Data Preparation](#data-preparation)
* [Exploratory Analysis](#exploratory-analysis)
* [Power BI Dashboard](#power-bi-dashboard)
* [Key Metrics](#key-metrics)
* [Key Insights](#key-insights)
* [Recommendations](#recommendations)
* [Dataset Source](#dataset-source)

---

### Project Overview
This project analyses breast cancer patient data to uncover survival patterns, treatment effectiveness, recurrence rates and mortality trends across different cancer stages, age groups and treatment types.

> The goal is to:
> - Understand overall survival and mortality rates across cancer stages
> - Evaluate which treatment types deliver the best survival outcomes
> - Identify recurrence patterns by treatment type and cancer stage
> - Analyse how age group and cancer type influence survival probability
> - Support data-driven clinical intelligence for healthcare decision makers

---

### Tools Used
- **Power BI Desktop** — Data modelling, DAX measure development and interactive dashboard design

---

### Dataset Overview
The dataset contains breast cancer patient records including demographics, diagnosis information, treatment types and clinical outcomes.

> - Patient demographics (age, gender, affected breast)
> - Diagnosis information (cancer stage, cancer type)
> - Treatment details (treatment type, recurrence status)
> - Clinical outcomes (survival status, survival months, mortality)

- **Total Patients:** 5,000
- **Cancer Stages:** Stage 0, Stage 1, Stage 2, Stage 3, Stage 4
- **Cancer Types:** Inflammatory, Ductal Carcinoma, Lobular Carcinoma, Triple Negative
- **Treatment Types:** Surgery, Targeted Therapy, Combination, Chemotherapy, Radiation, Hormone Therapy
- **Affected Breast:** Bilateral, Left, Right

**Dataset Sample Preview**

| Patient_ID | Age | Gender | Cancer_Stage | Cancer_Type | Treatment_Type | Survival_Months | Survived | Recurrence |
|-----------|-----|--------|-------------|------------|----------------|----------------|----------|------------|
| P001 | 54 | Female | Stage 2 | Ductal Carcinoma | Surgery | 48 | Yes | No |
| P002 | 67 | Female | Stage 4 | Triple Negative | Chemotherapy | 12 | No | Yes |
| P003 | 43 | Male | Stage 1 | Lobular Carcinoma | Radiation | 60 | Yes | No |

---

### Data Preparation
Key preparation steps performed in Power BI:

- Validated patient record completeness across all key fields
- Standardised cancer stage, cancer type and treatment type values for consistency
- Created Age Band calculated column grouping patients into: Under 30, 30-39, 40-49, 50-59, 60-69, 70+
- Verified survival month ranges and recurrence flag consistency across records
- Created DAX measures table organising all clinical calculations by business area

---

### Exploratory Analysis
The following summarises the key clinical questions explored and how they were answered using DAX measures and Power BI visuals.

**1. Overall survival and mortality summary**
```
Total Patients         = 5,000
Overall Survival Rate  = 75%
Overall Mortality Rate = 25%
Avg Survival Months    = 29.5
```

**2. Survival rate by cancer stage**
```
Stage 0 = 96%  ← best survival rate
Stage 1 = 95%
Stage 2 = 80%
Stage 3 = 56%
Stage 4 = 54%  ← lowest survival rate
```

**3. Mortality rate by cancer stage**
```
Stage 4 = 46%  ← highest mortality
Stage 3 = 44%
Stage 2 = 20%
Stage 1 = 5%
Stage 0 = 4%   ← lowest mortality
```

**4. Recurrence rate by treatment type**
```
Overall Recurrence Rate = 30.1%

Surgery          = 32%  ← highest recurrence
Targeted Therapy = 31%
Combination      = 31%
Chemotherapy     = 30%
Radiation        = 30%
Hormone Therapy  = 28%  ← lowest recurrence (H R Treatment Surgery = 31.7%)
```

**5. Patient distribution by age group**
```
70+     = 1,353  ← largest group
60-69   =   846
50-59   =   821
40-49   =   794
30-39   =   768
Under 30 =  418  ← smallest group
```

**6. Cancer type distribution**
```
Inflammatory      = 25.82%
Ductal Carcinoma  = 24.98%
Triple Negative   = 24.66%
Lobular Carcinoma = 24.54%
```

**Key DAX Measures Created:**
```
Total Patients        = COUNTROWS(patient_table)
Survival Rate %       = DIVIDE(COUNT of survived patients, Total Patients, 0) * 100
Mortality Rate %      = DIVIDE(COUNT of deceased patients, Total Patients, 0) * 100
Recurrence Rate %     = DIVIDE(COUNT of recurrence = Yes, Total Patients, 0) * 100
Avg Survival Months   = AVERAGE(patient_table[survival_months])
Survival by Stage     = CALCULATE(Survival Rate %, FILTER by stage)
Mortality by Stage    = CALCULATE(Mortality Rate %, FILTER by stage)
```

---

### Power BI Dashboard
The dashboard provides a single-page interactive clinical analytics report with dynamic filtering by gender, recurrence status, affected breast and treatment type.

<img width="1366" height="768" alt="Screenshot (102)" src="https://github.com/user-attachments/assets/6811f143-da54-4167-b4ba-7fe5ad110f44" />


**Dashboard Features**

> **KPI Cards with Sparklines:**
> - Total Patients — vs Avg Diagnosed per year (5,000)
> - Survival Rate % — Best Surviving Stage: Stage 0 (96.4%)
> - Mortality Rate % — Most Affected Stage: Stage 4 (46%)
> - Recurrence Rate % — Highest Recurrence: H R Treatment Surgery (31.7%)
> - Avg Survival Months — vs Overall Avg Months (30)

> **Interactive Filters / Slicers:**
> - Gender (Female / Male)
> - Recurrence (No / Yes)
> - Affected Breast (Bilateral / Left / Right)
> - Treatment Type (Chemotherapy / Combination / Hormone Therapy / Radiation / Surgery / Targeted Therapy)
> - Cancer Stage (Stage 0 / Stage 1 / Stage 2 / Stage 3 / Stage 4)

**Visuals — Single Page Dashboard**

| # | Visual | Chart Type | Insight |
|---|--------|-----------|---------|
| 1 | KPI — Total Patients | Card with Sparkline | 5,000 patients tracked |
| 2 | KPI — Survival Rate % | Card with Sparkline | 75% overall survival |
| 3 | KPI — Mortality Rate % | Card with Sparkline | 25% overall mortality |
| 4 | KPI — Recurrence Rate % | Card with Sparkline | 30.1% recurrence |
| 5 | KPI — Avg Survival Months | Card with Sparkline | 29.5 months average |
| 6 | Age Group Distribution | Bar Chart | 70+ is largest patient group |
| 7 | Recurrence by Treatment Type | Donut Chart | Surgery has highest recurrence at 32% |
| 8 | Survival Rate % and Mortality Rate % by Age Group | Clustered Bar Chart | Survival vs mortality across age bands |
| 9 | Survival Rate % by Cancer Stage | Bar Chart | Stage 0 leads at 96% |
| 10 | Cancer Type Distribution | Donut Chart | Evenly split across 4 types |
| 11 | Mortality Rate % by Cancer Stage | Bar Chart | Stage 4 highest at 46% |
| 12 | Medical Imagery | Image Visual | Anatomical breast cancer illustrations |

---

### Key Metrics

| Metric | Value |
|--------|-------|
| Total Patients | 5,000 |
| Overall Survival Rate | 75% |
| Overall Mortality Rate | 25% |
| Recurrence Rate | 30.1% |
| Avg Survival Months | 29.5 |
| Best Survival Stage | Stage 0 (96%) |
| Worst Survival Stage | Stage 4 (54%) |
| Highest Mortality Stage | Stage 4 (46%) |
| Highest Recurrence Treatment | Surgery (32%) |
| Lowest Recurrence Treatment | Hormone Therapy (28%) |
| Largest Age Group | 70+ (1,353 patients) |

---

### Key Insights

**1. Early stage detection is the single most critical survival factor**
- Stage 0 patients survive at 96% while Stage 4 drops to 54% — a 42 percentage point gap. This stark difference confirms that early detection programmes are the most impactful intervention available to improve survival outcomes across the patient population.

**2. Stage 4 carries disproportionate mortality risk**
- Stage 4 patients face a 46% mortality rate compared to just 4% at Stage 0. The rapid mortality escalation between Stage 2 (20%) and Stage 3 (44%) highlights a critical transition point where treatment outcomes change dramatically — reinforcing the urgency of Stage 2 intervention.

**3. Surgery has the highest recurrence rate despite being a primary treatment**
- Surgery carries a 32% recurrence rate — the highest of all treatment types. In contrast Hormone Therapy shows the lowest recurrence at 28%. This 4 percentage point gap warrants further investigation into whether combination approaches post-surgery could reduce recurrence risk.

**4. Older patients represent the largest patient group but face compounding risk**
- The 70+ age group is the largest cohort at 1,353 patients — nearly triple the Under 30 group. Older patients typically present with later stage diagnoses and reduced treatment tolerance, making age-sensitive treatment planning essential for this dominant group.

**5. Cancer type is evenly distributed — no single type dominates**
- All four cancer types (Inflammatory, Ductal Carcinoma, Lobular Carcinoma, Triple Negative) each account for approximately 25% of the patient population. This even distribution means treatment resources and research investment should be maintained equally across all four types rather than concentrating on any single diagnosis.

**6. Survival and mortality rates are mirror images across age groups**
- Survival rate and mortality rate charts move in opposite directions across age groups — as survival increases mortality decreases proportionally. This confirms the dataset's internal consistency and validates the reliability of the clinical outcome measures used throughout the analysis.

**7. Overall recurrence rate of 30.1% represents a significant clinical challenge**
- Nearly 1 in 3 patients experiences cancer recurrence regardless of treatment type. With recurrence rates clustered tightly between 28% and 32% across all treatment types, no single treatment decisively prevents recurrence — suggesting multi-modal combination approaches should be prioritised.

---

### Recommendations

**1. Invest in early detection and screening programmes**
- The 42 percentage point survival gap between Stage 0 and Stage 4 makes early detection the highest-return clinical intervention available. Healthcare providers should prioritise funding for community-level screening especially for the 70+ population who represent the largest patient group.

**2. Review post-surgery recurrence prevention protocols**
- Surgery's 32% recurrence rate — the highest of all treatment types — suggests current post-surgical follow-up may be insufficient. Clinical teams should evaluate whether adjuvant therapies (hormone therapy, targeted therapy) applied systematically after surgery could reduce recurrence rates toward the 28% benchmark set by Hormone Therapy.

**3. Develop age-sensitive treatment pathways for older patients**
- With 70+ patients representing 27% of the total patient population, age-specific clinical protocols are essential. Treatment plans for older patients should account for reduced physiological tolerance while maintaining access to the full range of treatment options.

**4. Prioritise Stage 2 intervention to prevent Stage 3 mortality escalation**
- Mortality jumps from 20% at Stage 2 to 44% at Stage 3 — a 24 percentage point increase. Clinical pathways that accelerate intervention at Stage 2 could prevent a significant proportion of Stage 3 mortality. Patient monitoring frequency should increase substantially at Stage 2 diagnosis.

**5. Maintain balanced research investment across all four cancer types**
- With each cancer type representing approximately 25% of patients, research and treatment development should avoid over-indexing on any single type. Equal investment across Inflammatory, Ductal Carcinoma, Lobular Carcinoma and Triple Negative cancer types will deliver the broadest patient benefit.

**6. Investigate Hormone Therapy's lower recurrence rate**
- At 28% recurrence Hormone Therapy outperforms all other treatment types on recurrence prevention. A dedicated study into the mechanisms driving this outcome could inform broader treatment protocol improvements and potentially reduce the overall 30.1% recurrence rate across the patient population.

---

### Dataset Source
The dataset was sourced and adapted for analytical and portfolio purposes, representing breast cancer patient records across multiple cancer stages, treatment types and clinical outcomes. It contains no real patient data and is used solely for educational data analysis.

---

*Project by Similoluwa Olagunju | MSc Business Analytics*
*Tool: Power BI Desktop*
*Connect on LinkedIn: www.linkedin.com/in/simiolagunju
