# Shopify AI Customer Support System (RAG-Powered)

This repository contains a **Retrieval-Augmented Generation (RAG) AI system** for Shopify customer support, built using **n8n, Pinecone, OpenAI, and Google Drive, Lovable AI for rapid frontend work**.  
It automates receiving user queries, searching a vectorized knowledge base, generating AI answers, and sending email responses. It also automatically updates the knowledge base when new company data is added to Google Drive.


---

## 🚀 Features

- **n8n Workflow Automation**: Handles form submissions, AI processing, vector search, and email delivery.
- **RAG (Retrieval-Augmented Generation)**: Uses **Pinecone vector store** + **OpenAI embeddings** to provide accurate, context-aware answers with the help of Google Drive .
- **Email Notifications**: Automatically sends AI-generated responses to the user’s email.
- **Query Logging**: Saves all queries and responses in Google Sheets / Database for analytics.
- **Simple Memory**: Keeps track of user sessions to maintain context for multiple queries.

---


User submits a query via the form (Name, Email, Phone, Query).
Workflow triggers in n8n:
Query is converted into a vector embedding (OpenAI). Pinecone vector store retrieves relevant context.
AI Agent generates a precise answer using context and memory.
User receives an email:
Contains the AI-generated answer in a clean, structured format.
Includes company contact info and support hours.
Query is logged in Google Sheets / Database for future analysis.



You can see the sample pdf and text information of a company of mine name Shopify https://drive.google.com/drive/folders/1zNP3tyv7-iatC6rXlwDVqOpqQTsi9zCx?usp=sharing

## 📦 Tech Stack


- **n8n** – Workflow automation
- **OpenAI** – Text embeddings (`text-embedding-3-small`) and Chat Completion (`gpt-4o-mini`)
- **Pinecone** – Vector database for RAG
- **SMTP / Gmail / SendGrid** – Email delivery
- **Google Sheets / Database** – Logging and analytics
- **Lovable AI** – Form frontend and submission interface

---
### Workflow 1: Google Drive → Pinecone Update
Google Drive Trigger → Search files → Split in Batches → Download → Embeddings OpenAI → Pinecone Vector Store
                                  ↘
                              Loop / NoOp (for batching)

![Google Drive to Pinecone Workflow](./Ai Agent Support.PNG)

### Workflow 2: User Query → AI Answer


Lovable AI Form → Webhook (n8n) → OpenAI Embeddings → Pinecone Vector Store → AI Agent → Email Node
                                         ↘
                                      Simple Memory

## ⚠️ Important Note
## To use this project, you must add your own API keys for OpenAI, Pinecone, and any email service.

## The Lovable AI form link provided is for reference only — it will not work out of the box.

## Currently, the workflow uses the ChatGPT free API, which may stop working after a few days.

## You can replace the ChatGPT model with a free alternative like Gemini or your own OpenAI API key to keep it running.
