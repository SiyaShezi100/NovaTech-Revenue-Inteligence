docs/
│   ├── verification-log.md
CRM Deals:
<img width="1600" height="900" alt="01_CRM_SPICE_499_Rows_20_Columns png" src="https://github.com/user-attachments/assets/65c0e4c6-ae47-45b7-91bc-1d4e021f1bda" />

  • 499 rows ✅
  • 20 columns ✅
  • 85 unique accounts ✅
 
Marketing:
<img width="1600" height="900" alt="02_Marketing_SPICE_2240_Rows_20_Columns png" src="https://github.com/user-attachments/assets/ac38556f-e4a2-4701-9d03-1d72fd586d45" />

  • 2,240 rows ✅
  • 20 columns ✅
  • 24 nulls in annual_income ✅
 
Support:
<img width="1600" height="900" alt="03_Support_SPICE_3000_Rows_20_Columns png" src="https://github.com/user-attachments/assets/e8e76bd1-abeb-4b17-860c-8a5a1b4d6d6b" />

  • 3,000 rows ✅
  • 20 columns ✅
  • 59 nulls in ticket_resolved_date ✅
 
Unified:
<img width="1600" height="900" alt="05_Unified_Dataset_Join_Diagram png" src="https://github.com/user-attachments/assets/f623a5dd-7850-4bea-be99-b0ff8e3f50fe" />
<img width="1600" height="900" alt="06_Unified_Dataset_Join_Configuration png" src="https://github.com/user-attachments/assets/1bbfe2f1-f311-4801-ac3a-b5c38c3a1bc6" />
<img width="1600" height="900" alt="07_Unified_Dataset_Join_Configuration png" src="https://github.com/user-attachments/assets/432f8db0-f3a1-481b-ba51-bb2d8ea27d27" />
<img width="1600" height="900" alt="07_Unified_Dataset_SPICE_Success png" src="https://github.com/user-attachments/assets/46e88991-71e7-489f-87f3-11c4abb4587b" />
  • LEFT JOIN configuration ✅
  • account_id join key ✅
  • All 85 accounts linked ✅







│   ├── q-exploration-log.md
# NovaTech Revenue Intelligence — Q Exploration Log

## Entry 1 — Marketing

### Question
Which campaign source has the highest conversion rate?

### Q Response
Based on the Marketing Funnel sheet from the Novatech Revenue Intelligence dashboard, Direct Mail has the highest conversion (response) rate among all campaign channels.
Here's the full ranking:
| Campaign Channel | Response Rate |
|---|---|
| **Direct Mail** | **53.0%** |
| Paid Social | 40.3% |
| Partner Referral | 34.3% |
| Organic Search | 14.5% |
| Email | 8.7% |
Interestingly, while Direct Mail leads in conversion rate at 53.0%, it generates the fewest total leads (149). In contrast, Partner Referral drives the most leads (807) but has a moderate conversion rate of 34.3%

### Dashboard Verification
Verified against the Marketing Funnel sheet using campaign channel, response/conversion metrics and attributed revenue.

---

## Entry 2 — Marketing

### Question
Which marketing channel generated the highest attributed revenue?

### Q Response
Based on the Marketing Funnel sheet from the Novatech Revenue Intelligence dashboard, the NovaPulse Launch campaign generated the highest attributed revenue at $394,156.59 — accounting for about 35% of the total $1,127,223.09. Here's the full breakdown by campaign:
| Campaign Name | Attributed Revenue | % of Total |
|---|---|---|
| **NovaPulse Launch** | **$394,156.59** | **35.0%** |
| Digital Retarget | $196,249.17 | 17.4% |
| Enterprise Expansion | $194,356.76 | 17.2% |
| Year-End Accelerator | $174,765.73 | 15.5% |
| Q3 Growth Sprint | $133,415.20 | 11.8% |
| NovaEdge Awareness | $34,279.64 | 3.0% |
NovaPulse Launch generated nearly double the revenue of the next closest campaign (Digital Retarget), while NovaEdge Awareness contributed the least at just $34,279.64.

