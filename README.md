# Automated Sales Follow-Up Alert (n8n)

## Overview
This workflow automatically sends follow-up reminder emails to sales representatives when new leads have not been contacted within 24 hours after being recorded.

Delayed first contact significantly reduces lead conversion rates. By enforcing a clear follow-up SLA, this workflow helps sales teams respond faster and avoid missed revenue opportunities.

While this implementation uses **Google Sheets** as the lead data source, the same logic can be adapted to CRM systems such as **HubSpot, Salesforce, or internal databases**.

---

## Business Use Case
Sales teams often manage leads across spreadsheets or CRMs, making it easy to overlook new inquiries—especially during high-volume periods.

This workflow ensures:
- No new lead is left unattended
- Sales accountability is enforced automatically
- Follow-up processes are standardized without manual checks

Each sales representative receives **one consolidated email** containing only the leads they are responsible for.

---

## Prerequisites
- A spreadsheet or database containing lead data  
- Required fields:
  - `lead_name`
  - `lead_email`
  - `lead_phone`
  - `sales_name`
  - `sales_email`
  - `created_at` / `lead_created_at` / `timestamp`
  - `lead_status` (Lead funnel stage)

---

## How It Works
1. The workflow runs on a scheduled interval using a **Schedule Trigger**
2. Lead data is fetched from the data source
3. Leads are filtered based on:
   - Lead status equals **"New"**
   - No contact activity within the last **24 hours**
4. Qualified leads are grouped by assigned sales representatives
5. A consolidated reminder email is sent to each sales rep containing:
   - Lead name
   - Email address
   - Phone number

---

## Customization Notes
- The follow-up time threshold can be adjusted by modifying the time comparison logic
- Lead status naming can be customized (e.g. **New**, **Contacted**, **Qualified**, **Lost**)
- The data source can be replaced with:
  - CRM integrations
  - Databases
  - API endpoints
- Email subject and body can be customized based on business tone or language

---

## Safeguards
- Leads without a valid `sales_email` are automatically excluded
- Grouping ensures each sales rep receives only **one email per workflow run**
- Filtering logic prevents alerts for already-contacted leads

---

## Limitations
- This workflow sends reminder notifications only
- It does not automatically update lead status or write back to the data source
- Timestamps are assumed to use a consistent timezone
- High-volume datasets may require batching or pagination

---

## Ideal For
- Sales Operations teams
- Marketing teams managing inbound leads
- Startups using spreadsheets before migrating to a CRM
- No-code / low-code automation scenarios

---

## Notes
This repository contains **workflow logic only**.  
All credentials (Google, Gmail, API keys, OAuth tokens) are **intentionally removed** for security reasons and must be configured individually by each user after importing the workflow.
