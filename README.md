# 🤖 NovaCart Finance Agent — Automated CFO Reporting with n8n

> An autonomous AI finance agent that generates and delivers monthly CFO-ready financial reports via Gmail and Slack — built with n8n, no code required.

---

## 📌 Overview

The **NovaCart Finance Agent** is a fully automated financial reporting pipeline built on [n8n](https://n8n.io). It runs on the 1st of every month at 8:00 AM, pulls financial data, generates a structured CFO report, and delivers it via Gmail and Slack — without any manual intervention.

This project was built as part of the **EdgeUp TPM Agentic AI Program** (Interview Kickstart) and demonstrates real-world agentic AI workflow design for enterprise finance operations.

---

## 🏗️ Architecture

```
Schedule Trigger (1st of month, 8AM)
        │
        ▼
Load Financial Data (Google Sheets)
        │
        ▼
Calculate KPIs (Revenue, Expenses, Net Profit, MoM Change)
        │
        ▼
Generate CFO Report (AI Text Generation)
        │
        ├──► Send Gmail Report (jattaaihq@gmail.com)
        │
        └──► Send Slack Notification (#finance-reports)
```

---

## 🔧 Tech Stack

| Tool | Purpose |
|------|---------|
| [n8n](https://n8n.io) | Workflow automation platform |
| Google Sheets | Financial data source |
| OpenAI GPT-4 | CFO report generation |
| Gmail | Email delivery |
| Slack | Real-time notification |

---

## 📊 Features

- ✅ **Fully Automated** — runs on schedule, zero manual steps
- ✅ **CFO-Ready Reports** — structured narrative with KPIs and variance analysis
- ✅ **Dual Delivery** — Gmail report + Slack alert in one pipeline
- ✅ **13-Node Workflow** — modular, maintainable, production-ready
- ✅ **Monthly Scheduling** — triggers on the 1st of every month at 8:00 AM
- ✅ **MoM Analysis** — month-over-month comparison with trend indicators

---

## 📁 Repository Structure

```
novaCart-n8n-finance-agent/
├── NovaCart_Finance_Agent_v1.json      # n8n workflow export
├── sample-data/
│   └── NovaCart_Financial_Data.xlsx    # Sample Google Sheet data
├── docs/
│   └── NovaCart_Finance_Agent_Project_Summary.pdf
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites
- n8n instance (cloud or self-hosted)
- Google Sheets with financial data
- OpenAI API key
- Gmail account connected to n8n
- Slack workspace with incoming webhook

### Setup Instructions

1. **Clone this repo**
```bash
git clone https://github.com/praveenjatta/novaCart-n8n-finance-agent.git
```

2. **Import the workflow**
   - Open your n8n instance
   - Go to **Workflows** → **Import from file**
   - Upload `NovaCart_Finance_Agent_v1.json`

3. **Configure credentials in n8n**
   - Google Sheets: connect your Google account
   - OpenAI: add your API key
   - Gmail: authenticate your Gmail account
   - Slack: add your webhook URL

4. **Set up Google Sheet**
   - Use the sample data file in `/sample-data/`
   - Update the Google Sheets node with your spreadsheet ID

5. **Activate the workflow**
   - Toggle the workflow to **Active**
   - It will trigger automatically on the 1st of every month at 8:00 AM

---

## 📧 Sample Output

**Gmail Report Subject:** `NovaCart Monthly CFO Report — June 2026`

**Slack Notification:** `#finance-reports` channel alert with KPI summary

---

## 🔗 Related Projects

| Project | Description | Repo |
|---------|-------------|------|
| NovaCart RAG Agent | AI knowledge agent with Pinecone vector search | [View](https://github.com/praveenjatta) |
| BankCo Retention Agent | Premium customer retention AI agent | [View](https://github.com/praveenjatta) |
| E-Commerce Checkout Agent | Incident detection and alerting agent | [View](https://github.com/praveenjatta) |

---

## 👤 Author

**Praveen Kumar Jatta**
- 🌐 [jattaai.com](https://jattaai.com)
- 💼 [LinkedIn](https://linkedin.com/in/praveenjatta)
- 🐙 [GitHub](https://github.com/praveenjatta)

> AI Automation Consultant | Technical Project Manager | EdgeUp Agentic AI Program

---

## 📄 License

MIT License — feel free to use, modify, and build on this project.

---

*Built with ❤️ by [JattaAI](https://jattaai.com) — AI Automation Consulting*
