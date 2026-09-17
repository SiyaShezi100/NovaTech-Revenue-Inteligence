# NovaTech Revenue Intelligence Dashboard

> An AWS Amazon Quick revenue intelligence solution integrating Marketing, Sales, and Customer Support data to provide management with a unified view of revenue performance and customer health.

## Project Overview

NovaTech Solutions is a mid-size B2B SaaS company that requires a more efficient way to understand revenue performance across Marketing, Sales, and Customer Support.

The project addresses the challenge of manually combining information from multiple siloed systems for management reporting.

The NovaTech Revenue Intelligence Dashboard brings these business areas together through AWS Amazon Quick and provides interactive dashboards and natural-language analysis.

## Business Questions

The solution focuses on three key business areas:

### Marketing

- Which campaign channels generate the strongest response?
- Which campaigns perform best?
- What is the campaign ROI?
- How does performance vary across funnel stages and customer segments?

### Sales

- What is the current sales pipeline and deal outcome distribution?
- What is the win rate across regions, sales representatives, and products?
- What are the main loss reasons?
- What are the average deal value and days to close?

### Customer Health

- Which accounts have high support activity?
- Which product areas generate the most support issues?
- What is the average resolution time?
- Which customers show negative sentiment and potential risk?

## Data Sources

The project uses three primary datasets:

| Dataset | Purpose | Records |
|---|---|---:|
| CRM Deals | Sales opportunities, deal outcomes, revenue and sales information | 499 |
| Marketing Campaigns | Campaign performance, funnel activity and attributed revenue | 2,240 |
| Support Tickets | Customer support activity, resolution and sentiment | 3,000 |

All three datasets contain the shared business key `account_id`.

## Data Architecture

CRM Deals is used as the primary/anchor dataset.

Marketing Campaigns and Support Tickets are connected through `account_id` using LEFT JOIN relationships.


Marketing Campaigns
        |
        | account_id
        v
    CRM Deals
        ^
        |
        | account_id
        |
Support Tickets


The unified dataset was created from the three sources and saved to SPICE.

The architecture preserves CRM accounts even when corresponding Marketing or Support records are not available.
Data Preparation

The datasets were imported into SPICE and verified for row and column counts.

Data types were reviewed and corrected where required.

Calculated fields were created to support analysis, including:

Days to Close
Won Deal Flag
Lost Deal Flag
Won Revenue
Marketing Response Flag
Resolution Hours

## Dashboard

The solution contains three dashboard sheets.

## 1. Marketing Funnel

The Marketing Funnel provides:

Marketing KPI summaries
Campaign performance
Channel performance
Funnel-stage analysis
Response-rate analysis
Attributed revenue
Marketing ROI
Interactive filters

## 2. Sales Pipeline

The Sales Pipeline provides:

Deal outcome KPIs
Won and Lost deal analysis
Revenue analysis
Win-rate analysis
Loss-reason analysis
Regional and representative performance
Product performance
Average deal value
Days-to-close analysis
Interactive filters

## 3. Customer Health

The Customer Health dashboard provides:

Support ticket KPIs
Ticket volume analysis
Customer sentiment
Priority analysis
Product-area analysis
Resolution-time analysis
Customer risk analysis
Account-level investigation
Dashboard Interactivity

## The dashboard includes interactive functionality including:

Filter controls
One-click filtering actions
Cross-sheet navigation
Drill-down analysis
Account-level analysis
Dashboard text annotations

## Topic and Natural-Language Analysis

A Quick Topic named NovaTech Revenue Intelligence was configured using:

CRM Deals
Marketing Campaigns
Support Tickets
The datasets are connected through account_id.

The Topic provides business context and metric definitions so users can ask natural-language questions across the NovaTech data.

## AI / Quick Evaluation

Baseline Quick Chat questions were captured before Topic configuration.

The same questions were then asked again after the Topic was configured and published.

The evaluation includes questions covering:

Marketing
Sales
Customer Health
Cross-functional analysis

The detailed Q Exploration Log is available in:

docs/q-exploration-log.md

## Key Business Insights

The dashboard provides management with visibility into:

Marketing response and campaign performance
Sales deal outcomes and revenue
Regional and representative sales performance
Customer support volume
Customer sentiment
Product-area support issues
Potential customer risk based on revenue, support activity and sentiment

The dashboard and supporting analysis allow management to investigate these areas interactively rather than relying on manually consolidated reports.

## Executive Reporting

A stakeholder report was prepared for VP Sarah Chen, covering:

Data strategy
Dashboard design rationale
Topic configuration
AI comparison
Key business insights
Management value

## Tools and Technologies
AWS Amazon Quick
SPICE
Quick Topics / Natural-Language Q&A
CSV datasets
GitHub
Data visualization and business intelligence techniques
Project Outcome

The NovaTech Revenue Intelligence Dashboard provides a centralized analytical solution for Marketing, Sales, and Customer Health.

The combination of interactive dashboards, unified data, SPICE, and natural-language Topic analysis gives management a structured way to investigate revenue performance, customer health, and business activity.

## Submission Evidence

All project evidence has been organized into folders according to the submission checklist.
