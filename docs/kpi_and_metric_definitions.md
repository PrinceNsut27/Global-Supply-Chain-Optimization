# KPI & Metric Definitions

This document defines the mathematical formulations, operational definitions, and business interpretations for all supply chain performance indicators used throughout the ThreadIQ Global Supply Chain Optimization project.

---

## 1. Supply Chain Fulfillment Performance Metrics

### 1.1 On-Time Delivery Rate (OTD)
* **Definition:** The percentage of fulfilled shipments that arrive at the customer doorstep on or before the committed scheduled delivery date.
* **Mathematical Formula:**
  $$\text{OTD} = \frac{N_{\text{On-Time}} + N_{\text{Advance}}}{N_{\text{Total Fulfilled}}} \times 100$$
  $$\text{Where: } N_{\text{Total Fulfilled}} = N_{\text{Late}} + N_{\text{On-Time}} + N_{\text{Advance}} + N_{\text{Canceled}}$$
* **Project Observed Value:**
  $$\text{OTD} = \frac{32,196 + 41,592}{180,519} \times 100 = \frac{73,788}{180,519} \times 100 = \mathbf{40.88\%}$$
* **Industry Benchmark:** $90.0\% - 95.0\%$ for competitive international e-commerce.
* **Business Implication:** An OTD rate of ~41% reflects a severe systemic fulfillment crisis across global operations.

---

### 1.2 Late Delivery Rate (LDR)
* **Definition:** The proportion of total fulfilled shipments that officially breached their committed delivery schedule.
* **Mathematical Formula:**
  $$\text{LDR} = \frac{N_{\text{Late Shipments}}}{N_{\text{Total Fulfilled}}} \times 100$$
* **Project Observed Value:**
  $$\text{LDR} = \frac{98,977}{180,519} \times 100 = \mathbf{54.83\%}$$
* **Business Implication:** More than 1 out of every 2 shipments arrives past its promised delivery window, heavily elevating customer churn risk.

---

### 1.3 Delivery Delay Delta ($\Delta_{\text{delay}}$)
* **Definition:** The discrete difference (in days) between the actual recorded shipping duration and the scheduled delivery promise for an individual shipment.
* **Mathematical Formula:**
  $$\Delta_{\text{delay}, i} = \text{Days for shipping (real)}_i - \text{Days for shipment (scheduled)}_i$$
* **Aggregated Average Delay ($\overline{\Delta}_{\text{late}}$):**
  $$\overline{\Delta}_{\text{late}} = \frac{1}{N_{\text{Late}}} \sum_{i \in \text{Late}} \left( \text{Days for shipping (real)}_i - \text{Days for shipment (scheduled)}_i \right)$$
* **Project Observed Value:**
  * For all 98,977 late shipments, the average delay is **+1.62 days** beyond the promised delivery date.

---

## 2. Financial Exposure & Capital Risk Metrics

### 2.1 At-Risk Order Value ($AROV$)
* **Definition:** The aggregated gross transaction value (`Order Item Total`) of all shipments that experienced a late delivery.
* **Mathematical Formula:**
  $$AROV = \sum_{i \in \text{Late Shipments}} \text{Order Item Total}_i$$
* **Project Observed Values:**
  * **Global Total AROV:** **$18,082,555.30** (54.71% of all $33.05M sales).
  * **Top 2 Regions (Western Europe + Central America) AROV:** **$5,752,054.15** (~$5.75M, "nearly $6 million").
  * **Top 10 Regions AROV:** **$13,475,060.56**.
* **Crucial Precision:** $AROV$ is an exposure metric quantifying order value subjected to delivery friction; it does not represent realized cash write-offs or accounting losses.

---

### 2.2 Regional At-Risk Concentration Share ($RCS$)
* **Definition:** The proportion of total global at-risk revenue originating from a specific geographical region.
* **Mathematical Formula:**
  $$RCS_{\text{region}} = \frac{\sum_{i \in \text{Late, Region}} \text{Order Item Total}_i}{\sum_{j \in \text{Late, Global}} \text{Order Item Total}_j} \times 100$$
