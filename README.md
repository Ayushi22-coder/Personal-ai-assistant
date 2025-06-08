AI Personal Assistant
Imagine a personal assistant in your pocket 📱 that handles your emails 📧, schedule 📅, to-do lists ✅, keeps you updated on Slack messages 💬, and performs online research for you 🔍—all through your favorite messaging app.

That's EXACTLY what this AI Personal Assistant does! 🤖✨

personal_assistant

This project provides a personal assistant agent that manages tasks related to your email inbox, calendar, Notion to-do list, Slack interactions, and handles any research you may have. The assistant communicates with you via your preferred communication channel (Telegram, Slack, or WhatsApp), keeping you informed about your schedule, tasks, emails, messages, and helping with research topics, people, or even companies.

The personal assistant is a hierarchical multi-agents system with a supervisor agent (manager) and several sub-agents that handle specific tasks and tools for efficient task management.

Overview
Main Agent: Assistant Manager
The Assistant Manager is your personal assistant that orchestrates the tasks and communication between you and the sub-agents. The manager is responsible for:

Receiving and analyzing your messages from your chosen communication channel.
Delegating tasks to the appropriate sub-agent (Email, Calendar, Notion, Slack, or Researcher).
Communicating updates, messages, and any queries back to you via your preferred channel.
Sub-Agents
The manager agent can communicate with five specialized sub-agents:

Email Agent: Can handle all your email-related tasks, including sending emails, retrieving specific emails, and checking for important messages from your contacts list.
Calendar Agent: Can manage your calendar by creating new events and retrieving and checking your scheduled events.
Notion Agent: Can manage your to-do list in Notion, helping you add, remove, or check tasks as needed.
Slack Agent: Can manage your Slack interactions by reading messages from channels or DMs and sending messages on your behalf.
Researcher Agent: Can perform web research, scrape websites, and gather information from LinkedIn profiles to assist with research tasks.
All the sub-agents report back to the Assistant Manager after completing their respective tasks.

Tech Stack
LangGraph & LangChain: Frameworks used for building the AI agents and interacting with LLMs (GPT-4, Llama 3, Gemini).
LangSmith: For monitoring the different LLM calls and AI agents' interactions.
Google APIs: Provides access to Google services like Calendar, Contacts, and Gmail.
Notion Client: Interface for interacting with Notion to manage and update to-do lists.
Slack SDK: For interacting with Slack, sending and receiving messages.
Tavily Search API: For performing web searches.
Telegram API: Depending on your choice of communication channel.
WhatsApp API via Twilio Sandbox (for testing): A way to integrate WhatsApp communication.
How to Run
Prerequisites
Python 3.9+
Your preferred LLM provider API keys (OpenAI, Claude, Gemini, Groq,...)
Google API credentials (for Calendar, Contacts, and Gmail access)
Notion API key
Tavily API key (for web research)
Slack Bot User OAuth Token and App Token
Telegram Bot Token (If you want to use telegram)
Twilio Account SID and Auth Token (If you want to test with WhatsApp)
Necessary Python libraries (listed in requirements.txt)
Setup
Clone the repository:

git clone https://github.com/kaymen99/AI-personal-assistant
cd AI-personal-assistant
Create and activate a virtual environment:

python -m venv venv
source venv/bin/activate  # On Windows use `venv\Scripts\activate`
Install the required packages:

pip install -r requirements.txt
Set up environment variables:

Create a .env file in the root directory of the project and add your API keys, see .env.example to know all the parameters you will need.

Configure Google API credentials:

Follow Google's documentation to set up credentials for Calendar, Contacts, and Gmail APIs. Save the credentials file in your project folder.

Set up Communication Channel:

Telegram:
Create a Telegram Bot: To interact with the assistant via Telegram, you will need to create a Telegram bot and obtain the bot token. Follow this guide to create your bot and get the necessary information.
Slack:
Create a Slack App: Follow the official Slack documentation to create a new Slack app, add the necessary OAuth scopes (refer to the provided code and documentation for the required scopes).
Install the app to your workspace and obtain your Bot User OAuth Token and App-Level Token.
WhatsApp (via Twilio Sandbox for Testing):
Important Note: Normally, interacting with the WhatsApp Business API requires a Meta Business Account. However, for testing purposes only, this project utilizes the Twilio WhatsApp Sandbox.
Twilio Sandbox Limitations: As stated in the Twilio documentation, "Use the Twilio Sandbox for WhatsApp for testing and discovery purposes only. You should not use it in production."
Setup:
Create a Twilio account and obtain your Account SID and Auth Token.
Follow Twilio's tutorial to set up the WhatsApp Sandbox: Twilio WhatsApp Sandbox Setup.
Save your Twilio Account SID, Auth Token and Sandbox number in your .env file.
Run the project:

For running the personal assistant on Slack or Telegram you'll only need to run:

python app.py
For running the personal assistant on whatsApp you'll need to run:

python run app_whatsapp.py
This will spin out a local fastAPI server, to enable the communication with the Twilio servers you need to make it public using Ngrok:

Expose the Webhook URL Using ngrok

ngrok http 5000
Configure Twilio Webhook

Go to the Twilio Console > Messaging > Sandbox for WhatsApp.
In the Sandbox settings section: Set the "WHEN A MESSAGE COMES IN" URL to your ngrok URL and save your configuration.
You're done now you can talk with your assistant via whatsApp

Usage
Communicating with the Assistant: Simply send a message to your configured communication channel (Telegram, Slack channel, or WhatsApp), and the assistant will analyze the message, delegate the tasks to the appropriate sub-agents, and report back to you with the results.
