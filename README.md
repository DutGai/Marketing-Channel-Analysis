# Marketing Channel ROI & Acquisition Cost Analysis

A SQL analysis of 2,216 customers to find where marketing spend earns its return: which campaigns, customers, channels and products drive revenue, and what it costs to acquire a responding customer.

![SQL](https://img.shields.io/badge/SQL-MySQL-blue) ![Status](https://img.shields.io/badge/status-complete-green)

## Table of Contents

- [Business Problem](#business-problem)
- [Dataset](#dataset)
- [Methodology](#methodology)
- [Key Findings](#key-findings)
- [Business Recommendations](#business-recommendations)
- [Limitations](#limitations)
- [Next Steps](#next-steps)
- [SQL Skills Demonstrated](#sql-skills-demonstrated)
- [Repository Structure](#repository-structure)

## Business Problem

Contact cost is spent on every customer, but only some respond. The analysis answers:

- How many customers respond, and what are they worth?
- Which campaign brings the most customers, and which brings the best customers?
- Which purchase channels and product categories drive revenue?
- What does it cost to acquire a responding customer?

## Dataset

- **Database:** `Marketing_Channel_Analysis`
- **Table:** `marketing` (2,216 customer records)
- **Contents:** customer profile (birth year, education, marital status, income, customer start date), spend in six product categories (wines, fruits, meat, fish, sweets, gold), purchases by channel (web, catalogue, store), acceptance of five past campaigns, response to the latest campaign, and contact cost / revenue constants (`Z_CostContact`, `Z_Revenue`).
- **Data quality:** no missing values in ID, Year_Birth, Education, Marital_Status, Income, Dt_Customer or Response.

## Methodology

1. **Check data quality:** counted missing values across key columns.
2. **Define metrics:** total revenue, conversion rate, average spend, CAC and ROAS.
3. **Analyse:** compared results by campaign, response, purchase channel and product category.
4. **Segment:** grouped customers by total spend into high, medium and low value tiers.

## Key Findings

| Metric | Result |
|---|---|
| Customers analysed | 2,216 |
| Total revenue (six categories) | 1,345,279 |
| Latest campaign conversion rate | 15.03% (333 customers) |
| Responder spend vs non-responder | About 82% higher |
| Most accepted campaign | Campaign 4 (162 customers) |
| Least accepted campaign | Campaign 2 (30 customers) |
| Highest-spending campaign group | Campaign 5 |
| Top purchase channel | Store, then Web, then Catalogue |
| Top product category | Wine, then Meat |

### Highlights

- **Only about 1 in 7 customers responded** to the latest campaign. 1,883 did not respond, so the opportunity is reaching more of the *right* customers, not simply more customers.
- **Volume vs value:** Campaign 4 reached the most customers, but Campaign 5 customers spend the most on average. Volume alone is not enough to judge a campaign.
- **Responders are more valuable:** they spend roughly 82% more on average. This is an association, not proof the campaign caused the extra spend.
- **Stores and wine lead the business:** store purchases have the highest order volume, and wine is the top revenue category, followed by meat.

### CAC and ROAS

| Measure | Value |
|---|---|
| Contact cost per customer | 3.00 |
| CAC per responder | 3.00 |
| ROAS on responders | 3.67 (3,663 response revenue) |

> **Read with caution:** the 3.00 CAC counts only responders' contact cost. Contacting all 2,216 customers at an assumed 3.00 each costs about 6,648, which puts **blended CAC near 19.96 and ROAS near 0.55** against 3,663 of response revenue.

### Customer Tiers

| Tier | Total spend | Suggested action |
|---|---|---|
| High value | 1,500 or more | Protect and reward with loyalty perks and early access |
| Medium value | 500 to 1,499 | Grow through wine and meat cross-sell bundles |
| Low value | Under 500 | Use low-cost channels and test before heavy spend |

## Business Recommendations

1. **Target by value:** prioritise high-value customers and look-alikes of Campaign 5 responders.
2. **Learn from Campaign 4:** replicate what drove its reach; redesign or retire Campaign 2.
3. **Lead with wine and meat:** build offers and bundles around the two biggest categories.
4. **Strengthen the store:** keep stores as the anchor; use web and catalogue to cross-sell.
5. **Cut wasted contact cost:** suppress low-propensity customers and track blended CAC.

## Limitations

- **Association, not causation:** responders spend more, but the data cannot show the campaign caused it.
- **Partial cost picture:** CAC covers responders only, and contact cost per customer is a single fixed value.
- **No channel-level spend:** channels are compared by orders, so true channel ROI cannot be calculated.
- **Inconsistent figures:** response rate (15.03% vs 14.91%) and average spend differ slightly between queries.
- **Fixed tier thresholds:** the 500 and 1,500 cut-offs are rules of thumb, not tested.
- **Single snapshot:** no time trend, so seasonality and campaign timing are not captured.

## Next Steps

1. **Reconcile the numbers:** align response rate and average spend across queries.
2. **Test true lift:** run a holdout test to measure what campaigns actually cause.
3. **Score customers:** build a response score within each value tier.
4. **Track real CAC:** report CAC and ROAS on all contacted customers, by channel.

## SQL Skills Demonstrated

- **Aggregation:** `SUM`, `COUNT`, `AVG` and `GROUP BY` to size revenue and response
- **Data validation:** `COUNT` checks to confirm complete records
- **CTEs and `UNION ALL`:** step-by-step queries and side-by-side campaign comparison
- **`CASE` segmentation:** rule-based high, medium and low value tiers
- **Safe calculations:** `COALESCE` and `NULLIF` to avoid divide-by-zero in CAC and ROAS
- **Business analysis:** turning metrics into findings and recommendations

*November 2026*

