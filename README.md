# 📄 Automated Invoice Processing Workflow (n8n)

An automated **n8n** workflow that listens for new invoice PDFs uploaded to Google Drive, extracts key invoice details using **Google Gemini AI**, saves the data into **Google Sheets**, and notifies your team via **Gmail** using **OpenAI**.

---

## 🚀 How It Works

```
Google Drive (New PDF) 
   ⬇️
Extract Text from PDF
   ⬇️
Gemini AI (Extract Fields)
   ⬇️
Google Sheets (Save Record)
   ⬇️
OpenAI (Draft Notification)
   ⬇️
Gmail (Send to Billing Team)
```

1. **Google Drive Trigger**: Monitors a specific Google Drive folder every minute for newly uploaded invoice PDFs.
2. **Download & Extract**: Downloads the file and reads the raw text from the PDF.
3. **AI Information Extraction**: Uses **Google Gemini (2.0 Flash)** to automatically locate and extract structured invoice details.
4. **Save to Google Sheets**: Appends the extracted invoice details into your database spreadsheet.
5. **AI Email Generator**: Uses **OpenAI (GPT-4o-mini)** to generate a clean summary email for your internal billing team.
6. **Send Email**: Sends the notification via **Gmail** with invoice details and a direct link to the spreadsheet.

---

## 📋 Data Extracted from Invoices

The AI model automatically pulls the following fields from each invoice:

- **Invoice Number**
- **Client Name**
- **Client Email**
- **Client Address**
- **Client Phone Number**
- **Total Amount**
- **Invoice Date**
- **Due Date**

---

## 🛠️ Prerequisites

To run this workflow, you need credentials for:

- **n8n** (Cloud or self-hosted)
- **Google Drive** (OAuth2)
- **Google Sheets** (OAuth2)
- **Gmail** (OAuth2)
- **Google Gemini API** (PaLM / Gemini API key)
- **OpenAI API** (API key)

---

## ⚙️ Setup Instructions

### 1. Import Workflow
1. Open your n8n workspace.
2. Click **Add workflow** > **Import from File**.
3. Select `4) Invoice Workflow.json`.

### 2. Connect Your Credentials
Set up your accounts for each node:
- **Google Drive Trigger & Download Binary**: Connect your Google Drive OAuth2 account and select the folder where incoming invoices will be stored.
- **Google Gemini Chat Model**: Connect your Google Gemini API key.
- **Update DB (Google Sheets)**: Connect your Google Sheets account, choose your spreadsheet document, and select the target sheet tab.
- **Create Email (OpenAI)**: Connect your OpenAI API key.
- **Send Email (Gmail)**: Connect your Gmail account and update the `To` field (replace `billing@example.com` with your team's email).

### 3. Activate the Workflow
1. Test each node once using a sample invoice PDF.
2. Toggle the workflow switch to **Active**.

