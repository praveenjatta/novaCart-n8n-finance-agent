# Agent Instructions — NovaCart Finance Agent

## Agent Overview
The NovaCart Finance Agent is an autonomous n8n workflow that generates and delivers monthly CFO-ready financial reports. It runs automatically on the 1st of every month at 8:00 AM, pulls data from Google Sheets, calculates KPIs, generates a structured narrative report using AI, and delivers it via Gmail and Slack.

---

## Workflow Logic

### Node 1 — Schedule Trigger
- Fires on the 1st of every month at 8:00 AM
- Timezone: America/Phoenix (GMT-07:00)

### Node 2 — Load Current Month Data (Google Sheets)
- Reads current month financial data from the "Monthly_Financials" tab
- Columns: month, revenue, expenses, net_profit, notes

### Node 3 — Load Previous Month Data (Google Sheets)
- Reads prior month row for MoM comparison
- Same sheet, previous month row

### Node 4 — Calculate KPIs (Code Node)
Calculates the following metrics:
- **Gross Revenue** — current month total revenue
- **Total Expenses** — current month total expenses
- **Net Profit** — revenue minus expenses
- **Profit Margin %** — (net_profit / revenue) × 100
- **MoM Revenue Change %** — ((current - previous) / previous) × 100
- **MoM Expense Change %** — ((current - previous) / previous) × 100
- **MoM Profit Change %** — ((current - previous) / previous) × 100

### Node 5 — Generate CFO Report (OpenAI)
**Model:** GPT-4  
**Prompt Template:**
```
You are a financial analyst preparing a monthly CFO report for NovaCart.

Financial Data:
- Month: {{month}}
- Revenue: ${{revenue}}
- Expenses: ${{expenses}}
- Net Profit: ${{net_profit}}
- Profit Margin: {{margin}}%
- MoM Revenue Change: {{mom_revenue}}%
- MoM Expense Change: {{mom_expenses}}%
- MoM Profit Change: {{mom_profit}}%
- Notes: {{notes}}

Generate a concise, professional CFO report with:
1. Executive Summary (2-3 sentences)
2. Key Financial Highlights (bullet points)
3. Month-over-Month Analysis
4. Risk Flags (if any metrics are negative or declining)
5. Recommended Actions

Keep the tone professional and data-driven. Plain text only, no HTML.
```

### Node 6 — Format Email Body (Code Node)
- Assembles the full email with header, KPI table, and AI-generated narrative
- Adds NovaCart branding and footer

### Node 7 — Send Gmail Report
- **To:** jattaaihq@gmail.com
- **Subject:** NovaCart Monthly CFO Report — {{month}} {{year}}
- **Body:** Full formatted report from Node 6
- **Account:** jattaaihq@gmail.com

### Node 8 — Format Slack Message (Code Node)
- Creates a concise Slack summary with key KPIs
- Includes emoji indicators (📈 up, 📉 down, ➡️ flat)

### Node 9 — Send Slack Notification
- **Channel:** #finance-reports
- **Message:** KPI summary with link to full report
- **Workspace:** JattaAI Slack

### Nodes 10–13 — Error Handling
- Catch any node failures
- Send error alert to jattaaihq@gmail.com
- Log error details with timestamp

---

## Credentials Required

| Credential | Type | Used In |
|------------|------|---------|
| Google Sheets OAuth2 | Google Account | Nodes 2, 3 |
| OpenAI API Key | API Key | Node 5 |
| Gmail OAuth2 | Google Account | Node 7 |
| Slack Webhook | Webhook URL | Node 9 |

---

## Trigger Schedule
- **Frequency:** Monthly
- **Day:** 1st of every month
- **Time:** 8:00 AM
- **Timezone:** America/Phoenix

---

## Output
- Gmail report delivered to CFO/finance team
- Slack notification in #finance-reports channel
- Full KPI breakdown with MoM trend analysis
