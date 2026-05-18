# Preventive-Healthcare-Hypertension-Analysis
As part of a public health analytics initiative, this analysis evaluates whether limited access to preventive healthcare is associated with a higher risk of hypertension among U.S. adults and identifies which populations face the greatest risk.


# Project Background

Hypertension is one of the leading preventable drivers of cardiovascular disease in the United States, yet disparities in prevalence persist across socioeconomic and geographic groups.

Preventive care routine screenings, early diagnosis, and ongoing management is widely considered a key mechanism for reducing this burden. However, access to preventive services varies significantly due to differences in insurance coverage, provider availability, and structural conditions.

This analysis examines whether limited preventive care access is associated with higher hypertension prevalence, and more importantly, whether insurance status alters that relationship. The goal is to identify where interventions will have the greatest population-level impact.
  
   
# Executive Summary

Limited access to preventive healthcare is associated with higher hypertension prevalence but this relationship is not uniform across populations.

This analysis finds that insurance status significantly amplifies risk: counties with both low preventive care access and high uninsured rates consistently exhibit the highest hypertension burden.

While increasing routine checkups is associated with lower hypertension overall, access alone does not guarantee improved outcomes. The ability to act on that access—largely determined by insurance coverage—drives whether preventive care translates into meaningful risk reduction.

Key Insight:
Hypertension disparities are driven by the intersection of access, insurance coverage, and structural conditions—not any single factor in isolation.

Supporting Evidence
- +1% increase in routine checkups → ~1.16% decrease in hypertension prevalence (p < 0.001)

- +1% increase in uninsured rate → ~0.62% increase in hypertension prevalence (p < 0.001)

- Preventive care × insurance interaction → statistically significant (p < 0.001)

# Data Structure
The dataset used is a CDC county-level dataset on chronic disease indicators and healthcare access. The analytic structure organizes variables across the following categories:

- Outcome
- Hypertension prevalence (%)
 - Primary Exposure
- Preventive care access indicator (county-level)
- Effect Modifier
- Insurance status (% uninsured by county)
- Confounders / Controls
- Primary care physician rate
- Socioeconomic indicators (education, poverty proxies)
- Behavioral risk factors (obesity rates, smoking prevalence, physical inactivity)
  
This structure reflects a standard epidemiological risk factor–outcome framework with effect modification, commonly applied in chronic disease surveillance and health services research. The county-level, ecological design enables cross-regional comparison but introduces ecological fallacy limitations addressed in the Next Steps section.

<img width="700" height="556" alt="image" src="https://github.com/user-attachments/assets/9ac84812-aa31-4028-842b-d6fe9401de57" />



# Statistical Approach
A multivariable regression model was used to estimate the association between preventive care access and hypertension prevalence.

An interaction term between preventive care access and insurance status was included to assess whether the relationship differs across insurance environments.

Models adjust for provider availability, socioeconomic conditions, and behavioral risk factors.


# **Baseline Context Before Accounting for Insurance Status**

Hypertension Prevalence and Preventive Care AccessCounties with lower preventive care access show consistently higher hypertension prevalence.

Unadjusted comparisons show a moderate positive association between limited preventive care and hypertension.

This association narrows slightly when behavioral confounders (obesity, inactivity) are introduced, confirming partial mediation through lifestyle pathways.

Absolute differences across access quintiles are meaningful at the population level.
Preventive care access alone does not fully explain hypertension variation, justifying the interaction analysis with insurance status.

Why this matters: Baseline differences by care access are present but modest when averaged across insurance groups, suggesting that stratifying by insurance status will reveal concentrated risk patterns that aggregate analyses conceal.

Baseline Regional Differences in Hypertension PrevalenceHypertension prevalence differs across U.S. census regions independent of preventive care access.
The South exhibits the highest baseline hypertension prevalence.
The Northeast and West show lower baseline rates.
Regional differences persist after adjusting for behavioral risk factors, indicating structural and healthcare access contributors.
Why this matters: Even before accounting for preventive care timing or insurance status, regional disparities justify geographic stratification in subsequent modeling.
                                                                                                                                                     
## Core Analytical Findings - Preventive Healthcare Access and Hypertension: Main Association

<img width="541" height="506" alt="image" src="https://github.com/user-attachments/assets/b820dc4b-bc71-4bf2-9a3a-b87580a745fc" />


