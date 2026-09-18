# NovaTech Revenue Intelligence Dashboard

An AWS Amazon Quick revenue intelligence solution integrating CRM, Marketing, and Customer Support data to provide management with a unified view of revenue performance, sales outcomes, marketing activity, and customer health.

---

## Project Overview

NovaTech Solutions is a mid-sized B2B SaaS company that requires a more efficient way to understand revenue performance across Marketing, Sales, and Customer Support.

The project addresses the challenge of manually combining information from multiple business systems for management reporting and decision-making.

The NovaTech Revenue Intelligence Dashboard brings these business areas together through AWS Amazon Quick and provides interactive dashboards and natural-language analysis.

### Project Objectives

The main objectives of the project are to:

- Consolidate CRM, Marketing, and Support data.
- Provide management with a unified view of revenue performance.
- Analyse sales pipeline and deal outcomes.
- Evaluate marketing campaign performance.
- Monitor customer support activity and customer sentiment.
- Identify potential customer-risk indicators.
- Provide interactive dashboard analysis.
- Enable natural-language business questions through Quick Topics.
- Support management decision-making using verified dashboard information.

---

# Business Questions

The dashboard was designed to answer key business questions across three areas.

## Marketing

- Which campaign source has the highest conversion rate?
- Which marketing channels generate the strongest response rates?
- Which campaigns generate the most attributed revenue?
- How does campaign performance change over time?
- Which customer segments respond most strongly to campaigns?
- What is the marketing ROI by campaign and channel?

## Sales

- What is the overall sales win rate?
- What is the win rate by sales region?
- What is the win rate by sales representative?
- What is the win rate by product?
- What are the main reasons for lost deals?
- What is the average deal value?
- How long does it take to close deals?
- How much revenue has been generated from won deals?

## Customer Health

- Which accounts have high support activity?
- Which accounts have negative customer sentiment?
- Which product areas generate the most support tickets?
- Which priority levels have the longest resolution times?
- Which customer accounts may require additional attention?
- How can support activity be analysed alongside account revenue?

---

# Data Sources

The project uses three primary datasets.

## 1. CRM Deals

**File:** `novatech_crm_deals.csv`

- Rows: **499**
- Columns: **20**
- Date range: June 2023 – January 2025
- Primary business area: Sales

Important fields include:

- `account_id`
- `company_name`
- `industry`
- `company_size_tier`
- `annual_revenue_usd`
- `employee_count`
- `opportunity_id`
- `sales_rep`
- `sales_manager`
- `sales_region`
- `product_name`
- `product_category`
- `list_price`
- `deal_stage`
- `deal_created_date`
- `deal_closed_date`
- `deal_value`
- `loss_reason`

The CRM dataset is the authoritative source for deal outcomes, deal value, sales representatives, sales regions, products, win rate, and days to close.

---

## 2. Marketing Campaigns

**File:** `novatech_marketing_campaigns.csv`

- Rows: **2,240**
- Columns: **20**
- Date range: January 2023 – January 2025
- Primary business area: Marketing

Important fields include:

- `account_id`
- `campaign_name`
- `campaign_channel`
- `campaign_date`
- `funnel_stage`
- `customer_segment`
- `campaign_spend`
- `revenue_attributed`
- `campaign_response`

The Marketing dataset is the authoritative source for campaign performance, channels, responses, funnel stages, campaign spend, attributed revenue, and marketing ROI.

---

## 3. Support Tickets

**File:** `novatech_support_tickets.csv`

- Rows: **3,000**
- Columns: **20**
- Date range: June 2023 – February 2025
- Primary business area: Customer Support

Important fields include:

- `account_id`
- `ticket_created_date`
- `ticket_resolved_date`
- `priority`
- `product_area`
- `customer_tier`
- `region`
- `customer_sentiment`
- `tickets_last_30_days`

The Support dataset is the authoritative source for support activity, ticket volume, priority, resolution time, product areas, customer sentiment, and recent ticket volume.

---

# Data Architecture

The three datasets share the common business key:

account_id

The CRM Deals dataset is used as the primary sales anchor.

