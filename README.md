<img width="1379" height="738" alt="image" src="https://github.com/user-attachments/assets/28132295-fbb4-4db6-b077-78f56374835d" /><img width="1379" height="738" alt="image" src="https://github.com/user-attachments/assets/e12a7069-50bd-4772-9f05-df4061d48b67" /># Coffee-Sales-Analysis

The Daily Grind Coffee - Sales Analysis (2023-2025)<br/>
Overview
--------

We received the following directive from Operations: a significant decline in portfolio profit margin—likely due to rising COGS, tariffs, and other factors—requires a pricing review using 2023–2025 order data. The priority is to:

*   Identify products with Gross Margin % (GMP) below 30% in Q3 2025
    
*   Build a dashboard showing Year-over-Year GMP and Revenue by Category, Product, and Region
    
*   Provide clear, data-backed recommendations for price increases or discontinuation
    

So what: This project consolidates multi-source order and cost data into a single analytical dataset, quantifies margin erosion, pinpoints where profit is leaking (by product and region), and translates insights into specific, financially grounded pricing actions.

Business Goals & Success Metrics
--------------------------------

*   Detect products and regions driving margin erosion and quantify “profit at risk”
    
*   Recommend price changes to return low-margin items to target GMP (e.g., 35%+)
    
*   Flag SKUs for discontinuation where price increases are impractical or brand-damaging
    
*   Success = measurable uplift in blended GMP and profit dollars within one quarter, alongside reduced share of sub-30% GMP items
    

Key KPIs

*   Gross Margin % (GMP) = (Net Sales − COGS) / Net Sales
    
*   YoY GMP Δ and YoY Revenue Δ by Category, Product, Region
    
*   Profit at Risk = Revenue × (Target\_GMP − Current\_GMP), for items below target
    
*   Price Change Needed to hit Target GMP: P\_new = COGS / (1 − Target\_GMP)
    

Data Sources
------------

*   orders\_header: order\_id, order\_date, customer\_id, region\_id, currency, status
    
*   order\_lines: order\_id, product\_id, quantity, unit\_price, discount, tax, returns\_flag
    
*   products: product\_id, product\_name, category\_id, brand, active\_flag
    
*   categories: category\_id, category\_name
    
*   regions: region\_id, region\_name, country, channel
    
*   cogs\_history: product\_id, effective\_from, cogs\_unit
    
*   calendar: date, year, quarter, month, fiscal\_period
    

Pre-processing highlights

*   Standardize Net Sales: quantity × unit\_price × (1 − discount) minus returns
    
*   Map time-varying COGS (cogs\_history) to each order\_line by effective date
    
*   Normalize currencies and fiscal calendars; exclude canceled orders/zero-quantity rows
    
*   Deduplicate orders; reconcile product/region dimension mismatches
    
*   Add derived fields: gross\_profit, gmp, yoy\_gmp, yoy\_revenue
    

Analytical Approach (Steps Taken)
---------------------------------

1.  Data Extraction
    
    *   Built a database schema and pulled data from orders, products, regions, and COGS tables
        
    *   Created a star schema for efficient slice-and-dice by product, category, and region
        
2.  Clean & Prepare
    
    *   Wrote SQL transformations to:
        
        *   Join orders to products, regions, and time-varying COGS
            
        *   Standardize Net Sales, compute Gross Profit and GMP
            
        *   Aggregate at reporting grains (by product, category, region, quarter)
            
3.  Visualize & Analyze
    
    *   Developed an interactive dashboard to:
        
        *   Track YoY GMP and Revenue
            
        *   Surface sub-30% GMP products in Q3 2025
            
        *   Quantify price increase needed to achieve target margins
            
        *   Prioritize actions by profit impact and feasibility
            

KPI Definitions (for clarity and alignment)
-------------------------------------------

*   Net Sales: quantity × unit\_price × (1 − discount\_rate) − returns\_value
    
*   COGS: quantity × cogs\_unit (matched by effective date)
    
*   Gross Profit: Net Sales − COGS
    
*   GMP: Gross Profit / Net Sales
    
*   YoY GMP: current\_period GMP − same\_period\_last\_year GMP
    
*   Profit at Risk (for items below target): Net Sales × (Target\_GMP − GMP)
    


Installation / Requirements
---------------------------
    
*   A SQL engine (MSSQL Server).
    
  
    

Usage / Order of Execution
--------------------------

Core SQL Patterns (examples)
----------------------------

Unifying orders with time-varying COGS

sql

Find products with GMP < 30% in Q3 2025

