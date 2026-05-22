# recall-intelligence-system
### A Pattern Analysis of Health Canada Recall Data — January 2023 to April 2026

---

I have a biochemistry degree from the University of Waterloo and I worked in food and pharmaceutical labs at Sanofi and Agropur. I know what quality systems look like from the inside. And I kept noticing that Health Canada publishes all their recall data publicly and nobody seems to be using it systematically to find the patterns that could prevent the next recall.

So I built a tool that does exactly that.

---

## What this project is

A Python-based recall classification and early warning system. It takes 847 modelled Health Canada recall records, classifies each one by root cause and severity, runs statistical analysis to identify which failure modes concentrate in which product categories, and outputs an interactive dashboard a quality team could actually use.

The live app is deployed on Streamlit Cloud. Anyone can explore the data by category, root cause, date range, and recall class.

---

## Live app

[Launch the Recall Intelligence System](your-streamlit-link-here)

---

## Key findings

| Finding | Detail |
|---------|--------|
| Total recalls analysed | 847 across 12 product categories |
| Class I recalls (serious health risk) | 307 (36.2% of total) |
| Top root cause | Microbiological contamination (149 recalls) |
| Highest risk category | Meat and Poultry |
| Chi-square test result | p < 0.05 — category and root cause are NOT independent |
| Most preventable root cause | Undeclared allergen — 100% preventable with robust allergen management |
| Estimated industry cost (midpoint) | $6 billion across 847 recalls |

---

## What the chi-square test actually tells us

The chi-square test of independence checks whether product category and root cause are statistically related or random. The result (p less than 0.05, chi-square = 113.56) means the relationship is real. Knowing what category a product belongs to tells you something useful about the most likely failure mode.

This is the finding that turns a descriptive analysis into an actionable one. Quality teams can design category-specific prevention programs rather than applying generic controls everywhere.

---

## Files in this repo

| File | What it is |
|------|-----------|
| app.py | The Streamlit application — 5-tab interactive dashboard |
| recall-dataset.csv | 847 classified recall records across 12 categories |
| pareto-analysis.csv | Root cause Pareto table with cumulative percentages |
| category-risk-scores.csv | Composite risk scores for all 12 product categories |
| monthly-trend.csv | Monthly recall volume with control chart limits |
| early-warning-framework.csv | Category-specific early warning indicators |
| business-impact.csv | Cost range estimates by recall class |
| chi-square-results.json | Full statistical test results and interpretation |
| analysis-summary.csv | All headline numbers in one place |
| analysis.py | The Python analysis pipeline that generates all outputs |
| generate_data.py | The data generation script with classification taxonomy |
| requirements.txt | Python dependencies for Streamlit Cloud deployment |

---

## How to run locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

---

## How to deploy on Streamlit Cloud

Go to share.streamlit.io. Sign in with your GitHub account. Click New app. Select this repository. Set the main file path to app.py. Click Deploy. The app will be live in about 2 minutes.

---

## Technical skills demonstrated

Python programming with pandas, plotly, scipy, and streamlit. Data pipeline design and automated classification logic. Statistical analysis including chi-square test of independence and control chart methodology. Risk scoring framework design. Interactive web application development and deployment. Regulatory affairs knowledge — Health Canada recall classification, CFIA violation taxonomy, GMP connection. Process improvement thinking — root cause taxonomy, Pareto analysis, early warning framework. Business analysis — cost impact modelling, cross-functional recommendations. Technical communication — app UI design, regulatory briefing style writing.

---

## About this project

This is part of The Case Files — a portfolio series built while job searching in Canada after graduating from the University of Waterloo.

Prepared by Simran Saran. Background in biochemistry, bioinformatics, and food and pharmaceutical lab experience. Targeting roles in quality engineering, process improvement, regulatory affairs, and business analysis across Canada.

All recall descriptions, companies, and product names are fictional and created for portfolio purposes. The analytical methodology, statistical tests, and early warning framework reflect real quality management practice.
