 # Autonomous AI-Driven Content Curator & Notification Pipeline 🚀

An enterprise-grade, event-driven automation architecture designed to streamline social media content curation. This system autonomously ingests real-time technical journalism, filters complex payloads, prompts advanced generative models to structure production-ready content, and maintains a dual-layer logging and human-in-the-loop notification layout.

Built natively within an n8n orchestration engine containerized via Docker.

## 🛠️ System Architecture & Node Ledger

[ Schedule Trigger ] ➔ [ RSS Content Fetcher ] ➔ [ Payload Stream Processor ] ➔ [ AI Agent Engine ] ➔ [ Google Sheets Data Layer ] ➔ [ Discord Notification Layer ]
1. **Schedule Trigger**: Programmed to initiate the orchestration sequence completely headless every day at a specified cadence.
2. **RSS Content Fetcher**: Programmed to tap into real-time tech feeds (TechCrunch API endpoint) to scrape incoming articles and engineering updates.
3. **Payload Stream Processor (Limit Node)**: Truncates deep nested JSON arrays down to an isolated single item (`Max Items: 1`) to preserve bandwidth and mitigate upstream AI rate limiting.
4. **AI Agent Engine (Orchestrated Brain)**: Leverages an integrated `gemini-2.5-flash` language model module configured with automated failover retry logic to parse text snippets and format professional social media layouts.
5. **Google Sheets Data Layer**: Leverages a Google Cloud IAM Service Account using cryptographic JSON keys to cleanly map and append historical text logs onto cloud spreadsheets safely.
6. **Discord Notification Layer (HTTP Request)**: Uses optimized raw webhooks to package text variables securely via JSON payloads, instantly alerting the user's mobile or desktop application with a formatted draft ready for manual approval.

## 📈 Engineering Stack & Protocols
* **Orchestrator Engine**: n8n core (Self-Hosted on local system via Docker containerization)
* **Generative AI Layer**: Google Gemini Developers API (`gemini-2.5-flash`)
* **Target Destinations**: Google Sheets Workspace v4 REST API & Discord Developer Webhooks API
* **IAM & Security Protocol**: Role-Based Google Cloud Service Account (Cryptographic authentication bypassing interactive session expiration)

## 🚀 How to Replicate & Deploy Locally

1. Set up your local workspace instance via Docker Desktop command:
   ```bash
   docker run -d --name n8n -p 5678:5678 -v n8n_data:/home/node/.n8n n8nio/n8n
   ```
2. Create a public repository workspace, import the `My_workflow.json` configuration file directly into your local n8n workflow canvas.
3. Authenticate your personal Google Cloud Service Account JSON file into the credentials block.
4. Supply your target Discord text channel webhook URL  string inside the Notification node parameter panel, then switch the canvas global toggle from **Inactive** to **Published**! 
