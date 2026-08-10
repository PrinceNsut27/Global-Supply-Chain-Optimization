# Global Supply Chain Bottleneck Analysis 
**Data Analyst:** Prince Kumar

## The Business Problem
A global FMCG (Fast-Moving Consumer Goods) enterprise was suffering from a high rate of late deliveries. These ongoing supply chain disruptions led to tied-up capital, canceled orders, and decreased customer satisfaction across international shipping routes.

## Methodology
Analyzed a massive dataset of 180,000+ historical shipping records using Python (Pandas, Matplotlib, Seaborn). 
* Engineered data pipelines to calculate real-vs-scheduled delivery deltas.
* Isolated late delivery statuses and aggregated the trapped `Order Item Total` to quantify financial risk.
* Generated a high-resolution, heat-mapped visualization to quickly identify regions with the most severe operational failures.
* **Dataset Used:** [DataCo Smart Supply Chain Dataset via Kaggle](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis)

## Business Impact & Strategic Recommendation
* **Findings:** Identified nearly **$6 million** in trapped revenue due to severe bottlenecks, with Western Europe and Central America acting as the primary points of failure. 
* **Actionable Insight:** Modeled a strategic routing intervention, proposing a shift of 15% of Standard Class freight to First Class within the top two failing regions to mitigate future operational losses and protect at-risk revenue.

