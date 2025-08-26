# 🧑‍💼 Profile Finder Chatbot

An intelligent chatbot that assists with **finding candidate profiles based on required skills**.  
This bot integrates with **Google Drive** for storing resumes/profiles, leverages **OpenAI embeddings** for semantic understanding, and uses **Pinecone** for efficient vector search.  
The bot is deployed with **n8n workflows** for automation and interacts with users via **Telegram Bot**.

## 🚀 Features
- 📂 Fetches candidate profiles stored in **Google Drive**
- 🔍 Converts resumes (PDF/DOCX) into embeddings using **OpenAI**
- 📊 Stores and searches embeddings efficiently with **Pinecone Vector DB**
- 🤖 Uses **OpenAI Chat Model** to understand queries and return relevant profiles
- 🔗 Automated workflows managed via **n8n**
- 💬 Integrated with **Telegram Bot** for easy access
- 🧑‍💼 Supports multi-format profiles (PDF, DOCX, text)

## 🛠️ Tech Stack
- **n8n** — Workflow automation  
- **OpenAI** — Embeddings & conversational responses  
- **Pinecone** — Vector DB for semantic search  
- **Telegram Bot API** — Messaging and interaction  
- **Google Drive API** — Resume/profile storage and retrieval  

## ⚙️ Architecture Flow

### 🔹 Workflow Diagram (Mermaid)
```mermaid
flowchart TD
    A[📂 Google Drive API] -->|Fetch Profiles| B[n8n Workflow]
    B -->|Extract Text & Preprocess| C[📝 Text Chunker]
    C -->|Convert to Embeddings| D[🔎 OpenAI Embeddings]
    D -->|Store & Search| E[📊 Pinecone Vector DB]
    E -->|Retrieve Matches| F[🤖 OpenAI Chat Model]
    F -->|Answer Generated| G[💬 Telegram Bot]
```

### 🔹 ASCII Flow
```
[Google Drive Profiles] --> [n8n Workflow] --> [Text Chunker] --> [OpenAI Embeddings] --> [Pinecone Vector DB]
                                                                                          |
                                                                                          v
                                                                               [OpenAI Chat Model] --> [Telegram Bot]
```

## 📦 Setup Instructions

### 1) Clone Repository
```bash
git clone https://github.com/anuradha2504/Profile-Finder-Chatbot-N8N/edit/main
cd profile-finder-chatbot
```

### 2) Environment Variables
Create a `.env` file in the project root:
```
OPENAI_API_KEY=your_openai_key
OPENAI_EMBEDDING_MODEL=text-embedding-3-small
PINECONE_API_KEY=your_pinecone_key
PINECONE_ENVIRONMENT=your_pinecone_env
PINECONE_INDEX=profile-finder
GOOGLE_DRIVE_API_KEY=your_gdrive_key
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
```

### 3) Setup n8n
1. Install n8n (Docker, desktop, or server).  
2. Import the workflow JSON: `workflows/profile_finder.json`.  
3. Configure credentials for Google Drive, Pinecone, OpenAI, and Telegram.  

### 4) Deploy Pinecone Index
- Create index (e.g., `profile-finder`).  
- Dimension = `1536`.  

### 5) Run the Bot
```bash
n8n start
```

## 📌 Example Usage
- **User (Telegram):** “which candidate has SQL knowledge?”  
- **Bot:** The candidate with SQL knowledge is Gajanan Sathe  

- **User (Telegram):** “Do we have any profile with Python?
”  
- **Bot:** Sorry! I can't find relevant information about any profile with Python knowledge from the knowledge base.

## 🛠️ Troubleshooting
- **Profiles not retrieved:** Check Google Drive API connection.  
- **Bot not responding:** Verify Telegram bot token in n8n.  
- **No profile matches:** Ensure profiles are processed and stored in Pinecone.  
- **Dimension mismatch error:** Ensure Pinecone index matches embedding model.  

---

# 👨‍💻 Author
Built by **Anuradha Kumari** using automation, AI, and profile search integrations.