### Dashboard Verification
Verified against the Marketing Funnel revenue-by-channel visual. 

---

## Entry 3 — Sales

### Question
What's our win rate for deals sourced from Partner Referral?

### Q Response
The win rate for deals sourced from Partner Referral is 64.78% — with 241 won out of 372 total deals.
This was calculated by identifying accounts that had at least one marketing campaign record with the Partner Referral channel, then looking at the deal outcomes for those accounts. Notably, this is significantly higher than the overall win rate of ~35.2%, suggesting that Partner Referral is a highly effective source for generating winnable deals.

### Dashboard Verification
Verified against the Sales Pipeline deal outcome and win-rate analysis.

---

## Entry 4 — Customer Health

### Question
Which product area has the longest average resolution time?

### Q Response
Data Pipeline has the longest average resolution time at approximately 1.99 days. That said, all six product areas are remarkably close in resolution time, spanning a narrow range of just 0.09 days:
| Product Area | Avg Resolution (Days) |
|---|---|
| **Data Pipeline** | **1.99** |
| Mobile App | 1.98 |
| Analytics Dashboard | 1.96 |
| Billing | 1.94 |
| Notifications | 1.93 |
| Authentication | 1.90 |

### Dashboard Verification
Verified against the Customer Health resolution-time visual by product area.

---

## Entry 5 — Cross-Dataset

### Question
What is the average deal size for accounts with more than 3 support tickets in the last 30 days?

### Q Response
The average deal size for accounts with more than 3 support tickets in the last 30 days is $1,430.34.

This was calculated by identifying accounts in the support tickets data where tickets_last_30_days > 3, then computing the average deal value for those accounts from the CRM deals data.

For context, the overall average deal value across all accounts is ~$1,417.24, so high-ticket accounts have a slightly higher average deal size — suggesting that larger or more active accounts tend to generate more support volume.

### Dashboard Verification
Verified using CRM deal value and Support ticket activity linked through account_id.



│   ├── vp-sarah-chen-report.md
Executive Report for VP Sarah Chen
1. Executive Overview

NovaTech Solutions requires an integrated view of revenue performance across marketing, sales and customer support. The Revenue Intelligence Dashboard was developed in Amazon Quick to combine these business perspectives and enable management to investigate campaign effectiveness, sales performance and customer health.

The solution uses CRM Deals, Marketing Campaigns and Support Tickets data linked through the shared account_id identifier.

2. Data Strategy

The project uses three primary business datasets:

CRM Deals — sales opportunities, deal outcomes, representatives, regions, products and deal value.
Marketing Campaigns — campaign channels, funnel stages, campaign spend, responses and attributed revenue.
Support Tickets — ticket activity, priorities, product areas, resolution times and customer sentiment.

A unified dataset was also created by joining the three sources through account_id, satisfying the requirement for a consolidated analytical view.

3. Dashboard Design Rationale

The dashboard is divided into three sheets.

Marketing Funnel

The Marketing Funnel evaluates campaign response, funnel progression, attributed revenue and channel performance.

Sales Pipeline

The Sales Pipeline provides visibility into deal outcomes, revenue by region and product, sales performance and win-rate trends.

Customer Health

The Customer Health sheet combines ticket volume, resolution time, product-area issues and customer sentiment to identify potential customer risks.

Interactive filters allow users to investigate specific regions, products, customer segments, accounts and other business dimensions.

4. Topic / AI Effects

Baseline natural-language questions were tested before Topic configuration. The same questions were subsequently asked after configuring the NovaTech Revenue Intelligence Topic.

The Topic defined relationships between the CRM, Marketing and Support datasets and supplied business rules for metrics such as win rate, Marketing ROI and days to close.

