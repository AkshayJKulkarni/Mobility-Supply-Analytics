# Mobility Supply Analytics

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AkshayJKulkarni/Mobility-Supply-Analytics/blob/main/Captain_Acquisition_%26_Supply.ipynb)

End-to-end analytics of driver acquisition, onboarding conversion, campaign effectiveness, and airport supply-demand dynamics using Python, statistical analysis, and data-driven experimentation.

## Overview

Mobility platforms need to balance two connected challenges:

- Acquiring and onboarding enough drivers while minimizing friction in the approval process.
- Ensuring sufficient driver supply during periods and locations of high rider demand.

This project analyzes synthetic mobility-platform data to identify onboarding bottlenecks, evaluate campaign effectiveness, characterize airport supply-demand gaps, and translate findings into operational recommendations.

The analysis focuses on business impact rather than model complexity — defining appropriate cohorts and denominators, validating the data, quantifying losses, distinguishing association from causation, and converting insights into measurable actions.

## Business Questions

### Driver Acquisition & Onboarding

- Where are the largest losses between signup and approval?
- Which onboarding stage represents the most actionable bottleneck?
- How do onboarding leaks vary across cities, vehicle types, acquisition channels, and device tiers?
- Which document verification issues contribute most to drop-off?
- Does `CAMP_WA_002` show evidence of incremental approvals?
- Should campaign spending be scaled or tested further?

### Mobility Supply & Airport Operations

- When and where does airport demand exceed available supply?
- Which zones and time windows contribute most to unfulfilled demand?
- What post-trip behavior may indicate supply or repositioning challenges?
- Is broad driver acquisition the right first intervention?

## Dataset

The project uses seven synthetic datasets representing the driver onboarding and mobility supply lifecycle.

| Dataset | Description |
|---|---|
| `captains.csv` | Driver signup, city, vehicle, acquisition channel, device and demographic attributes |
| `doc_events.csv` | Document uploads, verification outcomes, attempts and failure reasons |
| `approvals.csv` | Final approval decisions and onboarding stage reached |
| `activation.csv` | First-order activation and post-approval activity |
| `nudges.csv` | Driver campaign delivery, engagement and click activity |
| `airport_hourly.csv` | Hourly airport demand, fulfillment, online supply, ETA and surge |
| `airport_trips.csv` | Airport trips, destinations, cancellations, fares and return-fare outcomes |

The datasets are synthetic and are analyzed as provided.

## Methodology

### 1. Data Validation

Before analysis, the raw datasets are checked for:

- Schema and data types
- Missing values
- Duplicate identifiers
- Timestamp validity
- Logical consistency between related datasets
- Cohort maturity and observation windows

A mature signup cohort is used for approval-funnel comparisons so that recent signups are not unfairly treated as failures simply because they have had less time to complete onboarding.

### 2. Driver Onboarding Funnel

The onboarding journey is reconstructed stage by stage:

```text
Signup
   ↓
Driving Licence
   ↓
Registration Certificate
   ↓
Aadhaar
   ↓
Permit*
   ↓
Fitness
   ↓
Insurance
   ↓
Approved
```
*Permit requirements vary by vehicle type.

Stage-level volume loss and conversion are quantified to identify the largest actionable bottlenecks.

3. Bottleneck & Segment Analysis

The onboarding funnel is segmented across relevant dimensions including:

City
Vehicle type
Acquisition channel
Device tier
Document type
Verification failure reason

The analysis focuses on identifying leaks that are large, explainable, and operationally actionable.

4. Campaign Evaluation

CAMP_WA_002 is evaluated using:

Delivery and engagement metrics
Approval conversion
Appropriate comparison groups
Onboarding stage
Campaign timing
Observable segment composition

The analysis distinguishes association from causal impact and identifies when randomized experimentation is required before scaling spend.

5. Airport Supply-Demand Analysis

Airport operations are analyzed to:

Identify periods of demand-supply imbalance
Quantify unfulfilled demand
Identify high-impact airport zones and time windows
Analyze destination-level cancellation and return-fare patterns
Translate findings into targeted supply interventions
How to Run
Google Colab — Recommended

The notebook is designed to run end-to-end in Google Colab.

Click the Open in Colab button at the top of this README.
The notebook loads all seven CSV datasets directly from this GitHub repository.
Run the notebook cells sequentially from top to bottom.
No manual dataset upload or local file-path configuration is required.
The notebook performs the complete analysis and generates the tables, visualizations, findings, and recommendations.
Local Jupyter Notebook

Clone the repository:

git clone https://github.com/AkshayJKulkarni/Mobility-Supply-Analytics.git
cd Mobility-Supply-Analytics

Install the required dependencies:

pip install pandas numpy matplotlib jupyter

Start Jupyter Notebook:

jupyter notebook

Open:

Captain_Acquisition_&_Supply.ipynb

Run all cells sequentially.

Reproducibility

The notebook is designed to run end-to-end from the raw CSV datasets without relying on precomputed analytical outputs.

For the recommended Colab workflow, the datasets are loaded directly from the GitHub repository. This allows the complete analysis to be reproduced without manually uploading the datasets.

The analysis is implemented using:

Python
Pandas
NumPy
Matplotlib
Jupyter Notebook
Google Colab
Git
GitHub
Project Structure
Mobility-Supply-Analytics/
│
├── README.md
├── Captain_Acquisition_&_Supply.ipynb
│
├── captains.csv
├── doc_events.csv
├── approvals.csv
├── activation.csv
├── nudges.csv
├── airport_hourly.csv
├── airport_trips.csv
│
└── .gitignore
Scope

The analysis covers:

Driver acquisition and onboarding conversion
Document verification friction
Campaign effectiveness
Airport supply-demand imbalance
Post-trip destination and return-fare behavior
Data-driven operational recommendations
Approved

