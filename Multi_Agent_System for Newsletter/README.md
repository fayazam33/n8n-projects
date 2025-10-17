# 📰 Multi-Agent System for Automated Newsletters (n8n + Gemini + Tavily)

This workflow automates newsletter creation using multiple AI agents coordinated within **n8n**.  
It takes a topic and an email address as input, gathers recent articles, writes topic sections using **Google Gemini**, and compiles a full HTML newsletter automatically sent to the subscriber via Gmail.

---
## demo video 
(Multi_Agent_System for Newsletter/demo2.gif)

## 🚀 Features

- 🧠 **AI Multi-Agent System:** Specialized Gemini agents collaborate to generate, refine, and merge newsletter content.
- 🔍 **Real-Time Web Research:** Tavily Search retrieves the latest and most relevant articles.
- 📧 **Auto Email Delivery:** Final HTML newsletter is sent directly through the Gmail API.
- 🧾 **Structured Output Parsing:** JSON schema ensures all AI outputs are properly validated.

---

## 🧩 Workflow Overview

### 1. **User_data (Form Trigger)**
- A form collects:
  - `Newsletter_topic`
  - `E-mail`
- The workflow starts automatically when a user submits the form.

### 2. **Search (Tavily Search Node)**
- Uses the provided topic to gather recent web articles and insights.

### 3. **AI Agent (Gemini)**
- Analyzes Tavily search results to extract main ideas.
- Generates a **newsletter brief**: title + 3 main subtopics.

### 4. **Structured Output Parser**
- Validates and formats the AI output (ensures correct schema).

### 5. **Split Out**
- Splits each subtopic for detailed research and writing.

### 6. **Search1 (Tavily Search)**
- Performs in-depth searches for each of the 3 subtopics.

### 7. **AI Agent1 (Gemini)**
- Writes a **standalone section** for each subtopic, including real verified citations and links.

### 8. **Aggregate**
- Combines all 3 generated sections for the final merge.

### 9. **AI Agent2 (Gemini - Editor)**
- Acts as the **chief newsletter editor**.
- Merges sections into a single cohesive, HTML-formatted newsletter with introduction, sources, and conclusion.

### 10. **Structured Output Parser1**
- Ensures the final AI output contains:
  - `subject` (for email subject line)
  - `content` (full HTML body)

### 11. **Send a message (Gmail Node)**
- Sends the final newsletter HTML to the user’s email address.


## 🔐 Required Credentials

| Service | Credential Name | Purpose |
|----------|----------------|----------|
| **Google Gemini (PaLM)** | `Google Gemini(PaLM) Api account` | For text generation & reasoning |
| **Tavily Search API** | `Tavily account` | For retrieving current articles |
| **Gmail OAuth2** | `Gmail account` | For sending the final newsletter email |

---

## 🧰 Setup Instructions

1. **Clone or Import Workflow**
   - Import the provided JSON file into your local or cloud **n8n** instance.

2. **Configure Credentials**
   - Set up and connect:
     - Gemini API key
     - Tavily API key
     - Gmail OAuth2 credentials

3. **Activate Workflow**
   - Turn on the workflow toggle (`active: true`) to make the form live.

4. **Test the Workflow**
   - Open your **Form Trigger URL**.
   - Enter a topic and your email.
   - Check your inbox for the generated newsletter.

---

## 💌 Example Input / Output

**Form Input: if you use my workflow you can add here Google Forms here**
