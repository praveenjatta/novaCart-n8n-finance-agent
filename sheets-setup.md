# Google Sheets Setup — NovaCart Finance Agent

## Spreadsheet Name
`NovaCart_Financial_Data`

---

## Tab 1 — Monthly_Financials

This is the main data source. Add one row per month.

### Column Headers
| Column | Type | Description |
|--------|------|-------------|
| month | Text | Month name (e.g. "January 2026") |
| revenue | Number | Total gross revenue for the month |
| expenses | Number | Total operating expenses for the month |
| net_profit | Number | Net profit (=revenue-expenses) |
| notes | Text | Notable events or context for the month |

### Sample Data
| month | revenue | expenses | net_profit | notes |
|-------|---------|----------|------------|-------|
| April 2026 | 142000 | 98000 | 44000 | Strong Q1 close |
| May 2026 | 138500 | 102000 | 36500 | Marketing spend increased |
| June 2026 | 155000 | 99500 | 55500 | New product launch |

### Notes
- No empty rows between data rows
- Keep month format consistent
- net_profit can use formula: `=B2-C2`

---

## Tab 2 — Config (Optional)

Store configuration values here for easy updates.

### Column Headers
| Column | Type | Description |
|--------|------|-------------|
| key | Text | Config parameter name |
| value | Text | Config parameter value |

### Sample Data
| key | value |
|-----|-------|
| company_name | NovaCart |
| report_recipient | jattaaihq@gmail.com |
| slack_channel | #finance-reports |
| currency | USD |
| fiscal_year_start | January |

---

## Setup Instructions

1. Create a new Google Sheet named `NovaCart_Financial_Data`
2. Create two tabs: `Monthly_Financials` and `Config`
3. Add the column headers exactly as shown above (case-sensitive)
4. Populate with your financial data
5. Share the sheet with your Google account connected to n8n
6. Copy the **Spreadsheet ID** from the URL:
   `https://docs.google.com/spreadsheets/d/[SPREADSHEET_ID]/edit`
7. Paste the Spreadsheet ID into the Google Sheets nodes in n8n

---

## n8n Node Mapping

| n8n Node | Sheet Tab | Columns Read |
|----------|-----------|--------------|
| Load Current Month | Monthly_Financials | All columns, last row |
| Load Previous Month | Monthly_Financials | All columns, second to last row |