sql
 `

Results & Visualizations (what the dashboard shows)
---------------------------------------------------

*   Portfolio Overview
    
    *   YoY GMP trend and YoY Revenue trend (2023–2025)
        
    *   Margin distribution and tail of sub-30% SKUs
        
*   Drilldowns
    
    *   Heatmap: GMP by Category × Region (spot regional cost/price pressure)
        
    *   Table: Top “Profit at Risk” SKUs with recommended price change and expected uplift
        
    *   Waterfall: Impact of price, discounting, and COGS on GMP
        
*   Scenario Tool
    
    *   Enter target GMP (e.g., 35%)
        
    *   Calculate required new price: P\_new = COGS / (1 − target\_GMP)
        
    *   Estimate profit impact with an elasticity slider (default example: −1.2\*
        

Recommendations Framework (actionable and data-backed)
------------------------------------------------------

Prioritization logic

1.  Price Increase Candidates
    
    *   Current GMP < 30%, strong or stable demand, low discount sensitivity
        
    *   Recommendation: Raise price to P\_new = COGS / (1 − target\_GMP); cap increases to protect brand
        
    *   Include guardrails: maximum % hike per quarter and competitive checks
        
2.  Cost/Packaging Optimization
    
    *   High freight/tariff share or waste; negotiate supplier terms, resize packs, or switch lanes
        
    *   Target: reduce COGS\_unit to restore margin without price shock
        
3.  Bundle or Trade-Up
    
    *   Low-margin hero SKUs bundled with high-margin complements
        
    *   Preserve perceived value while lifting blended margin
        
4.  Promotional Discipline
    
    *   SKUs with margin damage from chronic discounting
        
    *   Tighten promo calendar; move from blanket discounts to targeted offers
        
5.  Discontinue/Deprecate
    
    *   Persistently < 25–30% GMP, elastic demand, weak strategic fit
        
    *   Controlled sunset with inventory run-down plan
        

Deliverables

*   SKU-level action list with:
    
    *   Current GMP, Target GMP, Required Price, Proposed Increase %, Expected Profit Uplift, Risk Notes
        
*   Region playbooks where margin dips are localized (tariffs, logistics, taxes)
    

How to Apply This in Your Org
-----------------------------

*   Start with Q3 2025 low-margin list; socialize thresholds and guardrails with Commercial and Brand
    
*   Pilot price changes on 1–2 categories in 1–2 regions; measure elasticity and churn signals
    
*   Roll out successful patterns, and track blended GMP weekly post-change
    

Future Work
-----------

*   Elasticity estimation via uplift modeling or geo-based experiments
    
*   True cost-to-serve allocation (shipping, handling, duties) by region/channel
    
*   Competitive price scraping to bound price corridors
    
*   Forecasting: COGS trends and margin-at-risk outlook
    
*   Dynamic pricing simulations under promo and seasonality constraints
    

Risks & Considerations
----------------------

*   Customer fairness and regulatory compliance (no discriminatory pricing)
    
*   Brand perception: phase price changes to avoid negative sentiment
    
*   Data quality: reconcile returns/discount leakage; align fiscal calendars
    

Maintainers / Contact
---------------------

*   Your Name — Data Analytics | email@example.com | www.linkedin.com/in/yourprofile
    

License
-------

*   MIT License (project code)
    
*   Data usage subject to source terms; remove or anonymize any sensitive data before sharing
## Key Metrics & Findings
Overall Performance (Full 3-Year Period)
Total Revenue: $871.07K<br/>
Total Profit: $477.71K<br/>
Profit Margin: 54.84%<br/>
Unique Customers: 200<br/>
Total Orders: 4,432<br/>
Total Units Sold: 11,035<br/>
## Customer & Sales Insights
Strong customer base with 200 unique customers across the period<br/>
Average order value demonstrates consistent repeat purchases<br/>
High profit margin indicates healthy pricing strategy and cost management<br/>
## Product Category Performance
### KPI by Product Category

<table>
<tr></tr><th>Category</th><th>Sales %</th>	<th>Key Insight</th></tr>
<tr><td>Grinders & Brewers</td><td>57.51%</td><td>Largest revenue driver; core product line</td></tr>
Consumables	57.89%	Strong performance; recurring revenue stream
Accessories	18.97%	Solid contributor; bundling opportunity
Subscriptions	8.62%	Growing segment; customer retention tool
Merchandise	7.51%	Smallest category; potential for growth
</table>
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

## Strategic Recommendations
Based on the analysis:<br/>

Leverage High-Margin Products: Grinders & Brewers and Consumables drive profitability—increase marketing spend here.<br/>
Expand Subscriptions: Subscriptions offer recurring revenue and predictable cash flow; grow this segment.<br/>
Regional Focus: South and East regions show strength; replicate their strategies in North and West regions.<br/>
Seasonal Planning: Plan inventory and promotions around Q1 and Q4 peaks.<br/>
Product Bundling: Pair accessories with core products to increase average order value.<br/>

## Tools Used
Power BI: Interactive dashboard and visualization<br/>
MSSQL Server: Data cleaning, queries, and aggregations<br/>

## How to Use This Analysis
View the Dashboard: Open the Power BI file to explore interactive filters by year, quarter, month, region, and product category.
Review Key Metrics: Check the summary cards for revenue, profit, margin, and customer counts.
Analyze Trends: Use the time-series chart to identify seasonal patterns and regional performance.
Make Decisions: Reference the strategic recommendations to guide pricing, inventory, and marketing initiatives.
## Stakeholders
Sales Team: Use regional data to optimize territory strategies
Marketing Team: Identify high-performing seasons and product categories
Finance Team: Monitor margin and profitability trends
Operations Team: Plan inventory based on demand patterns
## Analysis Period
Start Date: January 1, 2023
End Date: December 31, 2025 (Q1 2025 data shown)
Data Granularity: Daily transactions with regional and product-level breakdowns

<img width="1409" height="737" alt="image" src="https://github.com/user-attachments/assets/f0cbd8b9-0396-426f-b7d1-2c68542b1757" />


<img width="1406" height="737" alt="image" src="https://github.com/user-attachments/assets/639710fe-a0cf-490a-b7be-ee18970fca4a" />

There are 4 products whose 3-year profit margin is less than 30% - Chemex Filters, Minimalist Keychain, Black Logo Hoodies, and Gooseneck Electric Kettle

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



