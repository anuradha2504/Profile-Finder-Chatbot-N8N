# Profile Finder Chatbot - README

## Introduction
This chatbot is designed to search and retrieve candidate profiles from Google Drive based on the required skills.  
It leverages AI-powered embeddings and vector search for efficient profile matching.  
The chatbot is integrated with Telegram for user interaction and is triggered seamlessly via messages.

   # 🧑‍💼 Profile Search Chatbot

An intelligent chatbot that assists with **profile searching based on required skills**.  
This bot helps recruiters and hiring managers fetch relevant candidate profiles stored in **Google Drive**, leveraging **Pinecone**, **OpenAI**, and **Telegram** with an **n8n automation pipeline**.

## 🚀 Key Features
- 📂 Fetches candidate profiles stored in **Google Drive**
- 🔍 Converts profiles into embeddings using **OpenAI**
- 📊 Stores and searches embeddings efficiently with **Pinecone Vector DB**
- 🤖 Uses **OpenAI Chat Model** to provide contextual profile matching
- 🔗 Automated workflows managed via **n8n**
- 💬 Integrated with **Telegram Bot**
- 🧑‍💼 Retrieves candidate profiles based on skill queries

## 🛠️ Tech Stack
- **n8n** — Workflow automation  
- **OpenAI** — Embeddings & conversational responses  
- **Pinecone** — Vector DB for semantic search  
- **Telegram Bot API** — Messaging and interaction  
- **Google Drive API** — Profile storage and retrieval  

## ⚙️ Architecture Flow

## Workflow
1. Profiles are stored in Google Drive (PDFs, Docs, or Text).  
2. n8n extracts and preprocesses profile data.  
3. Profiles are converted into embeddings using OpenAI and stored in Pinecone.  
4. User sends a skill query via Telegram chatbot.  
5. AI agent converts query into embedding and searches Pinecone for matches.  
6. Relevant profiles are retrieved and returned to the user in Telegram.
   
flowchart TD
    A[📂 Google Drive API] -->|Fetch Profiles| B[n8n Workflow]
    B -->|Convert to Embeddings| C[🔎 OpenAI Embeddings]
    C -->|Store & Search| D[📊 Pinecone Vector DB]
    D -->|Retrieve Matches| E[🤖 OpenAI Chat Model]
    E -->|Answer Generated| F[💬 Telegram Bot]
🔹 ASCII Flow
less
Copy
Edit
[Google Drive Profiles] --> [n8n Workflow] --> [OpenAI Embeddings] --> [Pinecone Vector DB]
                                                                      |
                                                                      v
                                                           [OpenAI Chat Model] --> [Telegram Bot]
📦 Setup Instructions



## Setup Instructions

1) Clone Repository
bash
Copy
Edit
git clone https://github.com/your-repo/profile-search-chatbot.git
cd profile-search-chatbot
2) Environment Variables
Create a .env file in the project root:

ini
Copy
Edit
OPENAI_API_KEY=your_openai_key
OPENAI_EMBEDDING_MODEL=text-embedding-3-small
PINECONE_API_KEY=your_pinecone_key
PINECONE_ENVIRONMENT=your_pinecone_env
PINECONE_INDEX=profile-search-chatbot
GOOGLE_DRIVE_API_KEY=your_gdrive_key
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
3) Setup n8n
Install n8n (Docker, desktop, or server).

Import the workflow JSON: workflows/profile_search_chatbot.json.

Configure credentials for Google Drive, Pinecone, OpenAI, and Telegram.

4) Deploy Pinecone Index
Create index (e.g., profile-search-chatbot).

Dimension = 1536.

5) Run the Bot
bash
Copy
Edit
n8n start
📌 Example Usage
User (Telegram): “Find profiles with Python and SQL skills”

Bot: The following profiles match your query:

No  Match Found

User (Telegram): “which candidate has SQL knowledge?”

Bot: The following profiles match your query:

The candidate with SQL knowledge is Gajanan Sathe

🛠️ Troubleshooting
Profiles not retrieved: Check Google Drive API connection.

Bot not responding: Verify Telegram bot token in n8n.

No profile matches: Ensure profiles are processed and stored in Pinecone.

Dimension mismatch error: Ensure Pinecone index matches embedding model.

👨‍💻 Author
Built by Anuradha Kumari using automation, AI, and profile search integrations.

## Future Enhancements
- Add ranking mechanism based on profile relevance score.  
- Support for multiple file formats (images with OCR).  
- Admin dashboard for monitoring queries and results.  
- Integration with ATS (Applicant Tracking Systems).  
