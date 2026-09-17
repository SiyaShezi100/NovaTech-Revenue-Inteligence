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

```text
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


