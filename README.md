# DataAnalytics1
# Shipment Cost Normalization & Outlier Analysis
## Overview
This project analyzes **parcel invoice data for a shoe company** to build a **normalized shipment cost model** that allows fair comparison of shipping costs across different carriers. Raw shipping invoices often contain multiple charges (base cost, fuel surcharge, handling fees, etc.) and shipments vary by **weight, distance, and service level**, making direct cost comparison misleading. This analysis aggregates invoice charges at the shipment level and normalizes cost by shipment characteristics to enable **fair benchmarking of carriers and identification of expensive shipments**

## Objectives
* Aggregate invoice-level charges to total shipment cost
* Create a normalized shipping cost metric
* Compare carrier efficiency
* Identify the worst 10% shipments by normalized cost
* Estimate the share of total spend contributed by these shipments

## Dataset
The dataset contains parcel invoice data with features such as:
* Tracking Number
* Carrier Name
* Service Level
* Zones (distance indicator)
* Weight (lbs)
* Dimensions (in)
* Charge Type
* Charge Amount
* Pickup Zipcode
* Dropoff Zipcode
* Date of Delivery
Each shipment may have multiple charge rows, representing different invoice components.

## Methodology

### 1. Shipment-Level Aggregation
Invoice data was aggregated using the tracking number to obtain
Total Shipment Cost = sum of all charges for that shipment
Then divide charges into Base and additional for normalisation

### 2. Cost Normalization
Shipping cost depends primarily on **weight and distance**.
A normalized metric was created:
Normalized Cost = Total Cost / (Weight × Zone) also considering volume
This allows fair comparison between shipments with different sizes and distances.

### 3. Carrier Benchmarking

Average normalized cost was calculated for each: Carrier + Service Level combination
This reveals which carriers provide **more cost-efficient shipping**.

### 4. Identifying Expensive Shipments
The 90th percentile of normalized cost was used to define the **worst 10% shipments**.
Worst shipments = shipments with normalized cost ≥ 90th percentile

### 5. Outlier Analysis
Worst shipments were analyzed to determine whether they are concentrated by:
**Carrier, Zone, Service level, Charge types**

### 6. Spend Contribution
The share of total shipping spend caused by these worst shipments was calculated:
Worst Spend Share = (Cost of worst shipments / Total shipping cost) × 100
This quantifies how much inefficient shipments impact total logistics cost.

## Key Insights
The analysis reveals:
* Raw shipping cost comparisons can be misleading.
* After normalization, significant differences appear between carriers.
* A small portion of shipments (the worst 10%) often contributes a **disproportionate share of total shipping spend**.
* High costs are frequently associated with:
* Express service levels
* Specific carriers.

## Technologies Used
* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook / Google Colab

## Output

The project produces:
* **Carrier cost comparison tables**
* **Service-level efficiency comparisons**
* **Cost distribution visualization**
* **Identification of high-cost shipment outliers**


## Business Value

This model helps companies:
* Benchmark carrier pricing
* Identify inefficient shipments
* Optimize logistics costs
* Negotiate better carrier contracts
  
## Future Improvements

Potential extensions include:
* Regression-based shipping cost models
* Weight–zone cost heatmaps
* Carrier performance dashboards
* Predictive shipping cost models

