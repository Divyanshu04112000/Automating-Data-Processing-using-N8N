# Automating-Data-Processing-using-N8N
📌 Overview
This workflow automates the process of fetching order data, filtering for processing orders, saving them to Airtable, calculating booking summaries, and sending weekly updates to a Discord channel.

⚙️ Workflow Components
Schedule Trigger

Runs weekly (every Monday at 9 AM).

Initiates the data fetch process.

HTTP Request

Sends a request to https://internal.users.n8n.cloud/webhook/custom-erp.

Uses HTTP Header Authentication with a unique ID.

IF Node

Filters incoming orders where orderStatus equals "processing".

Edit Fields

Extracts and maps orderID and employeeName for Airtable storage.

Airtable - Create a Record

Saves filtered order data to the processingOrders table in the Airtable base.

Code Node

Calculates:

totalBooked — total number of booked orders.

bookedSum — sum of all booked order prices.

Discord

Sends a formatted weekly summary message:

vbnet
Copy
Edit
This week we've X booked orders with a total value of Y. 
My Unique ID: <unique_id>
🛠️ Prerequisites
n8n instance

Airtable Personal Access Token

Discord Webhook URL

Custom ERP Webhook URL with authentication header

📂 Setup Instructions
Import this JSON workflow into your n8n instance.

Configure the following credentials:

httpHeaderAuth for the HTTP Request.

airtableTokenApi for Airtable integration.

discordWebhookApi for sending updates.

Adjust scheduling as needed in the Schedule Trigger node.

Update URLs, table IDs, and Airtable schema to match your environment.

🚀 Usage
Once activated, the workflow will:

Trigger automatically on schedule.

Fetch ERP data.

Filter for processing orders.

Save order details to Airtable.

Calculate and send a weekly report to Discord.

📜 License
This workflow is provided for educational and internal automation purposes.
