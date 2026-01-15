# Setup Guide (Expense Tracker AI Agent)

## 1) Google Sheet
Create a Google Sheet with these headers:
Date | Description | Amount | Type (Income/Expense) | Remaining Balance

## 2) n8n Credentials
- Add OpenAI credential
- Add Google Sheets credential (same Google account as the sheet)
- Add Gmail credential

## 3) Import Workflow
Import: `workflows/expense-tracker-ai-agent.json`

## 4) Test
Try:
- “I made 3000”
- “Paid 600 for electricity”
Confirm:
- Rows appear in Google Sheets
- Gmail alert triggers when balance <= 0
