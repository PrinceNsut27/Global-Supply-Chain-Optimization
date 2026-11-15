# Business Problem & Stakeholder Impact Analysis

## 1. Executive Context & Industry Background
In global Fast-Moving Consumer Goods (FMCG) and multi-category e-commerce operations, delivery punctuality is a primary driver of customer retention, Net Promoter Score (NPS), and working capital velocity. Modern supply chain networks operate under strict Service Level Agreements (SLAs). When deliveries are consistently delayed, enterprises face cascading operational friction:
* Increased customer support ticket volume (WISMO: *"Where Is My Order?"*).
* Higher rates of order cancellations, return-to-origin (RTO) shipments, and refund claims.
* Working capital trapped in transit across extended delivery cycles.
* Reputational degradation leading to customer churn in highly competitive regional markets.

This project investigates the historical shipping performance of a global consumer goods enterprise across 180,519 order fulfillment records, analyzing the operational and financial impact of delivery delays across global territories and carrier shipping modes.

---

## 2. Problem Statement
The enterprise's global fulfillment network experiences an acute delivery delay crisis:
* **Overall Late Delivery Rate:** **54.83%** of all fulfilled shipments arrive after their scheduled delivery target.
* **Order Item Value Associated with Delays:** Out of **$33.05M** in total historical sales, **$18.08M** in gross order item value has been subjected to late delivery.
* **Geographical Concentration:** Delays are heavily concentrated in specific global theaters, with the top two regions—**Western Europe** and **Central America**—accounting for **$5.75M** (nearly $6M) in delayed shipment value across **30,658 late shipments**.
* **Structural Promise Mismatch:** A substantial portion of the delay volume is driven by static, unrealistic delivery promises assigned to premium shipping tiers (such as 1-day promises on international routes), setting up fulfillment operations for automatic SLA failure.

---

## 3. Financial Clarification: Order Value at Risk vs. Accounting Loss

> [!IMPORTANT]
> **Key Analytical Distinction: Order Value at Risk vs. Realized Loss**
> The **~$5.75M** (nearly $6M) identified in Western Europe and Central America—and the **$18.08M** across the entire dataset—represents the **gross order item total of shipments that suffered delivery delays**.
> * It **does NOT** represent a direct accounting loss, unrecoverable revenue, or verified refund chargeback.
> * It represents **revenue at risk** (exposure). When shipments are late, this revenue is exposed to customer dissatisfaction, potential cancellation prior to delivery, post-delivery returns, customer service overhead, and diminished repeat-purchase rates.

### Exposure Mechanism
$$\text{Revenue at Risk (Exposure)} = \sum_{i \in \text{Late Shipments}} \text{Order Item Total}_i$$

* Actual financial loss would be a downstream fraction of this figure, driven by:
  $$\text{Financial Loss} = (\text{At-Risk Value} \times \text{Cancellation Rate}) + (\text{At-Risk Value} \times \text{Return Rate}) + \text{WISMO Support Overhead} + \text{Customer Churn LTV Loss}$$

---

## 4. Stakeholder Impact Matrix

The persistence of a 54.8% late delivery rate creates distinct operational and strategic challenges across corporate stakeholder groups:

| Stakeholder Persona | Strategic Concerns | Operational Pain Points | Direct KPI Impact |
| :--- | :--- | :--- | :--- |
| **Chief Supply Chain Officer (CSCO) / VP Logistics** | Fulfillment network resilience, carrier contract compliance, freight budget efficiency | Carrier dispatch delays, bottlenecked transfer hubs, lack of dynamic SLA capability | • On-Time Delivery Rate (OTD)<br>• Average Shipping Delay Days<br>• Carrier SLA Adherence |
| **Chief Financial Officer (CFO)** | Capital efficiency, cash conversion cycle (CCC), margin erosion from concessions | Revenue tied up in transit, dispute chargebacks, refund processing fees | • Revenue at Risk ($M)<br>• Freight Expense Ratio<br>• Return & Concession Costs |
| **Regional Fulfillment & Logistics Managers** (Western Europe & Central America) | Local carrier management, cross-border customs throughput, warehouse dispatch capacity | Static SLA schedules ignoring local transit realities; lack of carrier accountability | • Regional On-Time Delivery %<br>• Lead Time Variance<br>• Node-to-Door Transit Days |
| **VP of Customer Experience & Support** | Brand reputation, repeat purchase retention, customer lifetime value (LTV) | High influx of delivery inquiry tickets, negative app/site reviews, customer churn | • WISMO Ticket Volume<br>• CSAT / NPS Score<br>• First Contact Resolution (FCR) |
| **Product Managers (Supply Chain & Checkout Platforms)** | Checkout promise accuracy, conversion vs. retention trade-off, checkout UX | Disconnect between promised delivery dates shown to shoppers and physical fulfillment capability | • Checkout Conversion Rate<br>• Delivery Date Promise Accuracy<br>• Cart Abandonment |

---

## 5. Project Objectives
1. **Isolate Delay Hotspots:** Identify the specific global regions and shipping modes generating the highest concentration of late deliveries and associated order values.
2. **Conduct Root-Cause Analysis:** Deconstruct the variance between `Days for shipping (real)` and `Days for shipment (scheduled)` across all fulfillment tiers.
3. **Formulate Actionable Interventions:** Evaluate potential operational solutions, including carrier SLA recalibration and strategic routing adjustments (such as modeling a 15% freight shift from Standard Class to First Class).
4. **Define Implementation Framework:** Provide an analytical roadmap and validation plan to guide supply chain leadership prior to capital deployment.
