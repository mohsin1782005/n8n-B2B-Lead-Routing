# Automated B2B Lead Filtering & Email Notification System
## Overview
This repository contains the workflow architecture and JSON blueprint for an automated B2B lead routing pipeline built in **n8n**. 

The system is designed to replace manual data entry and monitoring for sales teams. It actively listens for incoming lead data, processes each entry through custom conditional logic, and dispatches dynamic notifications for high-priority prospects.

## Workflow Architecture
1. **Trigger (Google Sheets API):** Actively monitors a designated spreadsheet for new rows of lead data.
2. **Logic Node (IF Condition):** Evaluates the incoming data batch and filters leads based on business rules (e.g., `Status = 'Ready'`).
3. **Action Node (Gmail API):** Generates and sends a dynamically formatted email (or Slack message) containing the specific lead's Name, Company, Email, and Score.

## Key Features
* **Zero Lead Leakage:** Ensures 100% of qualified leads are immediately sent to the sales team.
* **Dynamic Formatting:** Uses variable mapping `{{$json.Value}}` to customize notification outputs.
* **Scalable Routing:** The logic nodes can be easily expanded to route different lead tiers to different departments.

## How to Deploy
You can deploy this exact workflow to your own n8n instance in minutes:
1. Download the `n8n-workflow-blueprint.json` file from this repository.
2. Open your n8n workspace and select **Import from File** in the top right workflow menu.
3. Once imported, connect your own Google Account credentials to the Trigger Node and your Gmail/SMTP credentials to the Action Node.
4. Point the Trigger node to your specific lead tracking spreadsheet.
5. Click **Publish** to make the automation live.

## Tech Stack
* **n8n** (Core Automation Engine)
* **REST APIs & Webhooks**
* **Google Sheets API**
* **Gmail/SMTP Node**
* **JSON / JavaScript** (Data mapping)
