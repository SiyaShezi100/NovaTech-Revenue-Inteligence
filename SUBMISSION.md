docs/
## verification-log.md
CRM Deals:
  • 499 rows ✅
  • 20 columns ✅
  • 85 unique accounts ✅
 
Marketing:
  • 2,240 rows ✅
  • 20 columns ✅
  • 24 nulls in annual_income ✅
 
Support:
  • 3,000 rows ✅
  • 20 columns ✅
  • 59 nulls in ticket_resolved_date ✅
 
Unified:
  • LEFT JOIN configuration ✅
  • account_id join key ✅
  • All 85 accounts linked ✅




# NovaTech Revenue Intelligence — Q Exploration Log

## Entry 1 — Marketing

### Question
Which campaign source has the highest conversion rate?

## Q-Response
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



vp-sarah-chen-report.md
## Executive-Report-fo-VP-Sarah-Chen
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
Marketing
2,240 leads
609 responses
$1,127,223.09 attributed revenue
Direct Mail response rate: 53.0%
Partner Referral: 807 leads
NovaPulse Launch: $394,156.59 attributed revenue
Sales
499 total deals
315 won
$707,201 total won revenue
Average deal value: $1,417.24
Average days to close: 66.76
Customer Health
3,000 support tickets
1,953 neutral
684 negative
304 positive
Notifications: 601 tickets
Analytics Dashboard: 597
Authentication: 582











## executive-summary.md
Marketing Funnel
The sheet provides a comprehensive marketing performance dashboard tracking 2,240 leads across campaigns, channels, funnel stages, and attributed revenue totaling 1,127,223.09.

Direct Mail achieves the highest response rate at 0.53, outperforming Paid Social (0.4) and Partner Referral (0.34), yet Partner Referral drives the most leads at 807.

NovaPulse Launch dominates attributed revenue at 394,156.59, accounting for over a third of total revenue, while NovaEdge Awareness contributes the least at 34,279.64.

All campaigns show negative Marketing ROI, totaling -2,023.65, indicating widespread underperformance despite strong lead volume.

Qualified Lead is the largest funnel stage with 848 records, followed by Lead (465) and Closed Won (412). 

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







## data-architecture.md
Data Architecture
Overview

The NovaTech Revenue Intelligence Dashboard integrates three business data sources:

CRM Deals
Marketing Campaigns
Support Tickets

The objective is to provide a unified view of revenue generation, sales performance, and customer health.

Source Datasets
CRM Deals

The CRM Deals dataset serves as the primary business dataset and contains:

Opportunity information
Deal outcomes
Deal values
Sales representatives
Products
Regions
Close dates

Dataset Statistics:

499 rows
20 columns
85 unique accounts
Marketing Campaigns

The Marketing Campaigns dataset contains marketing performance information including:

Campaign names
Campaign channels
Funnel stages
Campaign spend
Lead responses
Attributed revenue

Dataset Statistics:

2,240 rows
20 columns
24 null values in annual_income
Support Tickets

The Support Tickets dataset contains customer support activity and service metrics including:

Ticket priority
Product area
Resolution dates
Customer sentiment
Ticket activity

Dataset Statistics:

3,000 rows
20 columns
59 null values in ticket_resolved_date
Dataset Integration Strategy

All datasets were connected using the common field:

account_id

The CRM Deals dataset was used as the primary dataset.

A LEFT JOIN strategy was implemented to ensure all deal records remained available in the unified model.

Join Key:

account_id

Join Type:

LEFT JOIN

Validation Results:

All 85 accounts successfully linked
Unified dataset created successfully
No account relationships were lost during integration
Unified Dataset Architecture

Marketing Campaigns
         |
         | account_id
         |
         v
 CRM Deals
         ^
         |
         | account_id
         |
 Support Tickets

Business Value

The unified dataset enables cross-functional analysis such as:

Marketing influence on sales outcomes
Campaign effectiveness and revenue attribution
Customer support activity by account
Relationship between customer health and revenue performance
Cross-dataset natural language queries using Amazon QuickSight Q

This architecture provides a single source of truth for revenue intelligence and customer analysis.