Limited Preventive Care Access Is Associated With Higher Hypertension Odds — But Effect Magnitude Depends on Who Is Uninsured
In unadjusted comparisons, counties with lower preventive care access show higher hypertension prevalence across all regions. However, the magnitude of this association is not consistent across insurance environments. A one percentage point increase in the county-level checkup rate was associated with a 1.158 percentage point decrease in hypertension prevalence (95% CI: −1.170 to −1.146; p < 0.001), holding the uninsured rate and all control variables constant.  
This reflects a compound exposure effect:
Low preventive care access delays diagnosis and interrupts disease management.

High uninsured rates in the same counties remove the financial mechanism that would otherwise enable care-seeking even when access nominally exists.

Absence of both preventive access and insurance coverage is associated with the strongest hypertension prevalence estimates across all regions.
Key Insight: The true risk concentration emerges at the intersection of limited access and high uninsured rates — not from either factor in isolation.


Preventive Care Access Quartile
Avg. Hypertension Prevalence
Absolute Gap vs. Highest Quartile
Lowest Quartile (Most Limited Access)
14.21%
+6.04 percentage points
Highest Quartile (Best Access)
8.17%
Reference

<img width="623" height="123" alt="image" src="https://github.com/user-attachments/assets/904c4109-da34-463a-9b49-16d7a2e21276" />


# Effect Modification by Insurance Status
Insurance Status Significantly Modifies the Relationship Between Preventive Care Access and Hypertension

The interaction term between preventive care access and insurance status was statistically significant.

What this means:
The effect of limited preventive care on hypertension is not uniform across populations. It is stronger disproportionately so in counties with higher uninsured rates.

- Interpreting the interaction coefficient:
The positive interaction coefficient indicates that the negative impact of limited preventive care is amplified among uninsured populations. Insurance coverage does not eliminate the risk from poor access, but it meaningfully buffers it, providing a mechanism for care-seeking even in resource-limited environments.

- Plain-language interpretation:
Limited preventive care increases hypertension risk for everyone, but the increase is substantially larger for uninsured populations.

•	Low-uninsured counties (no_insurance ≤ median): The checkup_rate coefficient was −0.0051 (p = 0.233) — not statistically significant. In counties with adequate insurance coverage, preventive care access alone does not show a significant marginal effect on hypertension, suggesting other factors dominate or that the relationship is non-linear.

•	High-uninsured counties (no_insurance > median): The checkup_rate coefficient was +0.0336 (p < 0.001) — statistically significant and positive. This counterintuitive direction warrants careful interpretation.

Explaining the Counterintuitive Finding in High-Uninsured Counties

A positive checkup coefficient in high-uninsured counties does not mean preventive care increases hypertension risk. Three mechanisms likely explain this pattern:

•	Reverse causality: Counties with higher hypertension burden may be proactively expanding screening programs, creating a spurious positive correlation in cross-sectional data.

•	Confounding: Unmeasured variables specific to high-uninsured environments — such as provider type mix, Federally Qualified Health Center density, or Medicaid expansion timing — may simultaneously drive both higher checkup rates and higher hypertension diagnosis rates.

•	Detection bias: Increased screening in high-risk counties increases diagnosed (measured) prevalence without necessarily reflecting increased true prevalence, inflating the observed positive coefficient.


## Effect size summary:
High uninsured rate + limited preventive access: Strongest hypertension association.

Low uninsured rate + limited preventive access: Moderate association

High uninsured rate + adequate preventive access: Moderate association

Low uninsured rate + adequate preventive access: Weakest association (reference group)

Key Insight: Insurance status functions as a structural amplifier. Improving preventive care access without addressing insurance gaps will yield diminished returns in the highest-risk counties.

# Structural and Behavioral Risk Drivers
Socioeconomic Disadvantage and Behavioral Environment Independently Amplify Hypertension Risk
Beyond the primary exposure and effect modifier, additional structural variables contributed meaningfully to the model:

Obesity and physical inactivity — Both are independently associated with higher hypertension prevalence across all county types. These behavioral exposures partially mediate the relationship between socioeconomic disadvantage and hypertension.

Primary care physician availability — Lower provider density is associated with reduced preventive care utilization, creating a downstream pathway to higher hypertension rates. This variable partially confounds and partially mediates the primary exposure.

Socioeconomic conditions — Counties with higher poverty proxies and lower educational attainment show elevated hypertension prevalence, even after adjusting for behavioral factors, suggesting structural pathways operating independently of individual health behaviors.

Smoking — Independently associated with cardiovascular risk, and clustered geographically in high-uninsured, low-access counties, contributing to confounding.

Key Insight: Hypertension disparities are driven by a convergence of structural exposures — not individual behavior alone. This has direct implications for intervention design.
Geographic Context

