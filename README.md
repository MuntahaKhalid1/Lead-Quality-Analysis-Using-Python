# Lead-Quality-Analysis-Using-Python
End to end lead quality analysis on 3,000 leads answering three business questions around quality trends, segment performance, and Cost Per Lead optimization. Built entirely in Python with statistical testing, 14 visualizations, and an automated PDF report.

<p align="center">
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>
  <img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white"/>
  <img src="https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white"/>
  <img src="https://img.shields.io/badge/Google%20Colab-F9AB00?style=for-the-badge&logo=googlecolab&logoColor=white"/>
</p>

## Approach
I chose Python with pandas, scipy, and matplotlib over Excel because it allowed me to run statistical significance tests on the trend, apply a minimum sample size filter across all segments, and compile every chart and insight into one structured PDF automatically.

## Data Note
The dataset references an 8% baseline quality rate which includes 2,140 Unknown leads in the denominator. This analysis excludes Unknowns and measures quality only against the 881 leads classified as Good or Bad, producing a 44.6% rate. Both interpretations are noted where relevant.

## Methods Used
- Data cleaning and feature engineering using pandas
- Lead classification into Good, Bad, and Unknown categories based on business rules
- Weekly trend analysis using linear regression (scipy.stats.linregress)
- Statistical significance testing using chi-square test (chi2_contingency)
- Minimum sample size filtering based on Central Limit Theorem (n≥30)
- Segment analysis across 12 dimensions including widget design, campaign type, traffic partner, keywords, debt level, and geographic data
- Revenue scenario modeling for Cost Per Lead optimization

## Questions Answered

### Q1 — Are lead quality trends improving or declining over time?
The trend slopes downward at 0.388% per week but the p-value of 0.221 means this decline is not statistically significant. The chi-square test comparing the first and second half of the period returns p=0.073, narrowly missing the 0.05 threshold. The more pressing issue is week-to-week volatility, with quality swinging between 25% and 65%, which points to inconsistency in traffic source or creative rather than a confirmed structural decline.

### Q2 — What drives lead quality?
Almost every segment across widget design, ad placement, campaign type, traffic partner, state, debt level, address score, and referral domain beats both the 8% baseline and the 9.6% target. The only exception is at the keyword level where "Student loan default" and "Loan default help" fall below baseline because searchers using those terms do not qualify for debt reduction programs. This is the most actionable finding in the entire dataset.

### Q3 — Can we reach 9.6% quality for a $33 CPL?
The optimized scenario filtering to the best performing widgets and campaigns produces 43.9%, nearly identical to the current 44.6%, confirming that segment optimization alone does not move the needle since quality is already strong across the board. The direct path to unlocking the $33 Cost Per Lead is cutting the two underperforming loan default keywords, which are the only confirmed drag on overall quality. At 1,000 leads per month this improvement unlocks $3,000 in additional monthly revenue and $36,000 annually.

## Recommendations
- Cut **"Student loan default"** and **"Loan default help"** from keyword targeting immediately
- Shift budget toward the branded creditsolutions campaign over the generic Debt Settlement form
- Investigate the address score anomaly where score 2 outperforms score 4 before using it as a quality filter
- Monitor weekly quality variance as the primary operational metric since trend direction is less concerning than inconsistency
