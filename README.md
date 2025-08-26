# Profile Finder Chatbot - README

## Introduction
This chatbot is designed to search and retrieve candidate profiles from Google Drive based on the required skills.  
It leverages AI-powered embeddings and vector search for efficient profile matching.  
The chatbot is integrated with Telegram for user interaction and is triggered seamlessly via messages.

## Key Features
- **Profile Search:** Retrieves profiles stored in Google Drive based on required skills.  
- **Vector Search:** Uses Pinecone vector database for semantic search.  
- **AI Embeddings:** OpenAI embeddings are used to transform profiles and skill queries into vectors.  
- **Messaging:** Telegram integration allows easy chatbot interaction.  
- **Automation:** n8n workflows handle profile ingestion, updates, and search orchestration.  
- **AI Agent:** Ensures natural language understanding and smart query handling.  

## Tech Stack
- **n8n** - Workflow automation and orchestration.  
- **Pinecone** - Vector database for semantic search.  
- **OpenAI Embeddings** - For profile and query vectorization.  
- **OpenAI Chat Model** - For natural language conversation.  
- **Telegram** - User interaction and chatbot triggering.  
- **Google Drive** - Storage for candidate profiles.  

## Workflow
1. Profiles are stored in Google Drive (PDFs, Docs, or Text).  
2. n8n extracts and preprocesses profile data.  
3. Profiles are converted into embeddings using OpenAI and stored in Pinecone.  
4. User sends a skill query via Telegram chatbot.  
5. AI agent converts query into embedding and searches Pinecone for matches.  
6. Relevant profiles are retrieved and returned to the user in Telegram.  

## Setup Instructions
1. Set up Google Drive API and share profiles folder with the service account.  
2. Configure n8n workflows for profile ingestion and Telegram integration.  
3. Create a Pinecone index and connect it with n8n.  
4. Set up OpenAI API keys for embeddings and chat model.  
5. Deploy Telegram bot and connect with n8n webhook.  
6. Run workflow and test with different skill queries.  

## Future Enhancements
- Add ranking mechanism based on profile relevance score.  
- Support for multiple file formats (images with OCR).  
- Admin dashboard for monitoring queries and results.  
- Integration with ATS (Applicant Tracking Systems).  
