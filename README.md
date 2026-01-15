# Expense Tracker AI Agent (n8n)

An AI-powered personal finance tracker built with **n8n AI Agent**.  
It accepts natural-language messages (example: “I made 3000”, “Paid 600 for electricity”), classifies each transaction as **Credit/Debit**, assigns a description/category, calculates a **running balance**, logs everything to **Google Sheets**, and sends a **Gmail alert** when the balance reaches zero or below.

## Features
- Natural language input via **Chat Trigger**
- **AI Agent** powered by **GPT-4.1-mini**
- Maintains continuity using **Simple Memory**
- Logs transactions to **Google Sheets**
- Sends “Bankruptcy Alert” email when balance is `<= 0`
- Timestamped transactions for auditability

## Workflow Overview
Nodes included:
- Chat Trigger (input)
- AI Agent (decision + tool choice)
- OpenAI Chat Model (GPT-4.1-mini)
- Simple Memory (context window)
- Google Sheets Tool (append row)
- Gmail Tool (send alert)

## Google Sheet Format
The tracker writes rows into a sheet with these columns:
- Date / Timestamp
- Description
- Amount
- Type (Income/Expense)
- Remaining Balance

## Example Inputs
- `I made 3000`
- `Paid 600 for electricity`
- `Crypto sales 3800`
- `House deposit 5900`
- `Bought a sofa 570`

## Logic (Agent Rules)
- Credit increases the balance
- Debit decreases the balance
- Every transaction is appended to Google Sheets
- If balance becomes **zero or negative**, send a Gmail alert:
  - Subject: `Bankruptcy Alert`
  - Message: `I'm bankrupt officially.`

## Setup
1. Create a Google Sheet with the required columns
2. Connect Google Sheets credentials in n8n
3. Connect Gmail credentials in n8n
4. Add your OpenAI API credentials in n8n
5. Import the workflow JSON from `workflows/expense-tracker-ai-agent.json`
6. Execute the workflow and test with sample inputs

## Screenshots
- Workflow: `images/workflow.png`
- Google Sheet output: `images/sheet-output.png`
- Gmail alert: `images/gmail-alert.png`

## Notes on Security
This repository does not include secrets (OpenAI key, Google/Gmail tokens).  
Credentials remain stored securely inside n8n.

## Author
Christian Ohwofasa


