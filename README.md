# Coffee-Sales-Analysis

The Daily Grind Coffee - Sales Analysis (2023-2025)
📊 Project Overview
This project analyzes three years of revenue, profit, and sales performance data for The Daily Grind Coffee, a specialty coffee retailer. The analysis covers 2023–2025, examining trends across product categories, regions, and time periods to identify growth opportunities and optimize profitability.

🎯 Key Metrics & Findings
Overall Performance (Full 3-Year Period)
Total Revenue: $871.07K
Total Profit: $477.71K
Profit Margin: 54.84%
Unique Customers: 200
Total Orders: 4,432
Total Units Sold: 11,035
Customer & Sales Insights
Strong customer base with 200 unique customers across the period
Average order value demonstrates consistent repeat purchases
High profit margin indicates healthy pricing strategy and cost management
📈 Product Category Performance
KPI by Product Category


Category	Sales %	Key Insight
Grinders & Brewers	57.51%	Largest revenue driver; core product line
Consumables	57.89%	Strong performance; recurring revenue stream
Accessories	18.97%	Solid contributor; bundling opportunity
Subscriptions	8.62%	Growing segment; customer retention tool
Merchandise	7.51%	Smallest category; potential for growth
Key Takeaway: Coffee equipment and consumables dominate sales, suggesting customers invest in quality brewing solutions and regularly repurchase supplies.

Regional Performance (2024-2025)
KPI by Year, Quarter, Month, Day and Region
South Region: Strongest performer; consistent peaks in 2024-2025
East Region: Steady baseline revenue; stable customer base
West Region: Moderate performance; growth potential
North Region: Emerging region; growing seasonal spikes
Trend: Multi-region expansion shows healthy geographic diversification. Peak seasons align with Q1 and Q4 (holiday gifting and New Year resolutions).

Detailed Data Sample
The dashboard includes daily transaction-level data showing:

Order dates broken down by day of week (Monday-Saturday peaks)
Regional revenue splits (East, North, South, West)
Daily KPI fluctuations to identify peak sales windows
Example: Friday, January 6, 2023 generated $892.23 in the East region alone, indicating strong weekend demand.

Strategic Recommendations
Based on the analysis:

Leverage High-Margin Products: Grinders & Brewers and Consumables drive profitability—increase marketing spend here.
Expand Subscriptions: Subscriptions offer recurring revenue and predictable cash flow; grow this segment.
Regional Focus: South and East regions show strength; replicate their strategies in North and West regions.
Seasonal Planning: Plan inventory and promotions around Q1 and Q4 peaks.
Product Bundling: Pair accessories with core products to increase average order value.

Tools Used
Power BI: Interactive dashboard and visualization
Excel/Spreadsheet: Data storage and initial exploration
SQL (Optional): Data queries and aggregations

How to Use This Analysis
View the Dashboard: Open the Power BI file to explore interactive filters by year, quarter, month, region, and product category.
Review Key Metrics: Check the summary cards for revenue, profit, margin, and customer counts.
Analyze Trends: Use the time-series chart to identify seasonal patterns and regional performance.
Make Decisions: Reference the strategic recommendations to guide pricing, inventory, and marketing initiatives.
👥 Stakeholders
Sales Team: Use regional data to optimize territory strategies
Marketing Team: Identify high-performing seasons and product categories
Finance Team: Monitor margin and profitability trends
Operations Team: Plan inventory based on demand patterns
📅 Analysis Period
Start Date: January 1, 2023
End Date: December 31, 2025 (Q1 2025 data shown)
Data Granularity: Daily transactions with regional and product-level breakdowns

<img width="1409" height="737" alt="image" src="https://github.com/user-attachments/assets/f0cbd8b9-0396-426f-b7d1-2c68542b1757" />


<img width="1406" height="737" alt="image" src="https://github.com/user-attachments/assets/639710fe-a0cf-490a-b7be-ee18970fca4a" />

There are 4 products whose 3-year profit margin is less than 30% - Chemex Filters, Minimalist Keychain, Black Logo Hoodies, and Gooseneck Electric Kettle

The price of all 4 products has remained the same in the past 3 years.
The demand for the first 3 products (Chemex Filters, Minimalist Keychain, Black Logo Hoodies) has consistently declined and as a result so has the revenue.
The demand for Gooseneck Electric Kettles dipped in 2024 but rallied in 2025.
The Cost of Goods Sold (COGS) has declined for first three products.
The demand for Gooseneck Electric Kettles dipped in 2024 but rallied in 2025.

We aim to have a minimum of 30% profit margin


## My Recommendations:
### 1. Strategy for the "Gooseneck Electric Kettle" (The Priority)
This product is an outlier because demand is actually recovering (rallied in 2025), yet the profit margin has slipped from ~32% to ~25.5%. Since the price has remained flat for 3 years, margins have dropped, and unit costs (COGS) have increased (likely due to inflation or material costs).

#### Recommendation A: Increase the Retail Price
Why: The demand rallied in 2025 despite the product being older. This indicates strong brand loyalty or market need. Customers are likely willing to pay slightly more.<br/>
Action: Increase the price by 10–15%.<br/>
Outcome: Since the price hasn't changed in 3 years, a correction is overdue. This will immediately lift the margin back above the 30% threshold without significantly hurting the recovering demand.<br/>
#### Recommendation B: Renegotiate Supplier Costs
Why: We have leverage. Unlike the other products, volume for the Kettle is up.<br/>
Action: Approach the supplier with the 2025 growth data. Ask for a volume discount or a return to previous pricing tiers based on the increased order quantity.
### 2. Strategy for Filters, Keychains, and Hoodies
These three products are currently "dead weight." Demand is falling, revenue is falling, and margins have crashed to roughly 12% (well below the 30% target). Even though total COGS declined, the margin compression suggests the per-unit cost is too high for the current price point.

#### Recommendation A: Discontinue Product
Why: These items are trending toward zero profitability. Spending marketing budget to revive them is risky.<br/>
Action: Stop placing new orders immediately. Mark these items as "End of Life" (EOL).<br/>
#### Recommendation B: Liquidation & Bundling
Why: We need to clear the existing inventory to free up cash and warehouse space.<br/>
Action: Create "Coffee Lover Bundles." Pair the low-margin Chemex Filters or Logo Hoodies with high-margin items (like the Automated Drip Brewer or Espresso Bean Sampler).<br/>
Outcome: This helps move the stagnant inventory without explicitly discounting the item further (which would hurt the margin more) and increases the perceived value of your best-sellers.<br/>
### Summary Table

<table>
 <tr><th>Product</th>	<th>Trend</th><th>	Diagnosis</th><th> Recommendation</th></tr>
<tr><td>Gooseneck Kettle</td>	<td>Demand ↑ / Margin ↓</td>	<td>Rising unit costs; Underpriced </td>	<td>Raise Price & Renegotiate Cost</td></tr>
<tr><td>Chemex Filters</td>	<td>Demand ↓ / Margin ↓	</td><td>Dying product</td>	<td>Bundle to clear & Discontinue</td></tr>
<tr><td>Keychain</td>	<td>Demand ↓ / Margin ↓	</td><td>Low value add</td>	<td>Clearance Sale & Discontinue</td></tr>
<tr><td>Logo Hoodie</td>	<td>Demand ↓ / Margin ↓</td>	<td>Lost appeal</td>	<td>Bundle & Discontinue</td></tr>
</table>



