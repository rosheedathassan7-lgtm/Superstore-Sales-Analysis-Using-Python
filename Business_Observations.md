# Business Observations – Superstore Sales Analysis

## 1. Executive Summary

This analysis examines the Superstore sales transactions from **03 Jan 2015 to 30 Dec 2018**. It focuses on monthly sales performance, product categories, regions, customer segments, and the relationship between discounts and profit.

- **Valid sales records analysed:** 9,994
- **Distinct orders:** 5,009
- **Total sales:** $2,297,200.86
- **Total profit:** $286,397.02
- **Overall profit margin:** 12.47%

Overall, the transaction records generated positive total profit. However, profitability varies considerably across product categories, regions, customer segments, and discount levels.

## 2. Data Quality and Preparation

### Findings from the uploaded CSV

- The file contains **10,296 rows** and **21 columns**.
- **0 exact duplicate rows** were detected across the full file.
- The `Order Date` column is missing in **302 rows**.
- Inspection shows these 302 rows are not ordinary sales transactions with only a missing date. They form a separate returns lookup section appended below the sales records: the values appear under the wrong sales-table column headings (for example, `Person`, `Region`, and `Returned` appear in the first two columns).
- The valid transaction section contains **9,994 sales rows**. The 302 rows without an order date were excluded from sales and monthly trend calculations.
- Valid order dates range from **03 Jan 2015** to **30 Dec 2018**.

**Important data-preparation note:** Do not describe these 302 rows simply as missing-date sales transactions. They appear to be a separate returns lookup table that has been appended to the sales data in a mismatched structure. If returns analysis is required, extract and clean that section separately rather than treating it as sales transaction rows.

## 3. Overall Sales and Profitability

- Total sales were **$2,297,200.86**.
- Total profit was **$286,397.02**.
- The overall profit margin was **12.47%**.
- **1,871 records (18.72%)** had negative profit.

**Business observation:** The dataset is profitable overall, but the number of loss-making transaction lines indicates that positive total profit does not mean every sale is profitable. The business should investigate the products, discount levels, and transaction conditions associated with losses.

## 4. Monthly Sales Performance

The monthly sales series contains **48 months**.

- Highest-sales month: **Nov 2018**, with sales of **$118,447.82**.
- Lowest-sales month: **Feb 2015**, with sales of **$4,519.89**.

Annual sales totals:

|   Order Date |      Sales |    Profit |
|-------------:|-----------:|----------:|
|         2015 | 484,247.50 | 49,543.97 |
|         2016 | 470,532.51 | 61,618.60 |
|         2017 | 609,205.60 | 81,795.17 |
|         2018 | 733,215.26 | 93,439.27 |

**Business observations:**

- Annual sales declined by **2.83%** in 2016 compared with 2015.
- Sales then increased by **29.47%** in 2017 and **20.36%** in 2018.
- The strongest annual sales total in the period was recorded in **2018**.

**Business implication:** The recovery and subsequent growth from 2017 to 2018 warrant further investigation. Management could compare the products, regions, customer segments, and promotional activities contributing to that growth. The monthly peak should also be checked against seasonality and order volume before being treated as a recurring pattern.

## 5. Product Category Performance

| Category        |      Sales |     Profit |   Profit Margin (%) |
|:----------------|-----------:|-----------:|--------------------:|
| Technology      | 836,154.03 | 145,454.95 |               17.40 |
| Furniture       | 741,999.80 |  18,451.27 |                2.49 |
| Office Supplies | 719,047.03 | 122,490.80 |               17.04 |

**Business observations:**

- **Technology** generated the highest sales (**$836,154.03**) and the highest profit (**$145,454.95**).
- **Office Supplies** generated the second-highest profit (**$122,490.80**), despite having the lowest sales total of the three categories.
- **Furniture** generated **$741,999.80** in sales but only **$18,451.27** in profit. Its profit margin was notably lower than the other two categories.

**Business implication:** Technology is a major contributor to both revenue and profit. Furniture deserves a closer profitability review, including its sub-categories, discounting, costs, and product mix.

## 6. Regional Performance

| Region   |      Sales |     Profit |   Profit Margin (%) |
|:---------|-----------:|-----------:|--------------------:|
| West     | 725,457.82 | 108,418.45 |               14.94 |
| East     | 678,781.24 |  91,522.78 |               13.48 |
| Central  | 501,239.89 |  39,706.36 |                7.92 |
| South    | 391,721.91 |  46,749.43 |               11.93 |

**Business observations:**

- The **West** recorded the highest sales (**$725,457.82**) and highest profit (**$108,418.45**).
- The **East** ranked second in both sales and profit.
- The **Central** region had the lowest profit margin (**7.92%**) among the four regions.
- The **South** recorded the lowest sales, while its profit exceeded Central's.

**Business implication:** The West provides a useful benchmark for the other regions. Central warrants further analysis to identify whether its lower margin is associated with discounting, product mix, or other transaction-level factors. The South's lower sales but higher profit than Central also shows why sales volume alone is not enough to evaluate regional performance.

## 7. Customer Segment Performance

