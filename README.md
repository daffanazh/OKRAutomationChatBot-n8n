# Telegram AI Assistant with Dynamic Data Retrieval

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/04c64378-999d-43bc-bf6c-ce5cd54ba6c0" />

## Executive Summary
This project demonstrates an intelligent, automated Telegram bot built with **n8n**. It doesn't just chat—it routes user intents, retrieves live structured data from Google Sheets, processes it through custom JavaScript logic, and uses **Google Gemini AI** to generate context-aware responses. 

This architecture is ideal for businesses needing automated customer support, internal data querying, or self-serve information retrieval without human intervention.

## Business Value
* **Automated Triage:** Uses logic branching (`Switch` node) to filter and route messages, ensuring the AI only processes relevant queries, saving API costs.
* **Real-time Data Access:** Bridges conversational AI with live database records (Google Sheets).
* **Context-Aware Responses:** Transforms raw database rows into natural language using Gemini AI.
* **Instant Deployment:** Fully orchestrated in n8n, allowing rapid iterations and zero-downtime updates.

## System Architecture & Workflow Logic
This workflow is triggered by real-time incoming Telegram messages and follows a structured pipeline:

1. **Trigger (`Telegram Trigger`):** Listens for incoming user messages via Webhook.
2. **Intent Routing (`Switch`):** Evaluates the message payload. 
   * *Path 0:* Direct text response for standard/fallback commands.
   * *Path 1:* Complex queries requiring database lookup and AI processing.
3. **Data Retrieval (`Google Sheets`):** Fetches specific rows from the database based on the user's query context.
4. **Data Transformation (`Code - JavaScript`):** Parses and sanitizes the raw JSON payload from Google Sheets into a structured format for the AI.
5. **Context Merging (`Merge` & `Edit Fields`):** Combines the user's original query with the retrieved database context.
6. **AI Processing (`AI Agent - Google Gemini`):** Instructs the Gemini Chat Model to formulate a precise, human-like response based *strictly* on the provided database context.
7. **Delivery (`Telegram Send Message`):** Delivers the final AI-generated response back to the user.

## Tech Stack
* **Workflow Automation:** n8n (Node-based automation)
* **AI Engine:** Google Gemini Chat Model
* **Database:** Google Sheets API
* **Messaging Interface:** Telegram Bot API
* **Data Parsing:** Custom JavaScript

## Repository Structure
* `telegram-ai-assistant.json` - The raw n8n workflow file. To test this system, simply import this JSON file directly into your n8n canvas.

---
*Architected for scalability and automation. Open for freelance opportunities.*