## topic-configuration.md
Topic Configuration
Topic Name

NovaTech Revenue Intelligence

Purpose

The NovaTech Revenue Intelligence Topic enables users to ask business questions using natural language across Marketing, Sales, and Customer Support data.

The topic was configured in Amazon QuickSight Q to improve the accuracy and context of question-and-answer interactions.

Datasets Included

The topic was built using the following datasets:

CRM Deals
Marketing Campaigns
Support Tickets
Dataset Relationships

The datasets are connected through a shared business identifier:

account_id

Relationship Structure:

Marketing Campaigns
         |
         | account_id
         |
         v
 CRM Deals
         ^
         |
         | account_id
         |
 Support Tickets

## Business-Definitions

The topic includes business-friendly descriptions and terminology to improve the natural language experience.

Examples include:

Win Rate
Deal Value
Closed Won Revenue
Attributed Revenue
Campaign Response Rate
Marketing ROI
Days to Close
Resolution Time
Customer Sentiment
Calculated Metrics

The topic supports analysis of several calculated metrics, including:

Win Rate

Won Deals / Total Deals

Average Deal Value

Total Deal Value / Total Deals

Marketing ROI

(Attributed Revenue - Campaign Spend) / Campaign Spend

Days to Close

Close Date - Created Date

Resolution Time

Resolved Date - Created Date

Q Validation Questions

The topic was validated using business questions across multiple domains.

Marketing
Which campaign source has the highest conversion rate?
Which marketing channel generated the highest attributed revenue?
Sales
What is the win rate for deals sourced from Partner Referral?
Customer Health
Which product area has the longest average resolution time?
Cross-Dataset Analysis
What is the average deal size for accounts with more than three support tickets in the last 30 days?
Benefits of Topic Configuration

Configuring the topic provides:

Improved Q&A accuracy
Better business terminology recognition
Enhanced cross-dataset analysis
Consistent metric definitions
Easier access to insights through natural language
Outcome

The NovaTech Revenue Intelligence Topic successfully enabled business users to explore marketing, sales, and customer support data through natural language questions while leveraging relationships established through the account_id field.



## screenshots
## 01-data
<img width="1600" height="900" alt="01_CRM_SPICE_499_Rows_20_Columns png" src="https://github.com/user-attachments/assets/65c0e4c6-ae47-45b7-91bc-1d4e021f1bda" />
<img width="1600" height="900" alt="02_Marketing_SPICE_2240_Rows_20_Columns png" src="https://github.com/user-attachments/assets/ac38556f-e4a2-4701-9d03-1d72fd586d45" />
<img width="1600" height="900" alt="03_Support_SPICE_3000_Rows_20_Columns png" src="https://github.com/user-attachments/assets/e8e76bd1-abeb-4b17-860c-8a5a1b4d6d6b" />
<img width="1600" height="900" alt="04_Data_Type_Correction png" src="https://github.com/user-attachments/assets/13fabae7-cf17-4fb4-aff2-ff1ebf8b0ec5" />
## Calculated-Fields
<img width="1600" height="900" alt="08_Calculated_Fields png" src="https://github.com/user-attachments/assets/71d46f8a-714f-4b23-91d3-851d887356d2" />
<img width="1600" height="900" alt="09_Calculated_Fields png" src="https://github.com/user-attachments/assets/12a83285-1a37-4d79-a1cd-16f37ff321a9" />
<img width="1600" height="900" alt="10_Calculated_Fields png" src="https://github.com/user-attachments/assets/d20c5829-d9ab-45ac-8429-451f2b2223b5" />
## Marketing -Funnel-KPIs
<img width="1600" height="900" alt="09_Marketing_Filter_Controls png" src="https://github.com/user-attachments/assets/f3a73fbf-7add-424d-a81f-d68b7db431cf" />
<img width="1600" height="900" alt="MARKETING FUNNEL KPI" src="https://github.com/user-attachments/assets/05a4b5a5-9444-43c2-b900-931c7efa4a11" />
<img width="1600" height="900" alt="MARKETING FUNNEL KPI2" src="https://github.com/user-attachments/assets/424291d3-9431-426d-b7a2-f709f6a80b98" />
<img width="1600" height="900" alt="MARKETING FUNNEL KPI3" src="https://github.com/user-attachments/assets/d16699f6-d3b9-47ae-9eb1-985083db870a" />


