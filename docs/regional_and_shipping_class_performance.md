# Regional & Shipping-Class Performance

## 1. Regional Fulfillment Performance
Delivery performance varies dramatically across global territories. This analysis evaluates the 23 destination territories (`Order Region`), ranking them by the gross order value subjected to delivery delays.

### Top 15 Regions by Late Delivery Value

| Rank | Order Region | Total Shipments | Late Shipments | Late Delivery Rate (%) | Total Regional Value ($) | Late Order Value ($) | Global At-Risk Share (%) | Mean Delay (Days) |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **1** | **Western Europe** | 27,109 | **15,140** | **55.85%** | $5,296,003.11 | **$2,957,445.00** | **16.36%** | +1.63 |
| **2** | **Central America**| 28,341 | **15,518** | **54.75%** | $5,093,850.15 | **$2,794,609.15** | **15.45%** | +1.61 |
| **3** | South America | 14,935 | 8,111 | 54.31% | $2,660,244.18 | $1,444,511.58 | 7.99% | +1.62 |
| **4** | Northern Europe | 9,792 | 5,292 | 54.04% | $1,939,361.85 | $1,037,341.15 | 5.74% | +1.63 |
| **5** | Southern Europe | 9,431 | 5,129 | 54.38% | $1,837,526.11 | $987,398.22 | 5.46% | +1.56 |
| **6** | Oceania | 10,148 | 5,482 | 54.02% | $1,809,997.27 | $969,617.52 | 5.36% | +1.62 |
| **7** | Southeast Asia | 9,539 | 5,297 | 55.53% | $1,738,552.88 | $964,124.65 | 5.33% | +1.60 |
| **8** | South Asia | 7,731 | 4,350 | 56.27% | $1,397,365.17 | $785,209.49 | 4.34% | +1.63 |
| **9** | Caribbean | 8,318 | 4,415 | 53.08% | $1,481,668.61 | $782,685.72 | 4.33% | +1.63 |
| **10**| West of USA | 7,993 | 4,313 | 53.96% | $1,412,254.49 | $752,118.09 | 4.16% | +1.64 |
| **11**| Eastern Asia | 7,280 | 3,955 | 54.33% | $1,334,312.92 | $728,551.72 | 4.03% | +1.66 |
| **12**| East of USA | 6,915 | 3,849 | 55.66% | $1,231,954.82 | $677,413.06 | 3.75% | +1.59 |
| **13**| West Asia | 6,009 | 3,322 | 55.28% | $1,056,080.70 | $590,250.08 | 3.26% | +1.60 |
| **14**| US Center | 5,887 | 3,252 | 55.24% | $1,034,128.59 | $573,700.73 | 3.17% | +1.59 |
| **15**| South of USA | 4,045 | 2,256 | 55.77% | $706,904.30 | $392,604.94 | 2.17% | +1.65 |

### Regional Insights:
1. **The Primary Failure Points:** Western Europe ($2.96M) and Central America ($2.79M) combine for **$5,752,054.15** (~$5.75M, "nearly $6 million") across **30,658 late shipments**.
2. **Homogeneous Failure Rates:** Remarkably, the late delivery rate across almost all global regions clusters within a narrow band of **53% to 56%**. This uniformity indicates that delay behavior is driven by centralized scheduling rules rather than purely localized geographic anomalies.

---

## 2. Shipping-Class Performance Comparison

The enterprise provides four fulfillment classes. Each class exhibits fundamentally different transit mechanics:

| Shipping Mode | Total Volume | Volume Share (%) | Late Shipments | Late Rate (%) | Total Value ($) | Late Value ($) | Mean Sched Days | Mean Real Days | Net Delay Gap (Days) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Standard Class**| **107,752** | **59.69%** | **41,023** | **38.07%** | $19,792,222.17 | **$7,516,306.02** | 4.00 | 4.00 | -0.004 |
| **Second Class** | 35,216 | 19.51% | 26,987 | 76.63% | $6,416,528.60 | $4,918,062.80 | 2.00 | 3.99 | +1.99 |
| **First Class** | 27,814 | 15.41% | 26,513 | **95.32%** | $5,100,450.81 | $4,860,949.75 | 1.00 | 2.00 | **+1.00** |
| **Same Day** | 9,737 | 5.39% | 4,454 | 45.74% | $1,745,200.80 | $787,236.73 | 0.00 | 0.48 | +0.48 |
| **Total** | **180,519** | **100.0%** | **98,977** | **54.83%** | **$33,054,402.38** | **$18,082,555.30** | **2.93** | **3.50** | **+0.57** |

---

## 3. Deep Dive: Shipping Modes in Western Europe & Central America

Because Western Europe and Central America represent 31.81% of total at-risk value, their internal shipping class dynamics are evaluated below:

### Western Europe Performance by Shipping Mode
* **Total Regional Volume:** 27,109 shipments | Total Value: $5,296,003.11
* **Total Regional Late Deliveries:** 15,140 shipments (55.85%) | Late Value: $2,957,445.00

| Shipping Mode in Western Europe | Total Shipments | Late Shipments | Mode Late Rate (%) | Total Value ($) | Late Value ($) | Mean Delay (Days) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Standard Class** | 15,864 | 6,089 | **38.38%** | $3,120,396.69 | **$1,212,878.96** | -0.01 |
| **Second Class** | 5,438 | 4,236 | **77.90%** | $1,051,940.48 | $810,960.78 | +1.99 |
| **First Class** | 4,312 | 4,107 | **95.25%** | $843,504.22 | $801,200.06 | +1.00 |
| **Same Day** | 1,495 | 708 | 47.36% | $280,161.72 | $132,405.20 | +0.47 |

---

### Central America Performance by Shipping Mode
* **Total Regional Volume:** 28,341 shipments | Total Value: $5,093,850.15
* **Total Regional Late Deliveries:** 15,518 shipments (54.75%) | Late Value: $2,794,609.15

| Shipping Mode in Central America | Total Shipments | Late Shipments | Mode Late Rate (%) | Total Value ($) | Late Value ($) | Mean Delay (Days) |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Standard Class** | 17,055 | 6,571 | **38.53%** | $3,072,249.77 | **$1,192,804.09** | -0.01 |
| **Second Class** | 5,481 | 4,111 | **75.00%** | $976,047.53 | $727,633.51 | +1.98 |
| **First Class** | 4,382 | 4,185 | **95.50%** | $793,412.83 | $757,936.19 | +1.00 |
| **Same Day** | 1,423 | 651 | 45.75% | $252,140.02 | $116,235.36 | +0.48 |

---

## 4. Analytical Findings on the Top Two Regions
1. **Identical Mode Proportions:** In both Western Europe and Central America, Standard Class represents ~59% of orders, Second Class represents ~19%, First Class represents ~16%, and Same Day represents ~5%.
2. **Standard Class Exposure:** In Western Europe and Central America combined, Standard Class accounts for **12,660 late deliveries** (6,089 + 6,571) representing **$2,405,683.05** in delayed merchandise value.
3. **The Transit Speed Dilemma:** Standard Class orders take between 2 and 6 days (mean 4.0 days), with 38.4% taking 5 or 6 days. In contrast, First Class orders take **consistently 2.0 days**. This fundamental speed gap forms the basis of the strategic routing recommendation.