The unified data model connects:
CRM Deals
     |
     | account_id
     |
     +--------------------+
     |                    |
     v                    v
Marketing Campaigns   Support Tickets

The project uses the CRM Deals dataset as the anchor and connects Marketing Campaigns and Support Tickets through account_id.

LEFT JOIN logic is used so that CRM account information remains available even when corresponding Marketing or Support records are unavailable.

| Dataset             |     Rows |  Columns |
| ------------------- | -------: | -------: |
| CRM Deals           |      499 |       20 |
| Marketing Campaigns |    2,240 |       20 |
| Support Tickets     |    3,000 |       20 |
| Unified Dataset     | Combined | Combined |

Data preparation included:

CSV dataset imports.
SPICE verification.
Data type correction.
Join configuration.
Unified dataset creation.
Calculated fields.
Validation of dataset row and column counts.

Dashboard

The project contains three primary dashboard sheets:

Marketing Funnel
Sales Pipeline
Customer Health
1. Marketing Funnel

The Marketing Funnel provides an overview of campaign activity and marketing performance.

Key metrics and visuals

The sheet analyses:

Campaign volume.
Campaign response rate.
Campaign channel performance.
Funnel stages.
Attributed revenue.
Campaign spend.
Marketing ROI.
Customer segment performance.
Key Marketing Findings

The Marketing dataset contains:

2,240 campaign records
609 responses
$1,127,223.09 attributed revenue

Direct Mail recorded an observed response rate of:

53.0%

The dashboard allows management to investigate campaign performance by channel, campaign, funnel stage, customer segment, and date.

2. Sales Pipeline

The Sales Pipeline provides an overview of deal outcomes, revenue, sales performance, and sales-cycle information.

Key metrics and visuals

The sheet analyses:

Total deals.
Won deals.
Lost deals.
Win rate.
Won revenue.
Average deal value.
Average days to close.
Deal outcomes.
Loss reasons.
Revenue by product.
Win rate by region.
Win rate by representative.
Product performance.
Verified Sales Results

The CRM contains:

499 total deals
315 won deals
184 lost deals
63.13% overall win rate
$707,201 total won revenue
$1,417.24 average deal value
66.76 average days to close

3. Customer Health

The Customer Health sheet combines customer support activity with account and revenue information to support customer-risk analysis.

Key metrics and visuals

The sheet analyses:

Total support tickets.
Customer sentiment.
Ticket volume.
Support priority.
Product area.
Resolution time.
Customer account activity.
Account revenue.
Recent ticket volume.
Potential customer-risk indicators.
Customer Health Findings

The Support dataset contains:

3,000 support tickets
684 negative sentiment records
1,953 neutral sentiment records
304 positive sentiment records

The most frequently recorded product areas include:

Notifications
Analytics Dashboard
Authentication

The dashboard allows management to investigate customer support activity at account, product-area, priority, region, and customer-tier levels.

Dashboard Interactivity

The dashboard includes interactive controls and actions across multiple sheets.

Filter Controls
Marketing Funnel includes interactive campaign/channel filtering.
Sales Pipeline includes interactive region/product/deal-stage filtering.
Customer Health includes customer support and account-level filtering.
One-Click Filtering

One-click filtering is configured on dashboard visuals to allow users to select a data point and cascade the selection to multiple visuals on the same sheet.

Cross-Sheet Navigation

A navigation action allows users to move from Sales Pipeline to Customer Health for deeper customer-level investigation.

Customer Health Unified View

The Customer Health sheet includes a unified-data customer risk view combining account, revenue, support activity, sentiment and priority information.

Dashboard Drill-Down Hierarchies

The dashboard supports drill-down analysis.

Marketing
Campaign Channel
        ↓
Campaign Name
        ↓
Funnel Stage
Sales
Sales Region
        ↓
Sales Manager
        ↓
Sales Representative
        ↓
Product
Customer Health
Region
   ↓
Account
   ↓
Product Area
   ↓
Priority

These drill-downs allow users to move from high-level management information to more detailed operational information.

Topic / Natural-Language Analysis

A Quick Topic was configured to provide natural-language access to the NovaTech datasets.

