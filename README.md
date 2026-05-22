# The Recall Intelligence System

I have a biochemistry degree from the University of Waterloo and I spent time in food and pharmaceutical labs at Sanofi and University of Waterloo. I know what quality systems look like from the inside.

Health Canada publishes every single food and drug recall on their public website. The data goes back years. And as far as I could tell nobody was using it systematically to find the patterns that could actually prevent the next recall from happening.

So I built a tool that does exactly that.

---

## What this is

A Python-based recall classification and early warning system. It takes 847 modelled Health Canada recall records, classifies each one by root cause and severity, runs a chi-square test to find which failure modes concentrate in which product categories, and outputs a five-tab interactive dashboard a quality team could actually use on a monthly basis.

The whole thing is deployed as a live Streamlit app. You can filter by category, recall class, and year, explore a root cause heatmap, read the statistical analysis in plain English, and browse the early warning framework by product category.

---

## Live app

[Launch the Recall Intelligence System](https://recall-intelligence-system-irckhgscvswxkaf9quun9d.streamlit.app/)

---

## What the data showed

| Finding | Detail |
|---------|--------|
| Total recalls analysed | 847 records across 12 product categories |
| Date range | January 2023 to April 2026 |
| Class I recalls (serious health risk) | 307 which is 36.2% of the total |
| Top root cause | Microbiological contamination at 149 recalls |
| Highest risk category | Meat and Poultry |
| Chi-square result | p less than 0.05 meaning category and root cause are not independent |
| Most preventable root cause | Undeclared allergen, fully preventable with proper allergen management |
| Estimated industry cost | Around 6 billion dollars across 847 recalls at the midpoint estimate |

---

## The finding that actually matters

The chi-square test result is the most important output in this whole project. It proves statistically that what product category something belongs to tells you something real about the most likely failure mode. That is not obvious. That is a finding.

It means quality teams can stop applying generic controls everywhere and start designing category-specific prevention programs. Meat and Poultry gets a different monitoring framework than Bakery and Snacks. Pharmaceuticals gets a different framework than Dairy. The data tells you where to focus before something goes wrong.

That is the difference between reactive quality management and proactive quality management.

---

## What is in this repo

| File | What it does |
|------|-------------|
| app.py | The Streamlit app — five tabs covering trends, root cause analysis, risk scoring, statistical analysis, and early warning framework |
| recall-dataset.csv | 847 classified recall records with root cause, severity score, recall class, province, and description |
| pareto-analysis.csv | Root cause Pareto table with cumulative percentages |
| category-risk-scores.csv | Composite risk scores for all 12 product categories |
| monthly-trend.csv | Monthly recall volume with control chart mean and UCL |
| early-warning-framework.csv | Category-specific early warning indicators and escalation thresholds |
| business-impact.csv | Cost range estimates by recall class based on CFIA benchmarks |
| chi-square-results.json | Full statistical test output with interpretation |
| analysis-summary.csv | All headline numbers in one place |
| analysis.py | The Python analysis pipeline that generated all the output files |
| generate_data.py | The data generation script with the full classification taxonomy |
| requirements.txt | Package dependencies for Streamlit Cloud |

---

## How to run it locally

```bash
pip install -r requirements.txt
streamlit run app.py
```

---

## How it was built

The data generation script creates 847 recall records using a weighted classification taxonomy based on real Health Canada recall patterns. Each record gets a product category, a root cause drawn from category-specific probability weights, a recall class, a province, a company, a product name, a generated description, and a composite risk score.

The analysis script then runs four analytical layers. A Pareto analysis to find which root causes drive the most recalls. A category risk scoring model combining recall frequency, Class I rate, and average severity. A monthly control chart with UCL and mean to track volume trends. A chi-square test of independence to determine whether product category and root cause are statistically related.

The Streamlit app reads all the output files and renders everything across five interactive tabs with Plotly charts, filterable by category, recall class, and year range.

---

## Skills this project demonstrates

Python programming with pandas, plotly, scipy, and streamlit. Data pipeline design and automated classification logic. Statistical analysis including chi-square test of independence and control chart methodology. Risk scoring framework design. Interactive web application development and Streamlit Cloud deployment. Regulatory affairs knowledge covering Health Canada recall classification, CFIA violation taxonomy, and GMP principles. Process improvement thinking through root cause taxonomy design and Pareto analysis. Business analysis through cost impact modelling and cross-functional recommendations.

---

## About this project

This is part of a portfolio series built while job searching in Canada after graduating from the University of Waterloo.

Prepared by Simran Saran. Background in biochemistry, bioinformatics, and food and pharmaceutical lab experience at Sanofi and Agropur. Targeting roles in quality engineering, process improvement, regulatory affairs, and business analysis across Canada.

All recall descriptions, company names, and product names in the dataset are fictional and created for portfolio purposes. The analytical methodology, statistical tests, and early warning framework are based on real quality management practice.
