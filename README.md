# Mobility Supply Analytics

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/AkshayJKulkarni/Mobility-Supply-Analytics/blob/main/Captain_Acquisition_%26_Supply.ipynb)

End-to-end analytics of driver acquisition, onboarding conversion, campaign effectiveness, and airport supply-demand dynamics using Python, statistical analysis, and data-driven experimentation.

## Overview

Mobility platforms need to balance two connected challenges:

1. Acquiring and onboarding enough drivers while minimizing friction in the approval process.
2. Ensuring sufficient driver supply during periods and locations of high rider demand.

This project analyzes synthetic mobility-platform data to identify the largest onboarding bottlenecks, evaluate the effectiveness of a driver engagement campaign, characterize airport supply-demand gaps, and translate the findings into operational recommendations.

The analysis focuses on **business impact rather than model complexity** — defining the right cohorts and denominators, validating the data, quantifying losses, distinguishing association from causation, and converting insights into measurable actions.

---

## Business Questions

### Driver Acquisition & Onboarding

- Where are the largest losses between signup and approval?
- Which onboarding stage represents the most actionable bottleneck?
- How do onboarding leaks vary across cities, vehicle types, acquisition channels, and device tiers?
- Which document verification issues contribute most to the drop-off?
- Does the `CAMP_WA_002` campaign generate meaningful incremental approvals?
- Should campaign spending be scaled, or should the intervention be tested further?

### Mobility Supply & Airport Operations

- When and where does airport demand exceed available supply?
- Which airport zones and time windows contribute most to unfulfilled demand?
- What post-trip behavior may indicate supply retention or repositioning challenges?
- Is broad driver acquisition the right first intervention, or should supply be targeted more precisely?

---

## Dataset

The project uses seven synthetic datasets representing the driver onboarding and mobility supply lifecycle:

| Dataset | Description |
|---|---|
| `captains.csv` | Driver signup, city, vehicle, acquisition channel, device and demographic attributes |
| `doc_events.csv` | Document uploads, verification outcomes, attempts and failure reasons |
| `approvals.csv` | Final approval decisions and onboarding stage reached |
| `activation.csv` | First-order activation and post-approval activity |
| `nudges.csv` | Driver campaign delivery, engagement and click activity |
| `airport_hourly.csv` | Hourly airport demand, fulfillment, online supply, ETA and surge |
| `airport_trips.csv` | Airport trips, destinations, cancellations, fares and return-fare outcomes |

All timestamps are treated consistently within the exercise's reporting window. The datasets are synthetic and are analyzed as provided.

---

## Methodology

### 1. Data Validation

Before analysis, the raw datasets are checked for:

- Schema and data types
- Missing values
- Duplicate identifiers
- Timestamp validity
- Logical consistency between related datasets
- Cohort maturity and observation windows

The analysis uses a mature signup cohort for approval-funnel comparisons so that recent signups are not unfairly treated as failures simply because they have had less time to complete onboarding.

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
