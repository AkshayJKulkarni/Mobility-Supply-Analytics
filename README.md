# Mobility Supply Analytics

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AkshayJKulkarni/Mobility-Supply-Analytics/blob/main/Captain_Acquisition_and_Supply.ipynb)

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
*Permit requirements vary by vehicle type.*

Stage-level volume loss and conversion are quantified to identify the largest actionable bottlenecks.

### 3. Bottleneck & Segment Analysis

The onboarding funnel is segmented across relevant dimensions including:

- City
- Vehicle type
- Acquisition channel
- Device tier
- Document type
- Verification failure reason

The analysis focuses on identifying leaks that are large, explainable, and operationally actionable.

### 4. Campaign Evaluation

`CAMP_WA_002` is evaluated using:

- Delivery and engagement metrics
- Approval conversion
- Appropriate comparison groups
- Onboarding stage
- Campaign timing
- Observable segment composition

The analysis distinguishes association from causal impact and identifies when randomized experimentation is required before scaling spend.

### 5. Airport Supply-Demand Analysis

Airport operations are analyzed to:

- Identify periods of demand-supply imbalance
- Quantify unfulfilled demand
- Identify high-impact airport zones and time windows
- Analyze destination-level cancellation and return-fare patterns
- Translate findings into targeted supply interventions

---

## How to Run

### Google Colab (Recommended)

The notebook is designed to run end-to-end in Google Colab.

1. Click the **Open in Colab** button at the top of this README.
2. The notebook loads all seven CSV datasets directly from this GitHub repository.
3. Run the notebook cells sequentially from top to bottom.
4. No manual dataset upload or local file-path configuration is required.
5. The notebook performs the complete analysis and generates the tables, findings, and recommendations.

### Local Jupyter Notebook

1. Clone the repository:
   ```bash
   git clone [https://github.com/AkshayJKulkarni/Mobility-Supply-Analytics.git](https://github.com/AkshayJKulkarni/Mobility-Supply-Analytics.git)
   cd Mobility-Supply-Analytics
   ```
 2. Install the dependencies : pip install pandas numpy matplotlib jupyter
 3. Start the jupyter notebook : jupyter notebook
 4. Open Captain_Acquisition_and_Supply.ipynb.
Run all notebook cells sequentially from top to bottom.

### The notebook loads the datasets directly from the GitHub repository, so no manual dataset upload or file-path configuration is required.

### Reproducibility
- The notebook is designed to run end-to-end from the raw CSV datasets without relying on precomputed analytical outputs.

- The analysis can be reproduced using either Google Colab or a local Jupyter Notebook environment.

- Tools: Python, Pandas, NumPy, Matplotlib, Jupyter Notebook, Google Colab, Git and GitHub.

### Project Structure
```text
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
```

### Scope

- Driver acquisition and onboarding conversion
- Document verification friction
- Campaign effectiveness
- Airport supply-demand imbalance
- Post-trip destination and return-fare behavior
- Data-driven operational recommendations
