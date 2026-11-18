# Retail Sales Performance Analysis Using Excel

https://github.com/goodysinsight/Excel-retail-sales-Dashboard/blob/main/dashboard.png

## Business question

Sales are growing, but profit is not keeping pace. Which products, regions and discount levels drive profit, and where is the business losing money?

## Dataset

Superstore Sales dataset from Kaggle: 9,994 order lines, 5,009 orders and 793 customers across four US regions, from January 2014 to December 2017. Each line has sales, quantity, discount and profit, plus product, customer and location details. The dataset has no cost data, so profit is taken as given.

Source: https://www.kaggle.com/datasets/vivek468/superstore-dataset-final

## Approach

I imported the raw CSV into Excel, converted it to a Table, fixed data types, and checked for duplicates, blanks and impossible dates (ship date before order date). I then added calculated columns for Year, Month, Profit Margin %, Ship Days, a Discount Band and a Profit/Loss flag. Five PivotTables summarise the data by region, category, segment, discount band and month, and each feeds a PivotChart on the dashboard. Slicers for Year, Region and Segment filter every chart and KPI card at once. Cleaning steps are documented in the `Data cleaning` sheet.

## What the data shows

Overall the business earned $286,397 profit on $2,297,201 of sales, a 12.5% margin. Between 2014 and 2017 sales grew 51% and profit grew 89%, so over the full period profit did keep up. The problem shows up in the last year. In 2017 sales rose 20% but profit rose only 14%, and the margin slipped from 13.4% to 12.7%. Something is eating into profit as the business scales, and the data points to discounting.

Discounts above 20% are the clearest source of loss. These orders make up just 14% of order lines and 16% of sales, yet they lost $135,376 in total. Orders discounted 21 to 40% run at a margin of about -15%, and orders discounted above 40% lose roughly 77 cents on every dollar sold. Everything else in the business earned $421,773, which means the deep-discounted orders cut total profit by about a third. They also account for 72% of every loss-making order line in the dataset. Orders with no discount, by comparison, earn a 29.5% margin. This is an upper bound on what is recoverable, because some of those orders might never have happened without the discount, but it is large enough to be the first thing worth examining.

Furniture is where the problem concentrates. It brings in 32% of sales but only 6% of profit, with a margin of 2.5% against about 17% for both Office Supplies and Technology. Tables are the worst case, losing $17,725 on $207,000 of sales, and Bookcases also run at a loss. More than half of all Table orders carry a discount above 20%. When I split Furniture by discount level, the orders discounted above 20% lost $54,478, while the rest earned $72,929, a healthy margin of roughly 13%. So Furniture is not a weak category by nature. It is a decent category being pulled down by how it is discounted.

The same pattern explains the regional gap. Central is the weakest region with a 7.9% margin, against 14.9% in the West and 13.5% in the East. Central's average discount is 24%, compared with 11% in the West, and 28% of its order lines are discounted above 20% against under 4% in the West. Its deep-discounted orders lost $52,392, more than the region's entire $39,706 profit. Central's Furniture sales actually lose money overall.

Timing matters too. September, November and December together produce 43% of annual sales, and December is the most profitable month at $43,369. January and February are the weakest, contributing under 7% of sales between them. Customer segment differences are smaller: Consumer is half of all sales but has the lowest margin at 11.5%, while Home Office is the smallest segment with the highest at 14.0%.

## Recommendations

Cap discounts at 20% unless a manager approves an exception, and start with Furniture and the Central region, where the damage is greatest. Review pricing on Tables and Bookcases separately, since even their lightly discounted orders earn very little. Plan stock and promotions around the September to December peak, and avoid deep discounting in that window just to move volume that would sell anyway. Finally, track margin alongside sales every quarter, because the 2017 slip would have been easy to miss by watching sales growth alone.

## Limitations

The dataset has no product cost or reason for discounting, so these findings show association rather than proof of cause. A deeper discount may be paired with products that already had thin margins, or with clearance stock. A proper test would compare similar orders at different discount levels.

## Files

`Retail sales performance dashboard.xlsx` contains the raw data, the cleaned Table, the PivotTables and the dashboard. Screenshots are in the `dashboard.png` folder.

## Tools

Microsoft Excel: Tables, calculated columns, PivotTables, PivotCharts, slicers and GETPIVOTDATA.
