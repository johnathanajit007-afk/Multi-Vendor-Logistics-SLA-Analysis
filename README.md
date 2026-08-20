# Multi-Vendor Logistics SLA & Revenue Leakage Analysis

## Executive Summary
This project analyzes **1,000 shipment records** across three major logistics partners (**BlueDart, Delhivery, EcomExpress**) to measure Service Level Agreement (SLA) compliance and quantify financial exposure caused by delayed deliveries. Using custom business-day logic, zone-based target mapping, and automated penalty modeling, this analysis identifies operational bottlenecks and revenue leakage.

---

## Key Metrics & Findings

* **Overall Breach Rate:** **28.40%** of total shipments failed to meet targeted SLA delivery timelines.
* **Total Penalty Liability:** Generated **₹89,448.85** in total financial claims across all breach instances.
* **Best Delivery Compliance:** **Delhivery** recorded the highest on-time delivery rate at **69.53%**.
* **Highest Financial Exposure:** **EcomExpress** registered the highest SLA breach rate at **30.45%**, driving **₹32,756.55** in penalty liabilities.

---

## Data Pipeline & Modeling Logic

### Data Processing & Transformation
1. **Business Days Calculation:** Excluded weekends to determine actual transit time:
   $$\text{Actual Business Days} = \text{NETWORKDAYS}(\text{Dispatch\_Date}, \text{Delivery\_Date})$$
2. **Zone-Based SLA Targets:** Mapped tier-specific delivery benchmarks:
   * **Metro:** 2 Days
   * **Tier 2:** 4 Days
   * **Tier 3:** 5 Days
3. **Automated Breach Flagging:** Marked status dynamically as `ON TIME`, `SLA BREACH`, or `Pending`.
4. **Penalty Quantification:** Evaluated penalty claims based on breach status and order value.

---

## Executive Dashboard Features

* **Dynamic Performance Breakdown:** Evaluates vendor breach distribution percentages (`% of row`).
* **Penalty Claim Summaries:** Tracks aggregated revenue leakage per vendor in currency format (`₹`).
* **Interactive Regional Filtering:** Features an active `Destination_Zone` Slicer allowing real-time cross-filtering across all metric summary tables.

---

## Repository Structure

```text
Multi-Vendor Logistics SLA & Revenue Leakage Analysis/
│
├── 01_Raw_Data.ipynb            # Jupyter Notebook for raw data extraction/generation
├── Raw_Logistics_Data.csv       # Ingested raw logistics dataset
├── 02_Excel_Model.xlsx          # Advanced Excel financial model & interactive dashboard
└── README.md                    # Project documentation
