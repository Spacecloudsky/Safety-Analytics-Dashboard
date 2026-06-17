# Workplace Safety Analytics Dashboard (2023–2025)

> **78% of incidents are preventable.** Across 1,200 recorded workplace incidents and $24M in total incident cost, this analysis shows that the majority of safety failures are rooted in human behaviour and process gaps — not equipment or environment. The data points to where intervention would have the highest financial and human impact.

![Safety Analytics Dashboard](images/safety-page1.png)

## Business Problem

A multi-facility operation needed visibility into incident patterns, root causes, and corrective action status across departments, shifts, and activity types — to prioritize safety investment and reduce the $19M cost of preventable incidents.

## Pipeline

**Raw CSV → Python metric engineering → Power BI dashboard**

This project uses a two-step pipeline. The Python notebook handles calculations that are complex or non-native in Power BI — industry-standard safety rates and engineered columns — then exports the enriched dataset for full visual analysis in Power BI.

**Layer 1 — Python (`HSE_Incident_Analysis_Cleaned.ipynb`)**
- Calculates TRIR (Total Recordable Incident Rate) and LTIR (Lost Time Injury Rate) using industry-standard OSHA methodology (200,000-hour baseline)
- Engineers key columns: `is_preventable_cost`, `is_lti`, `prevention_score` (composite of JSA completion, toolbox talk, and PPE compliance)
- Builds root cause, facility/department, activity, and cost summary tables
- Exports enriched dataset (`hse_incident_processed.csv`) for Power BI

**Layer 2 — Power BI (`safety_analytics_report.pbix`)**
Single-page executive dashboard covering total incident cost, root cause analysis by year (2023–2025), corrective action status breakdown, cost and incident volume trends over time, and a full incident-type cost matrix across all activity categories.

## Key Insights

- **Poor Housekeeping is the #1 root cause** across all facilities and departments — a behavioural and process failure, not an equipment one. The top two root causes (Poor Housekeeping and Communication Breakdown) are both human factors.
- **Lost Time Injuries account for 48.5% of total incident cost** ($11.8M of $24M), driven heavily by Vehicle Operations activity.
- **Vehicle Operations is the single most costly activity** at $3.37M — nearly double several other categories.
- **67 corrective actions are overdue**, representing unresolved risk that could directly drive re-incident rates.
- **78% of all incidents are classified as preventable** — meaning the vast majority of this $24M cost is recoverable through targeted behavioural and process interventions.

## Recommendations

- Launch targeted housekeeping audits and 5S programs site-wide to address the #1 root cause systematically.
- Implement a dedicated Vehicle Operations safety review — this single activity carries the highest total incident cost across all incident types.
- Prioritize closure of the 67 overdue corrective actions to reduce re-incident risk immediately.
- Focus LTI prevention programs on Chemical Handling and Manual Handling, both exceeding $1.3M each.

## Tools

Python (pandas, NumPy, Plotly, Matplotlib) · Power BI · DAX

## Repo Structure

```
safety-analytics-dashboard/
│
├── data/
│   ├── hse_incident_analysis.csv         ← raw source data
│   └── hse_incident_processed.csv        ← Python-engineered output for Power BI
│
├── notebooks/
│   └── HSE_Incident_Analysis_Cleaned.ipynb
│
├── dashboard/
│   └── safety_analytics_report.pbix
│
├── images/
│   └── safety-page1.png
│
└── README.md
```

---
*Part of my BI portfolio: [spacecloudsky.netlify.app](https://spacecloudsky.netlify.app)*