Topic Name
NovaTech Revenue Intelligence
Topic Datasets

The Topic uses:

CRM Deals
Marketing Campaigns
Support Tickets

The datasets are connected through:

account_id
Topic Custom Instructions

The Topic uses business-specific instructions to improve the interpretation of questions.

This Topic represents NovaTech Solutions' revenue intelligence data.
CRM Deals contains sales opportunities and final deal outcomes.
Marketing Campaigns contains campaign interactions and funnel stages.
Support Tickets contains customer support activity.
The common account identifier is account_id.

Use CRM Deals as the authoritative source for deal outcomes, deal value, sales representatives, sales regions, products, win rate and days to close.

Use Marketing Campaigns as the authoritative source for campaign performance, channel, response, funnel stage, campaign spend, attributed revenue and marketing ROI.

Use Support Tickets as the authoritative source for ticket volume, priority, resolution time, product area, customer sentiment and tickets in the previous 30 days.

When answering cross-dataset questions, connect datasets through account_id.

Do not sum duplicated deal values caused by multiple marketing or support records for the same account.

Win rate = Won Deals / Total Deals.

Marketing ROI = (revenue attributed - campaign spend) / campaign spend.

Days to close = deal closed date - deal created date.

Exclude unresolved support tickets from average resolution time calculations.
Natural-Language Questions Tested

Examples of questions tested using the Topic include:

Marketing

Which campaign source has the highest conversion rate?

Sales

What is our win rate for deals sourced from Partner Referral?

Customer Health

Which product area has the longest average resolution time?

Cross-Dataset Analysis

What is the average deal size for accounts with more than 3 support tickets in the last 30 days?

Customer Risk

Show me all Enterprise accounts with negative customer sentiment.

AI / Quick Validation

Natural-language analysis was tested both before and after Topic configuration.

The purpose of the comparison was to determine whether the Topic improved the AI's understanding of:

Dataset relationships.
Business terminology.
Relevant fields.
Cross-dataset questions.
Calculated metrics.

AI responses were compared against the dashboard rather than being treated as automatically correct.

Some questions produced useful results, while other responses did not always answer the requested analytical dimension.

For example, a campaign-level response may not directly answer a question requesting channel-level information.

Similarly, the overall sales win rate must be verified against the CRM data:

315 Won / 499 Total = 63.13%

This validation process demonstrates the importance of checking natural-language results against the underlying dashboard and source data.

Key Business Insights
Sales

NovaTech recorded 315 won deals out of 499 total deals, resulting in an overall win rate of approximately 63.13%.

Total won revenue recorded in the CRM is $707,201.

The average recorded deal value is $1,417.24, with an average time to close of 66.76 days.

Marketing

The Marketing dataset contains 2,240 records and 609 responses.

Direct Mail recorded the highest observed response rate at 53.0%.

Total attributed revenue recorded in the Marketing dataset is $1,127,223.09.

Customer Health

The Support dataset contains 3,000 tickets.

Negative sentiment accounts for 684 records, while neutral sentiment accounts for 1,953 records and positive sentiment accounts for 304 records.

The dashboard enables management to investigate support activity alongside account revenue, sentiment, priority, and product-area information.

Management Use Cases

The dashboard can support management activities including:

Revenue Management
Monitor won revenue.
Analyse deal outcomes.
Monitor win rates.
Investigate lost opportunities.
Compare sales performance.
Marketing Management
Compare campaign channels.
Monitor response rates.
Analyse campaign performance.
Review attributed revenue.
Investigate campaign ROI.
Customer Success
Identify high-support-volume accounts.
Monitor negative customer sentiment.
Analyse product-area issues.
Review resolution times.
Investigate customer-level risk indicators.
Stakeholder Recommendations

Based on the dashboard analysis, management can:

Review lost opportunities by region, representative, product, and loss reason.
Investigate the performance of marketing channels and campaigns using response rate and attributed revenue.
Monitor accounts with high support activity and negative customer sentiment.
Review support resolution times by priority and product area.
Use interactive filters and drill-downs to investigate changes in performance at account and operational levels.
Validate AI-generated responses against dashboard metrics before using them for management decisions.
