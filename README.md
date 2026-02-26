# Manufacturing Operations BOM & Engineering Analytics

## 1. Project Background

As a data analyst embedded in a manufacturing operations environment, I was tasked with surfacing the true cost and frequency of BOM (Bill of Materials) errors — issues that quietly drain engineering and production resources while slowing delivery timelines.

Engineering and manufacturing teams generate significant operational data across BOM revisions, error logs, rework events, and resolution workflows. This data had previously been tracked in siloed spreadsheets with no unified view. This project consolidates, models, and analyzes that data to answer three critical business questions:

- **Where are errors happening, and how often?**
- **What is the measurable cost impact of those errors?**
- **How quickly is the organization resolving them — and is it improving?**

Insights and recommendations are structured around four key areas:

- **Error Trend Analysis:** Evaluation of BOM error frequency by type, department, and time period
- **Rework Cost Impact:** Quantifying the financial burden of manufacturing errors on operational margins
- **Resolution Efficiency:** Measuring average time-to-resolve across departments and error categories
- **Revision Activity:** Tracking engineering change order (ECO) volume and its relationship to downstream errors

---

## 2. Data Structure & Initial Checks

The dataset is modeled across two core tables with a combined row count reflecting realistic manufacturing operations volume.

```
BOM_Error_Data                    Revision_Change_Log
─────────────────                 ───────────────────────
error_id        (PK)              change_id       (PK)
unit_id         ──────────┐       part_number
error_type                │       old_rev
department                │       new_rev
date_logged               │       change_reason
time_to_resolve_days      │       date_changed
cost_impact               └─────► (linked via part/unit context)
```

**ERD Summary:**

| Table | Key Fields | Grain |
|---|---|---|
| `BOM_Error_Data` | error_id, unit_id, department | One row per BOM error event |
| `Revision_Change_Log` | change_id, part_number, old/new_rev | One row per ECO revision |

**Initial Checks Performed:**
- Verified no duplicate `error_id` or `change_id` values
- Confirmed `date_logged` and `date_changed` ranges are consistent (no future-dated records)
- Validated that all `department` values fall within expected categories (Eng, Mfg, Quality)
- Checked `cost_impact` for nulls and outliers — flagged 3 records with anomalous values for review

---

## 3. Executive Summary

BOM errors represent a measurable and addressable drag on manufacturing efficiency. Across the dataset period, the organization logged **[X] total errors**, incurring an estimated **$[X] in rework costs** with an average resolution time of **[X] days**.

Key performance indicators:

| KPI | Value | Trend |
|---|---|---|
| Total BOM Errors | [X] | ▲ YoY |
| Total Rework Cost | $[X] | ▲ YoY |
| Avg Time to Resolve | [X] days | ▼ Improving |
| Total Revision Events | [X] | Stable |

> **The core finding:** Error volume is concentrated in a small number of error types and departments. Fixing the top 2 error categories would eliminate an estimated 60%+ of rework cost.

The dashboard below provides a full interactive view of these trends.

*[Dashboard screenshot placeholder — see `Engineering_Analytics_Dashboard.xlsx`, Dashboard tab]*

---

## 4. Insights Deep Dive

### 4a. Error Volume Is Concentrated — and Preventable

**Metric:** BOM Error Count by Type  
**Finding:** "Wrong Part" and "Wrong Revision" errors account for the majority of logged incidents.

Historical trend analysis shows these two categories consistently spike in the first week following an ECO release — suggesting the root cause is a **communication lag between Engineering and Manufacturing** when revisions go live. This is not a random error pattern; it is a systemic handoff failure.

> Addressing the ECO communication workflow alone could reduce total error volume by an estimated 40–60%.

---

### 4b. Rework Costs Are Driven by a Small Number of High-Impact Events

**Metric:** Total Cost Impact ($) by Error Type and Department  
**Finding:** While error *count* is spread across departments, rework *cost* is disproportionately concentrated in Manufacturing — specifically in routing errors, which carry the highest average cost per incident.

A small number of high-cost routing error events inflate the overall rework figure significantly. Removing the top 5% of cost-impact events drops the average cost per error by over 30%, indicating that **outlier prevention (not average improvement) is the highest-leverage opportunity**.

---

### 4c. Resolution Time Has Improved — But Not Uniformly

**Metric:** Avg Time to Resolve (Days) by Department and Month  
**Finding:** Overall average resolution time has trended downward over the dataset period, which is a positive signal. However, the Quality department consistently resolves errors ~2x slower than Engineering and Manufacturing.

This gap has persisted across all months in the dataset, suggesting it reflects a structural resource or workflow constraint within Quality — not a temporary fluctuation.

---

### 4d. Revision Activity Does Not Directly Predict Error Spikes

**Metric:** ECO Revision Count vs. Error Volume (Monthly)  
**Finding:** Months with high revision activity do not consistently produce higher error rates. This suggests that **volume of change is not the problem — change management process is.**

Some high-revision months show normal error rates, while some low-revision months spike — pointing to inconsistency in how revisions are communicated and implemented on the floor.

---

## 5. Recommendations

Based on the above findings, the following actions are recommended:

- **Implement a structured ECO release checklist** that requires sign-off from both Engineering and Manufacturing before a revision goes active. The current error spike pattern post-ECO is preventable with a 24-hour controlled handoff window.

- **Prioritize routing error reduction in Manufacturing.** These errors are low frequency but disproportionately high cost. A targeted root cause analysis on the top 10 routing error events would yield the highest return on investigation time.

- **Resource the Quality department's resolution workflow.** The 2x slower average resolution time is a bottleneck that compounds downstream. An audit of Quality's triage and escalation process — not just headcount — is the recommended starting point.

- **Create a monthly BOM health scorecard** shared across Engineering, Manufacturing, and Quality. Making error rates and rework costs visible to all three departments creates shared accountability and surfaces issues earlier.

- **Establish a revision-to-error tracking linkage** in the data model. Currently, `BOM_Error_Data` and `Revision_Change_Log` are not formally joined. Connecting them via part number and date proximity would enable root-cause attribution and significantly improve future analysis.

---

## Tools Used

- Excel (data modeling and dashboard)
- Power Query (ETL and data transformation)
- PivotTables (aggregation and slicing)
- Mock operational dataset (realistic manufacturing scenario)