## 02-data-transformation
<img width="1600" height="900" alt="05_Unified_Dataset_Join_Diagram png" src="https://github.com/user-attachments/assets/f623a5dd-7850-4bea-be99-b0ff8e3f50fe" />
<img width="1600" height="900" alt="06_Unified_Dataset_Join_Configuration png" src="https://github.com/user-attachments/assets/1bbfe2f1-f311-4801-ac3a-b5c38c3a1bc6" />
<img width="1600" height="900" alt="07_Unified_Dataset_Join_Configuration png" src="https://github.com/user-attachments/assets/432f8db0-f3a1-481b-ba51-bb2d8ea27d27" />
<img width="1600" height="900" alt="07_Unified_Dataset_SPICE_Success png" src="https://github.com/user-attachments/assets/46e88991-71e7-489f-87f3-11c4abb4587b" />



## 03-dashboard
## Annotations
<img width="1600" height="900" alt="Customer Health Annotation" src="https://github.com/user-attachments/assets/6b41df6e-73af-468e-a783-e899133f3eb9" />
<img width="1600" height="900" alt="Marketing Funnel Annotation" src="https://github.com/user-attachments/assets/dd319c1e-0270-4d0b-a5a9-310a8a327d53" />
<img width="1600" height="900" alt="Sales Pipeline Annotation" src="https://github.com/user-attachments/assets/4a9fd9f4-5f08-4dd3-b3e7-6dee5bbf5404" />

<img width="1600" height="900" alt="09_Marketing_Filter_Controls png" src="https://github.com/user-attachments/assets/8d2cf4e6-730c-46f3-8e74-9d4441772ee0" />
<img width="1600" height="900" alt="MARKETING FUNNEL KPI" src="https://github.com/user-attachments/assets/86d71bff-24d5-4a85-af77-1a4ca9ab7535" />
<img width="1600" height="900" alt="MARKETING FUNNEL KPI2" src="https://github.com/user-attachments/assets/2cf9d39f-2204-4c3b-86c2-6844c7d4037d" />
<img width="1600" height="900" alt="MARKETING FUNNEL KPI3" src="https://github.com/user-attachments/assets/0943451f-77a5-4c03-8d5c-225d0345a034" />


## 04-dashboard-interactions
<img width="1600" height="900" alt="11_One_Click_Filter_Action png" src="https://github.com/user-attachments/assets/7a69cbf8-d912-40c2-be0b-319d1c8db1dd" />
<img width="1600" height="900" alt="12_One_Click_Filter_Working png" src="https://github.com/user-attachments/assets/d57af2e5-2b5a-41d4-8862-4ae974a3e146" />
## Dashboard-KPIs
<img width="1600" height="900" alt="Open Support Tickets 7" src="https://github.com/user-attachments/assets/cfc0fa82-bdc1-44e2-9d12-5ad01fa00c84" />
<img width="1600" height="900" alt="Open Support Tickets 9" src="https://github.com/user-attachments/assets/6c0b3ec2-3b71-4199-b1be-4a277dd0ca1c" />
<img width="1600" height="900" alt="Open Support Tickets KPI" src="https://github.com/user-attachments/assets/97d4ba40-a0fd-439b-8c9e-6715c0b32d79" />
<img width="1600" height="900" alt="Open Support Tickets2" src="https://github.com/user-attachments/assets/def68e8d-d616-4c27-a1f3-afeba217426f" />
<img width="1600" height="900" alt="Open Support Tickets3" src="https://github.com/user-attachments/assets/01215158-653a-4cb1-8c41-b0c98939b661" />
<img width="1600" height="900" alt="Open Support Tickets4" src="https://github.com/user-attachments/assets/8ae1622e-48d7-456b-87c8-00da00032dab" />
<img width="1600" height="900" alt="Open Support Tickets6" src="https://github.com/user-attachments/assets/9838bc35-da4e-4eff-9e9c-17ca62a0e316" />
<img width="1600" height="900" alt="Open Support Ticktes8" src="https://github.com/user-attachments/assets/63d004e2-c754-41d7-95de-c3c11e75c25c" />