This improved the analytical context available to the natural-language experience, particularly for questions requiring information from multiple business domains.

5. Key Business Insights

The dashboard enables management to investigate:

Which marketing channels produce the strongest response and revenue performance.
Which regions, products and sales representatives contribute most to sales performance.
Where deals are being lost and which loss reasons require attention.
Which product areas create the greatest support burden.
Which customers may require attention based on ticket activity and sentiment.
How customer support activity can be evaluated alongside account revenue.
6. AI Comparison

The baseline Q&A results demonstrated the limitations of asking natural-language questions without the project-specific Topic context.

After Topic configuration, the AI was provided with:

Dataset relationships
Field meanings
Business definitions
Cross-dataset rules
Metric definitions
account_id as the common identifier

The before-and-after screenshots provide evidence of how the Topic changed the Q&A experience.

7. Management Recommendation

NovaTech management should use the dashboard as a recurring revenue intelligence tool. Marketing performance should be monitored alongside sales conversion, while customer support signals should be incorporated into account-level reviews.

The combination of revenue, sales activity and customer health provides a more complete view than evaluating each business function independently.












│ executive-summary.md
Marketing Funnel 
The sheet provides a comprehensive overview of marketing campaign performance, tracking 2,240 
leads, 609 responses, and $1,127,223.09 in attributed revenue across multiple campaigns and 
channels. 

• Direct Mail achieves the highest response rate at 0.53, outperforming Paid Social (0.4) and 
Partner Referral (0.34), despite Partner Referral generating the most leads at 807. 
• NovaPulse Launch dominates attributed revenue at $394,156.59, accounting for roughly 35% 
of total revenue. 
• All campaigns show negative Marketing ROI, totaling -2,023.65, signaling widespread 
underperformance. 
• Qualified Lead is the largest funnel stage with 848 records, followed by Lead (465) and 
Closed Won (412). 

Sales Pipeline 
The sheet provides a comprehensive sales pipeline overview, tracking 499 total deals with metrics on 
revenue, deal values, closure times, win rates, and loss reasons across multiple products and sales 
representatives. 
• Of 499 total deals, 315 were won, generating a Total Won Revenue of 707,201 with an 
Average Deal Value of 1,417.24 and an average of 66.76 days to close. 
• NovaPulse Starter leads in deal volume with 118 deals, while NovaPulse Ultimate has the 
highest Average Deal Value despite <a href="c13efbe0-744e-4fcf-966d
e3d244ff8b62_</completion> 
• The top loss reasons—No Decision Made (43) and Poor Product Fit (43)—are tied, suggesting 
opportunities to improve product alignment and buyer engagement. 
• Grace Adeyemi leads win rate performance at 3,592.83, while Anya Petrov trails at 395.43, 
revealing significant variation across sales representatives. 

Customer Health 
The sheet provides an overview of customer support ticket performance, analyzing resolution times 
by priority, customer sentiment distribution, and issue volumes across product areas and accounts. 
• Resolution times are remarkably similar across priority levels—low (58.92 hours), high (57.62 
hours), and medium (57.49 hours)—suggesting priority has minimal impact on resolution 
speed. 
• Neutral sentiment dominates with 1,953 tickets, while negative tickets (684) significantly 
outnumber positive ones (304), highlighting a potential customer satisfaction concern. 
• Notifications (601), Analytics Dashboard (597), and Authentication (582) generate the most 
tickets, while Data Pipeline (310) and Billing (329) are notably lower. 







│   ├── data-architecture.md
│   └── topic-configuration.md
│
├── screenshots/
│   ├── 01-data/
│   ├── 02-data-transformation/
│   ├── 03-dashboard/
│   ├── 04-dashboard-interactions/
│   ├── 05-topic/
│   └── 06-q-baseline-after/
│       ├── before-topic/
│       └── after-topic/
│
└── submission/
    └── NovaTech_Revenue_Intelligence_Dashboard.pdf