* **Project Observed Values:**
  * **Western Europe:** $\frac{\$2,957,445.00}{\$18,082,555.30} \times 100 = \mathbf{16.36\%}$
  * **Central America:** $\frac{\$2,794,609.15}{\$18,082,555.30} \times 100 = \mathbf{15.45\%}$
  * **Combined Top Two Share:** $\mathbf{31.81\%}$ of all globally delayed revenue is concentrated in these two regions.

---

## 3. Shipping Class Operational Metrics

### 3.1 Mode Late Ratio ($MLR$)
* **Definition:** The rate of late deliveries occurring within a specific shipping mode.
* **Mathematical Formula:**
  $$MLR_{\text{mode}} = \frac{N_{\text{Late, mode}}}{N_{\text{Total, mode}}} \times 100$$
* **Project Observed Values:**
  * **First Class:** $\frac{26,513}{27,814} \times 100 = \mathbf{95.32\%}$
  * **Second Class:** $\frac{26,987}{35,216} \times 100 = \mathbf{76.63\%}$
  * **Same Day:** $\frac{4,454}{9,737} \times 100 = \mathbf{45.74\%}$
  * **Standard Class:** $\frac{41,023}{107,752} \times 100 = \mathbf{38.07\%}$

---

### 3.2 Real vs. Scheduled Transit Delta ($RSD$)
* **Definition:** The gap between the mean empirical transit time and the nominal scheduled SLA promise for a shipping tier.
* **Mathematical Formula:**
  $$RSD_{\text{mode}} = \overline{\text{Days}}_{\text{real, mode}} - \overline{\text{Days}}_{\text{sched, mode}}$$

| Shipping Mode | Mean Scheduled Days | Mean Actual Days | Empirical RSD Gap | Operational State |
| :--- | :---: | :---: | :---: | :--- |
| **First Class** | 1.0 day | 2.0 days | **+1.00 day** | Guaranteed failure (100% of non-canceled take 2 days) |
| **Same Day** | 0.0 days | 0.48 days | **+0.48 days** | 45.7% spill over into Day 1 |
| **Second Class** | 2.0 days | 3.99 days | **+1.99 days** | Severe lag (uniform 2-6 days transit, avg 4 days) |
| **Standard Class** | 4.0 days | 4.00 days | **-0.004 days** | Bimodal distribution: 38.6% early, 19.1% on-time, 38.1% late |

---

## 4. Summary Table of Key Project Metrics

| Metric Code | Metric Name | Mathematical Formula | Project Baseline | Business Objective |
| :--- | :--- | :--- | :---: | :---: |
| **OTD** | On-Time Delivery Rate | $(N_{\text{On-Time}} + N_{\text{Advance}}) / N_{\text{Total}} \times 100$ | **40.88%** | $> 85.0\%$ |
| **LDR** | Late Delivery Rate | $N_{\text{Late}} / N_{\text{Total}} \times 100$ | **54.83%** | $< 15.0\%$ |
| **AROV** | At-Risk Order Value | $\sum \text{Order Item Total}_{\text{Late}}$ | **$18.08M** | Minimize exposure |
| **Top-2 AROV** | Western Europe + Central America AROV | $\sum_{\text{WE+CA}} \text{Order Item Total}_{\text{Late}}$ | **$5.75M** | Priority intervention |
| **AOD** | Average Order Delay (Late Orders) | $\text{mean}(\text{Days}_{\text{real}} - \text{Days}_{\text{sched}})_{\text{Late}}$ | **+1.62 days** | $\le 0.0$ days |
| **SCR** | Shipping Cancellation Rate | $N_{\text{Canceled}} / N_{\text{Total}} \times 100$ | **4.30%** | $< 2.0\%$ |
