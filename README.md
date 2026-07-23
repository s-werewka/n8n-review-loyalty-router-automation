# n8n-review-loyalty-router-automation
🚀 Automated Customer Feedback & Incident Management System
An automated system for collecting, analyzing, and managing customer feedback powered by n8n, OpenAI, Twilio, Google Sheets, and Telegram. The system automatically dispatches personalized post-visit surveys, analyzes satisfaction levels, categorizes negative feedback using AI, and alerts the team instantly on Telegram.

🌟 Key Features

•	Personalized SMS Messaging: Automated dispatch of survey links via Twilio with unique URL parameters.

•	Secure Data Transfer (Hidden Fields): Customer details pass seamlessly in the background across form steps.

•	AI-Powered Intelligence (OpenAI): Automated urgency evaluation, issue categorization, summary generation, and response drafting for team members.

•	Google Sheets Database: Logs feedback featuring an interactive dropdown menu to manage ticket statuses (New, In Progress, Completed).

•	Telegram Incident Alerts: Instant alerts sent to the team for 1–3★ ratings, featuring a full summary and quick-response capabilities.

•	Error Handling: A dedicated error-catching workflow (Error Trigger) that dispatches failure alerts to Telegram.

🔄 Modular Triggers & Flexibility
The system features a modular architecture. While initialized by email events (Gmail) by default, the n8n trigger can easily be swapped for:

•	Google Sheets Trigger: Runs automation when a new row is appended to a sheet.

•	Webhook / HTTP Request: Integrates with external CRMs, e-commerce platforms, or custom web apps.

•	Schedule Trigger: Periodically polls databases at specified time intervals.

•	Third-Party Integrations: Connects with Zapier, Typeform, PostgreSQL, HubSpot, Pipedrive, and more.


🛠️ System Architecture & Workflow

[Trigger (Gmail / Sheets / Webhook)] 
                 │
                 ▼
     [Twilio: Dispatch SMS Link]
                 │
                 ▼
     [n8n Form Submission Ingest]
                 │
                 ▼
           [Switch Node]
           /           \
   (4–5★ Rating)     (1–3★ Rating)
        │                  │
        ▼                  ▼
[Google Sheets Log]  [Detailed Feedback Form]
        │                  │
        ▼                  ▼
[Thank You Page]     [OpenAI Analysis Engine]
                           │
                           ▼
                   [Google Sheets Log]
                           │
                           ▼
                   [Telegram Alert]

	
	1.	Trigger: Event detection (Gmail / Google Sheets / HTTP Webhook).
	
	2.	Twilio: Generates and dispatches an SMS containing a unique survey link.
	
	3.	n8n Form Submission: Captures customer responses alongside hidden payload data (first_name, last_name, phone, visit_date).
	
	4.	Switch Node:

•	4–5★ (Positive): Direct log to Google Sheets and displays a thank-you page.

•	1–3★ (Negative): Redirects to a detailed issue report form.

	5.	OpenAI (GPT): Analyzes text input, determines urgency, categorizes the incident, and drafts a proposed reply.
	
	6.	Google Sheets: Logs complete data entries marked with status 🔴 New.
	
	7.	Telegram: Alerts team members with an incident summary and status management capabilities.


⚙️ Requirements & Configuration
	
	1.	n8n Instance (Cloud or Self-hosted).
	
	2.	API Accounts & Credentials:

•	OpenAI API Key

•	Twilio Account SID & Auth Token

•	Telegram Bot Token

•	Google Workspace (Google Sheets API)
	
	3.	Step-by-Step Setup:

•	Import the workflow.json file into your n8n instance.

•	Connect your Google, OpenAI, Twilio, and Telegram credentials.

•	Create a Google Sheet featuring matching columns and a Data Validation rule for the Status field.

•	Activate the dedicated error-handling workflow (Error Trigger) and link it in the primary workflow settings.
