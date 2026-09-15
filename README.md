# NovaTech Revenue Intelligence Dashboard

> An AWS Amazon Quick revenue intelligence solution that brings together Marketing, Sales, and Customer Support data to provide management with a unified view of revenue performance and customer health.

## Project Overview

NovaTech Solutions previously relied on manual Monday reporting across three siloed business systems. This process required approximately one hour of manual reporting and made it difficult to answer cross-functional business questions quickly.

The NovaTech Revenue Intelligence Dashboard was developed using Amazon Quick to provide a centralized analytical view across:

- Marketing Campaigns
- CRM Sales Deals
- Customer Support

The project combines dashboard analytics, interactive filtering, cross-sheet navigation, natural-language Q&A, and a Topic-based semantic layer.

---

## Business Problem

NovaTech's Marketing, Sales, and Customer Support information was distributed across separate systems.

The dashboard was designed to reduce the dependency on manual reporting and enable management to answer important cross-functional questions from one analytical environment.

### Core Business Questions

The completed solution is designed to answer questions such as:

1. Which marketing campaign source has the highest conversion performance?
2. What is NovaTech's win rate for deals sourced from Partner Referral?
3. Which product area has the longest average support resolution time?

The solution also supports cross-functional account-level analysis using `account_id`.

---

# Data Architecture

The project uses three source datasets:

| Dataset | Rows | Columns | Business Purpose |
|---|---:|---:|---|
| CRM Deals | 499 | 20 | Sales opportunities, deal outcomes, revenue and sales performance |
| Marketing Campaigns | 2,240 | 20 | Campaign performance, funnel activity, spend and attributed revenue |
| Support Tickets | 3,000 | 20 | Support activity, resolution time, product issues and customer sentiment |

## Shared Key

The three datasets share:

`account_id`

CRM Deals was used as the anchor dataset.

The unified dataset was created using LEFT joins through `account_id` to connect:

```text
CRM Deals
    |
    | account_id
    |
    +----> Marketing Campaigns
    |
    | account_id
    |
    +----> Support Tickets