# Southern Counties Exhibit the Strongest Convergence of Risk Factors
After adjusting for insurance status and behavioral confounders:
- The South consistently shows the highest hypertension prevalence, the lowest preventive care access scores, and the highest uninsured rates in the dataset.
  
- The Midwest shows a similar but less extreme pattern.
  
- The West and Northeast show relatively lower risk convergence.
  
## Regional healthcare context:

The South and Midwest pattern likely reflects compounding structural conditions: rural hospital closures, maternity and primary care deserts, and lower Medicaid expansion uptake in some states have reduced both preventive care infrastructure and insurance coverage simultaneously — creating precisely the high-risk environment identified by the interaction term.

These findings suggest that the geographic healthcare policy environment shapes how preventive care access translates into population-level outcomes, not just individual-level exposure.

Analytical Limitations
•	Ecological design: The county-level structure introduces ecological fallacy risk — county-level associations may not accurately reflect individual-level effects. Replication with BRFSS or NHANES individual-level data is the recommended next step.

•	Multicollinearity: Elevated VIF for checkup_rate (6.26) and obesity (9.44) indicates these variables share variance with other predictors, potentially inflating standard errors for their individual estimates.

•	Cross-sectional limitation: The analysis cannot establish temporal precedence. The counterintuitive positive checkup coefficient in high-uninsured counties likely reflects reverse causality rather than a causal effect of preventive care on hypertension.

•	Missing interaction term in primary model: The main regression does not include an explicit checkup_rate × no_insurance interaction term. The effect modification analysis relies on stratification rather than a formal interaction test.

•	Unmeasured confounders: Provider type mix, FQHC density, Medicaid expansion status, and demographic factors (age, race/ethnicity, sex) are not fully controlled, limiting causal inference.


# Policy and Practice Recommendations
Healthcare systems and public health programs should:

- Prioritize Preventive Care Expansion in High-Uninsured Counties
Target counties where limited access and high uninsured rates converge — particularly in the South and Midwest. Community-based screening programs and mobile health clinics can reduce diagnostic delay even where provider infrastructure is limited.

- Develop Insurance-Aware Intervention Strategies
General access improvements will have a muted impact in high-uninsured environments. Programs must pair expanded preventive services with subsidized visit pathways, free screening initiatives, and Medicaid enrollment support to realize full risk-reduction potential.

- Address Behavioral Risk Factors at the Population Level
Obesity, physical inactivity, and smoking are independently associated with higher hypertension rates and are concentrated in the same counties facing structural access barriers. Integrated behavioral interventions — co-located with preventive care — can address multiple upstream risk factors simultaneously.

- Strengthen Primary Care Infrastructure in Underserved Regions
Increase primary care provider density in counties with low physician-to-population ratios. Financial incentives for primary care practice in high-need regions (loan forgiveness, enhanced Medicaid reimbursement) can address the structural supply gap driving reduced preventive utilization.

- Improve Data Completeness and Granularity
Enhance county-level data collection on insurance status, preventive care utilization rates, and hypertension diagnosis timing. Missing or proxy-only socioeconomic data likely underestimates risk in the most disadvantaged counties.

These findings could directly inform:
Public health outreach and screening program design
Medicaid policy analysts evaluating expansion impact
Hospital and health system community benefit strategies
State and federal chronic disease prevention funding allocation

# Next Steps
- Move to Individual-Level Analysis — The current dataset is ecological (county-level). The next analytic step is replication using BRFSS or NHANES for individual-level modeling, which will eliminate ecological fallacy concerns and enable more precise odds ratio estimation.

- Add Demographic Controls — Introduce age, sex, and race/ethnicity as additional effect
modifiers and confounders. Racial disparities in hypertension prevalence are well-documented and likely interact with both preventive access and insurance status.

- Apply Causal Inference Methods — Propensity score matching, instrumental variable analysis, or difference-in-differences designs using Medicaid expansion as a natural experiment would strengthen causal claims beyond the current associational framework.
  
- Conduct Policy Simulation — Estimate the projected reduction in hypertension prevalence if preventive care access improves by a defined threshold (e.g., 10th to 50th percentile) under varying insurance coverage scenarios. This translates statistical findings into actionable risk reduction estimates for policymakers.
  
- Expand Downstream Outcomes — Incorporate cardiovascular event rates, hospitalization for hypertensive crisis, and all-cause mortality as downstream outcomes to assess the full public health cost of the identified access and insurance gaps.
