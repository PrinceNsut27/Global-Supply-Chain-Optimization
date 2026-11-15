# Dataset Description & Data Dictionary

## 1. Dataset Provenance & Overview
The analytical foundation for this project is the **DataCo Smart Supply Chain for Big Data Analysis** dataset, sourced from Kaggle. The dataset captures end-to-end operational, logistical, and commercial transactions of an international consumer goods and retail enterprise operating global supply chain channels across multiple continents.

* **Primary Source:** [DataCo Smart Supply Chain Dataset via Kaggle](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis)
* **Dataset Shape:** 180,519 transaction records across 53 structured fields.
* **Temporal Scope:** January 2015 through January 2018.
* **Granularity:** Line-item fulfillment level (each row represents a distinct item within a multi-item or single-item customer order).
* **Unique Entities:**
  * **65,752** distinct customer orders (`Order Id`)
  * **20,652** distinct customers (`Customer Id`)
  * **118** distinct product catalog items (`Product Card Id`)
  * **51** product categories (`Category Id`)
  * **23** global delivery regions (`Order Region`) across 5 macro-markets (`Market`)

---

## 2. Data Cleaning & Encoding Specifications

### Character Encoding
The source CSV file (`DataCoSupplyChainDataset.csv`) contains international characters across customer names, city names, and product titles (e.g., accented characters in Spanish and French geographic names). Loading the dataset requires `latin-1` (or `ISO-8859-1`) encoding:
```python
import pandas as pd
df = pd.read_csv('DataCoSupplyChainDataset.csv', encoding='latin-1')
```
Attempting to parse using standard `utf-8` results in a `UnicodeDecodeError` at byte position containing non-ASCII regional characters.

### Data Completeness & Null Analysis
* **Core Logistics Attributes:** Critical fields utilized in this study (`Days for shipping (real)`, `Days for shipment (scheduled)`, `Delivery Status`, `Shipping Mode`, `Order Region`, and `Order Item Total`) contain **zero missing values (100% complete)** across all 180,519 rows.
* **Informational Fields with Nulls:** Fields such as `Product Description` (100% missing) and `Order Zipcode` (86.3% missing) are omitted from operational delay modeling.

---

## 3. Data Dictionary

The table below documents the 25 primary columns pertinent to supply chain fulfillment, regional bottleneck identification, and financial exposure modeling:

| Column Name | Data Type | Example Value | Description & Business Usage |
| :--- | :--- | :--- | :--- |
| `Days for shipping (real)` | Integer | `3` | Actual measured transit time from warehouse dispatch to recorded customer delivery. |
| `Days for shipment (scheduled)` | Integer | `4` | Target SLA transit promise communicated to the customer based on chosen shipping class. |
| `Delivery Status` | String / Categorical | `Late delivery` | Categorical classification: `Late delivery`, `Shipping on time`, `Advance shipping`, `Shipping canceled`. |
| `Late_delivery_risk` | Binary Flag (0/1) | `1` | Indicator flag denoting whether the shipment is classified as having late delivery risk. |
| `Shipping Mode` | String / Categorical | `Standard Class` | Fulfillment service level tier: `Standard Class`, `Second Class`, `First Class`, `Same Day`. |
| `Order Id` | Integer | `77202` | Unique identifier for the customer purchase order. Multiple rows can share one Order Id. |
| `Order Item Id` | Integer | `180517` | Unique line-item identifier within an order. Primary surrogate key. |
| `Order Item Total` | Float | `184.50` | Net monetary value for the order line item after applying discounts: `(Product Price * Quantity) - Discount`. |
| `Sales` | Float | `200.00` | Gross revenue for the line item prior to discount deduction: `Product Price * Quantity`. |
| `Order Item Discount` | Float | `15.50` | Total monetary promotional discount applied to the line item. |
| `Order Item Discount Rate` | Float | `0.08` | Percentage discount applied relative to gross sales. |
| `Order Profit Per Order` | Float | `32.40` | Net operational profit allocated to this specific order line item. |
| `Order Item Profit Ratio` | Float | `0.18` | Profit margin ratio: `Order Profit Per Order / Order Item Total`. |
| `order date (DateOrders)` | Timestamp | `2017-10-02 12:45:00` | Exact timestamp when the order was placed by the customer. |
| `shipping date (DateOrders)`| Timestamp | `2017-10-06 12:45:00` | Timestamp when the order was handed over to the logistics carrier. |
| `Order Region` | String / Categorical | `Western Europe` | Destination geographical territory for the delivery (23 distinct regions). |
| `Market` | String / Categorical | `Europe` | High-level geographical commercial theater (`Europe`, `LATAM`, `Pacific Asia`, `USCA`, `Africa`). |
| `Order Country` | String | `Francia` | Destination sovereign country. |
| `Order City` | String | `Paris` | Destination municipality or city. |
| `Customer Id` | Integer | `12345` | Unique identifier of the purchasing customer. |
| `Customer Segment` | String / Categorical | `Consumer` | Segment classification: `Consumer`, `Corporate`, `Home Office`. |
| `Category Name` | String | `Sporting Goods` | Product category taxonomy. |
| `Product Name` | String | `Perfect Fitness Perfect Rip Deck` | Description title of the physical SKU. |
| `Product Price` | Float | `59.99` | Unit list price of the product. |
| `Order Item Quantity` | Integer | `1` | Physical count of units fulfilled in this line item. |

---

## 4. Derived & Engineered Attributes

To perform bottleneck analysis and quantify transit variance, the analytical pipeline engineers the following fields:

### `Delivery_Delay_Days`
$$\text{Delivery\_Delay\_Days} = \text{Days for shipping (real)} - \text{Days for shipment (scheduled)}$$
* **Interpretation:**
  * Positive values ($> 0$): Shipment arrived later than scheduled promise (operational delay).
  * Zero ($= 0$): Shipment arrived exactly on the scheduled day.
  * Negative values ($< 0$): Shipment arrived earlier than scheduled (advance delivery).

### `Late_Flag`
$$\text{Late\_Flag} = \begin{cases} 1, & \text{if Delivery Status} = \text{'Late delivery'} \\ 0, & \text{otherwise} \end{cases}$$
Used for binary aggregations, regional delay rate computations, and carrier compliance metrics.
