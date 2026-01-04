# Automated Sales Follow-Up Alert (n8n)

## Overview
This workflow automatically sends reminder emails to sales representatives
when new leads have not been contacted within 24 hours.

Delayed follow-ups often reduce conversion rates.
This automation helps prevent lead neglect and standardizes sales response time.

## Business Problem
- Leads are collected but not always followed up promptly
- Sales managers have limited visibility into uncontacted leads
- Manual monitoring is time-consuming and error-prone

## Solution
A scheduled n8n workflow that:
- Fetches lead data from Google Sheets
- Filters leads with status "New" and no contact in the last 24 hours
- Groups leads by assigned sales representative
- Sends one consolidated reminder email per sales rep

## Tools Used
- n8n
- Google Sheets
- Gmail

## Workflow Logic
1. Schedule trigger runs daily
2. Lead data is fetched from Google Sheets
3. Leads older than 24 hours with status "New" are filtered
4. Leads are grouped by sales representative
5. Reminder emails are sent automatically

## Customization
- The 24-hour threshold can be adjusted
- Google Sheets can be replaced with CRM systems
- Email content can be customized

## Notes
This repository contains the workflow logic only.
Credentials are intentionally removed for security reasons.