| Segment     |        Sales |     Profit |   Profit Margin (%) |
|:------------|-------------:|-----------:|--------------------:|
| Consumer    | 1,161,401.34 | 134,119.21 |               11.55 |
| Corporate   |   706,146.37 |  91,979.13 |               13.03 |
| Home Office |   429,653.15 |  60,298.68 |               14.03 |

**Business observations:**

- **Consumer** customers contributed the highest sales (**$1,161,401.34**) and highest total profit (**$134,119.21**).
- **Corporate** ranked second in sales and profit.
- **Home Office** had the lowest sales total, but the highest profit margin (**14.03%**) among the three segments.

**Business implication:** The Consumer segment is important for scale and total contribution. Home Office may offer an opportunity to study higher-margin purchasing patterns and identify whether similar products or offers can be developed for other customer groups.

## 8. Discount vs Profit Analysis

At transaction-line level, the correlation between discount and profit was:

- **Pearson correlation:** -0.219
- **Spearman correlation:** -0.543

The negative values indicate an overall negative association between discount and profit in this dataset. This is an association, not proof that discounts alone caused lower profit.

Profit by discount level:

|   Discount |   Records |   Avg_Profit |   Total_Profit |
|-----------:|----------:|-------------:|---------------:|
|       0.00 |  4,798.00 |        66.90 |     320,987.60 |
|       0.10 |     94.00 |        96.06 |       9,029.18 |
|       0.15 |     52.00 |        27.29 |       1,418.99 |
|       0.20 |  3,657.00 |        24.70 |      90,337.31 |
|       0.30 |    227.00 |       -45.68 |     -10,369.28 |
|       0.32 |     27.00 |       -88.56 |      -2,391.14 |
|       0.40 |    206.00 |      -111.93 |     -23,057.05 |
|       0.45 |     11.00 |      -226.65 |      -2,493.11 |
|       0.50 |     66.00 |      -310.70 |     -20,506.43 |
|       0.60 |    138.00 |       -43.08 |      -5,944.66 |
|       0.70 |    418.00 |       -95.87 |     -40,075.36 |
|       0.80 |    300.00 |      -101.80 |     -30,539.04 |

**Business observations:**

- Records with no discount generated the largest total profit (**$320,987.60**).
- Discount levels of **30% and above** in this dataset generally show negative aggregate profit at the listed discount levels.
- The 70% discount group recorded total profit of **$-40,075.36**, while the 80% group recorded **$-30,539.04**.
- Discount groups contain different numbers of records and different sales values, so total profit should be interpreted alongside record count, average profit, and product mix.

**Business implication:** Review high-discount transactions and consider setting discount controls based on product margin and expected order value. Test discount campaigns against a suitable baseline before concluding that a particular discount causes losses.

## 9. Sub-Categories Requiring Attention

The five lowest-profit sub-categories are:

| Sub-Category   |      Sales |     Profit |
|:---------------|-----------:|-----------:|
| Tables         | 206,965.53 | -17,725.48 |
| Bookcases      | 114,880.00 |  -3,472.56 |
| Supplies       |  46,673.54 |  -1,189.10 |
| Fasteners      |   3,024.28 |     949.52 |
| Machines       | 189,238.63 |   3,384.76 |

**Business observation:** Tables recorded the largest aggregate loss (**$-17,725.48**), followed by Bookcases and Supplies. These sub-categories should be prioritised for a deeper review of discounting, pricing, costs, and product mix.

## 10. Recommendations

1. **Protect margins:** Review discount rules, especially for transactions with discounts of 30% or more, and assess profitability at product level before approving large discounts.
2. **Investigate Furniture:** Examine Furniture sub-categories, particularly Tables and Bookcases, to understand the sources of weak or negative profit.
3. **Learn from stronger regions:** Study the West's sales and profit performance and assess which practices may be transferable to other regions.
4. **Improve Central-region profitability:** Analyse Central-region discount levels, category mix, and loss-making products.
5. **Use segment-specific strategies:** Maintain the Consumer segment while studying the higher margin achieved by Home Office.
6. **Monitor monthly performance:** Track sales and profit together each month so that revenue growth is not mistaken for improved profitability.
7. **Separate data sources correctly:** Keep the returns lookup section separate from the sales transaction table and join it using order identifiers when performing returns analysis.

## 11. Limitations

- The returns lookup section is embedded in the uploaded CSV using a different structure. It was not included in the sales calculations in this report.
- The monthly analysis excludes rows without a valid order date; in this file, those rows appear to belong to the separate returns section rather than incomplete sales transactions.
- The discount-profit correlation describes association and does not establish causation.
- This report analyses the supplied dataset only. It does not include external business context, operating costs beyond the recorded profit field, or explanations for changes in customer demand.

## 12. Conclusion

The Superstore dataset records **$2,297,200.86** in sales and **$286,397.02** in profit across 9,994 valid transaction rows from 2015 to 2018. Technology, the West region, and the Consumer segment are the leading contributors to total sales. However, Furniture has a comparatively weak profit margin, Central has the lowest regional margin, and several sub-categories—including Tables and Bookcases—record aggregate losses. The negative relationship observed between discount and profit reinforces the need to monitor promotional activity carefully.

The key business priority is to grow sales while protecting profitability through better discount controls, product-level reviews, and ongoing monitoring of regional and customer-segment performance.
