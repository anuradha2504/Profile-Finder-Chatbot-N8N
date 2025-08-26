# Profile-Finder-Chatbot-N8N

# 👤 Skill-Based Profile Finder Chatbot

An AI-powered chatbot that helps **find the right candidate profiles** based on required skills from a list of resumes/profiles stored in **Google Drive**.  
This chatbot leverages **Google Drive**, **Pinecone**, **OpenAI**, and **Telegram**, orchestrated with **n8n**.

## 🚀 Features
- 📂 Fetches resumes/profiles (PDF/Docs) from **Google Drive**
- 🔍 Extracts and embeds skills using **OpenAI Embeddings**
- 📊 Stores and searches profiles efficiently with **Pinecone Vector DB**
- 🤖 Matches required skills against stored profiles using **OpenAI Chat Model**
- 🔗 Automated workflows managed via **n8n**
- 💬 Provides results via **Telegram Bot**

## 🛠️ Tech Stack
- **n8n** — Workflow automation
- **OpenAI** — Embeddings & query handling
- **Pinecone** — Vector DB for semantic skill search
- **Telegram Bot API** — Messaging interface
- **Google Drive API** — Profile storage

## ⚙️ Architecture Flow

flowchart TD
    A[📂 Google Drive API] -->|Fetch Profiles| B[n8n Workflow]
    B -->|Convert to Embeddings| C[🔎 OpenAI Embeddings]
    C -->|Store & Search| D[📊 Pinecone Vector DB]
    D -->|Retrieve Matching Profiles| E[🤖 OpenAI Chat Model]
    E -->|Ranked Candidate Profiles| F[💬 Telegram Bot]
🔹 ASCII Flow

[Google Drive Profiles] --> [n8n Workflow] --> [OpenAI Embeddings] --> [Pinecone Vector DB]
                                                                                  |
                                                                                  v
                                                                    [OpenAI Chat Model] --> [Telegram Bot]
📦 Setup Instructions
1) Clone Repository
bash
Copy
Edit
git clone https://github.com/your-repo/skill-profile-finder-chatbot.git
cd skill-profile-finder-chatbot
2) Environment Variables
Create a .env file in the root:

ini
Copy
Edit
OPENAI_API_KEY=your_openai_key
OPENAI_EMBEDDING_MODEL=text-embedding-3-small
PINECONE_API_KEY=your_pinecone_key
PINECONE_ENVIRONMENT=your_pinecone_env
PINECONE_INDEX=skill-profile-finder
GOOGLE_DRIVE_API_KEY=your_gdrive_key
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
3) Setup n8n
Install n8n (via Docker, desktop, or self-hosted).

Import the workflow JSON: workflows/skill_profile_finder.json.

Configure credentials for Google Drive, Pinecone, OpenAI, and Telegram.

4) Deploy Pinecone Index
Create index (e.g., skill-profile-finder).

Dimension = 1536 (for text-embedding-3-small).

5) Run the Bot
bash
Copy
Edit
n8n start
Now users can send skill queries to the Telegram bot and get matched profiles.

📌 Example Usage
User (Telegram): “Find me profiles with Python and SQL skills.”

Bot: Fetches profiles → Searches embeddings → Returns list of candidates.

User (Telegram): “Who has experience in Data Engineering and Snowflake?”

Bot: Extracts relevant profiles → Responds with ranked matches.

User (Telegram): “Show me resumes with AI + Machine Learning background.”

Bot: Retrieves and lists the profiles with matching experience.

🧩 How It Works (Step-by-Step)
Google Drive stores resumes/profiles (PDFs, Docs).

n8n fetches profiles and extracts text.

OpenAI Embeddings convert text into semantic vectors.

Pinecone stores vectors and performs similarity search.

OpenAI Chat Model interprets the user’s query and ranks profiles.

Telegram Bot delivers results instantly to users.

🛠️ Troubleshooting
No profiles found: Ensure resumes are uploaded in Google Drive.

Bot not responding: Verify Telegram bot token in n8n.

Index dimension mismatch: Check Pinecone index setup.

Wrong matches: Confirm that text extraction from profiles works correctly.

🔮 Future Enhancements
📅 Add candidate experience filtering (e.g., years of experience)

🎯 Rank profiles based on skill relevance score

🌍 Multi-language resume parsing

📊 Export matched profiles to CSV or Jira for HR tracking

👨‍💻 Author
Built by Anuradha Kumari using automation, AI, and workflow orchestration.
