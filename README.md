# 🍽️ Tadka Tales - WhatsApp AI Food Ordering Assistant

An automated, AI-powered food ordering and customer support assistant built using **n8n**. This workflow connects a WhatsApp Business API trigger to an advanced LangChain AI Agent powered by Google Gemini, using Google Sheets as a lightweight CRM and inventory backend.

## 🚀 Features
- **Smart Greetings:** Dynamically welcomes users with a clean app-like menu structure.
- **Conversational Ordering:** Guides customers step-by-step through capturing their name, food item, and quantity.
- **Live Inventory Check:** The AI Agent queries a Google Sheet to confirm stock availability before confirming any order.
- **Automated Order Logging:** Appends successfully confirmed orders to an active Google Sheet tracking dashboard.
- **Instant Order Lookup:** Allows users to check live stock levels or verify their order status (Confirmed, Delayed, Delivered) via natural chat.
- **Contextual Memory:** Keeps track of the last 10 WhatsApp message exchanges to maintain conversational context.

## 🛠️ Architecture & Nodes Used
As shown in the n8n canvas:
1. **WhatsApp Trigger:** Listens for incoming customer messages.
2. **AI Agent (LangChain):** The brain processing instructions and executing conditional tool choices.
3. **Google Gemini Chat Model:** Advanced language model providing natural text generation.
4. **Window Buffer Memory:** Retains conversation context for smooth multi-turn ordering.
5. **Google Sheets Tools:** Three dedicated sub-tools acting as the database:
   - `Get FAQ`: Fetches delivery, timing, and policy answers.
   - `Get Inventory`: Reads real-time stock levels.
   - `Post Orders`: Appends finalized order logs.
6. **Send Message (WhatsApp):** Routes the final AI-generated response back to the customer's phone.

## 📋 Prerequisites
To deploy this workflow, you will need credentials for:
- An active **n8n instance** (Self-hosted or Cloud)
- **Meta/WhatsApp Business API** developer account (Permanent Token & Phone Number ID)
- **Google Cloud Console** (with Google Sheets API enabled via OAuth2)
- **Google AI Studio / PaLM API Key** (for Gemini)

## 📦 Installation & Setup
1. Clone this repository or download the `My workflow.json` file.
2. In your n8n dashboard, click **New Workflow** -> **Import from File** and select the `.json` file.
3. Configure your credentials inside n8n for:
   - Google Sheets OAuth2
   - Google Gemini API
   - WhatsApp API
4. Link your own copy of the Google Sheets template containing the sheets: `Food Inventory`, `FAQ`, and `Orders`.
5. Toggle the workflow to **Active** and configure your WhatsApp Webhook URL in your Meta Developer portal.
