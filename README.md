# patient-segmentation-mimic-iv-
Patient segmentation and retention analytics project leveraging real-world clinical data to support care management and healthcare decision-making.
# Project Overview
This project demonstrates an end-to-end **patient segmentation and retention analysis** using real-world clinical data from the **MIMIC-IV Clinical Database (Demo 2.2)**.
The objective is to identify **distinct patient cohorts** based on healthcare utilization, clinical complexity, and acuity signals, enabling healthcare organizations to:

- Improve patient retention and engagement

- Identify high-risk or high-cost patient segments

- Optimize care management and resource allocation

The project follows a **SQL-first feature engineering approach**, with Python used for modeling, clustering, and interpretation.
Dataset
Core Tables Used

Table	Purpose
patients.csv	Demographics (age proxy, gender)
admissions.csv	Visit history & engagement metrics
diagnoses_icd.csv	Clinical complexity & chronic conditions
icustays.csv	Severity & care intensity signals

Problem Statement
Healthcare organizations often struggle to:

Distinguish low-risk vs high-utilization patients

Identify chronic and high-acuity populations early

Design targeted retention and care management programs

This project addresses these challenges by building patient-level analytical features and applying unsupervised clustering to uncover meaningful patient segments.

Tech Stack
Python: pandas, numpy, scikit-learn, matplotlib
SQL: Feature design & validation logic
Environment: Jupyter Notebook
ML Technique: K-Means clustering
Domain: Healthcare / Clinical Analytics
Feature Engineering (SQL-First Design)

All features were conceptually designed and validated in SQL before implementation in Python, mirroring real-world EHR analytics workflows.

Patient Engagement & Utilization
Number of admissions
Average length of stay
Days since last admission
Clinical Complexity
Number of unique ICD diagnoses
Binary chronic condition indicator
Severity & Acuity
ICU visit count
Total ICU days
Demographics
Gender
Age bucket (derived from anchor year)

Example SQL pattern:

SELECT
    subject_id,
    COUNT(DISTINCT hadm_id) AS num_admissions,
    AVG(DATE_DIFF(dischtime, admittime, DAY)) AS avg_length_of_stay
FROM admissions
GROUP BY subject_id;
Data Preparation & Quality Handling
Normalized patient identifiers across tables

Handled one-to-many joins safely to prevent double counting

Filled missing numeric features with 0

Assigned "Unknown" category for missing demographic values

Scaled numeric features using StandardScaler

Modeling Approach
Unsupervised Learning: K-Means clustering

Feature Scaling: Standardization prior to clustering

Cluster Selection: Chosen based on interpretability and healthcare relevance

Final Output: Patient-level cluster assignment

Results & Insights
The clustering process identified distinct patient personas, such as:

Low-utilization, healthy patients

Chronic but stable patients

High-frequency, high-cost utilizers

Acute and ICU-intensive patients

These segments can support:

Targeted retention strategies

Preventive care outreach

Resource and staffing optimization

Value-based care initiatives

Business Value
This analysis can be directly applied to:

Hospital care management teams

Population health analytics

Healthcare SaaS platforms

Life sciences and regulatory technology products

​