## 05-topic
<img width="1600" height="900" alt="21_Topic_Configuration png" src="https://github.com/user-attachments/assets/c76e9510-7c92-42a9-9c60-248a47b1cfb8" />

## 06-q-baseline-after
## before-topic
<img width="1600" height="900" alt="18_Q_Baseline_Marketing png" src="https://github.com/user-attachments/assets/f8bb6f15-1cd6-460c-b2af-b7fa9bf75514" />
<img width="1600" height="900" alt="20_Q_Baseline_Customer_Health png" src="https://github.com/user-attachments/assets/35d8f1e6-a4f7-4be0-bacf-a9d2d3ea04de" />
<img width="1600" height="900" alt="Basekine Sales" src="https://github.com/user-attachments/assets/3e08a4f9-bb3e-4f90-a6dd-4ad566d01619" />

## after-topic
<img width="1600" height="900" alt="18_Q_Baseline_Marketing png1" src="https://github.com/user-attachments/assets/056a8a04-c3f2-41b4-9af6-6acf1df2f474" />
<img width="1600" height="900" alt="19_Q_Baseline_Sales png2" src="https://github.com/user-attachments/assets/ee80e57b-ff65-4b3b-aed6-b3b5f395b438" />
<img width="1600" height="900" alt="20_Q_Baseline_Customer_Health png2" src="https://github.com/user-attachments/assets/3f829745-dfb7-47e1-83f0-b48b08916d84" />


## submission
NovaTech_Revenue_Intelligence_Dashboard.pdf
    
[NovaTech Dashboard combined Doc.pdf](https://github.com/user-attachments/files/32326673/NovaTech.Dashboard.combined.Doc.pdf)

## Dashboard-Summary 
## Marketing-Funnel 
The sheet provides a comprehensive overview of marketing campaign performance, 
tracking 2,240 leads across multiple channels, attributed revenue of 1,127,223.09, 
response rates, funnel stages, and marketing ROI. 
Partner Referral generated the most leads (807), yet Direct Mail achieved the highest 
response rate (0.53), suggesting different channels excel at different funnel objectives. 
NovaPulse Launch drove the highest attributed revenue at 394,156.59, capturing over a 
third of total revenue, while NovaEdge Awareness contributed the least at 34,279.64. 
All campaigns show negative Marketing ROI, totaling -2,023.65, indicating widespread 
underperformance despite generating 609 total response flags. 
Most deals recorded zero won revenue (184 out of 499 records), highlighting significant 
conversion challenges across the funnel. 

## Sales-Pipeline 
The sheet provides a comprehensive sales performance dashboard tracking deal 
outcomes, revenue, product performance, and sales representative effectiveness across 
499 total deals. 
Of 499 deals, 315 were won, generating a Total Won Revenue of 707,201 with an Average 
Deal Value of 1,417.24. 
NovaPulse Starter led in volume with 118 deals, while NovaPulse Ultimate commanded 
the highest Average Deal Value at 2,658,800%. 
The top loss reasons were "No Decision Made" and "Poor Product Fit" at 43 opportunities 
each, followed by "Competitor Won" with 34. 
Average Days to Close was 66.76, with dramatic variation over time—ranging from 1 day on 
Nov 5, 2024 to 177 days on Jan 5, 2025. 

## Customer-Health 
The sheet provides an overview of customer support ticket metrics, analyzing resolution 
times, customer sentiment, product area distribution, and account-level ticket volumes 
across 3,000 total tickets. 
Resolution times are nearly identical across priority levels, with low at 58.92 hours, high at 
57.62 hours, and medium at 57.49 hours, suggesting priority level has little impact on 
resolution speed. 
Neutral sentiment dominates with 1,953 tickets, while negative tickets (684) far exceed 
positive ones (304), highlighting opportunities for customer experience improvement. 
Notifications (601) and Analytics Dashboard (597) generate the most issues, while Data 
Pipeline (310) and Billing (329) report the fewest.








    
