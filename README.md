# 🤖 RAG AI Agent & Chatbot (n8n + Gemini + Pinecone)

An automated **Retrieval-Augmented Generation (RAG)** pipeline built with **n8n**. This project automatically syncs documents from Google Drive, indexes them into a vector database, and provides a conversational AI agent that answers questions based on your specific private data.

## ✨ Features

- **Automated Data Ingestion:** Monitors a specific Google Drive folder for new files.
- **Smart Chunking:** Uses Recursive Character Splitting to ensure high-quality context for the AI.
- **Vector Search:** Utilizes **Pinecone** as a high-performance vector database for semantic search.
- **State-of-the-Art AI:** Powered by **Google Gemini** for both high-dimensional embeddings and conversational reasoning.
- **Live Chat Interface:** A ready-to-use chat trigger to interact with your knowledge base in real-time.

---

## 🏗️ Workflow Architecture

The project consists of two main logic flows:

### 1. The Ingestion Pipeline (Drive → Pinecone)

- **Trigger:** Google Drive watches for `fileCreated` events.
- **Processing:** Downloads the file, extracts text, and splits it into manageable chunks ().
- **Embedding:** Converts text chunks into vectors via `Embeddings Google Gemini`.
- **Storage:** Upserts vectors into the **Pinecone** index under the `FAQ` namespace.

### 2. The Chat Pipeline (User → Agent → Response)

- **Input:** User sends a message via the `Chat Trigger`.
- **Retrieval:** The AI Agent uses the `Vector Store Tool` to query Pinecone for relevant document snippets.
- **Generation:** Gemini uses the retrieved snippets as "context" to generate a grounded, accurate response.

---

## 🛠️ Tech Stack

- **Automation:** [n8n](https://n8n.io/)
- **LLM & Embeddings:** [Google Gemini](https://aistudio.google.com/)
- **Vector Database:** [Pinecone](https://www.pinecone.io/)
- **Source:** [Google Drive](https://www.google.com/drive/)

---

## 🚀 Getting Started

### Prerequisites

1. **n8n instance** (Desktop, Cloud, or Self-hosted).
2. **Google Cloud Project** with the Google Drive API enabled.
3. **Google AI Studio API Key** (Free tier from [aistudio.google.com](https://aistudio.google.com)).
4. **Pinecone Index** named `rag-agent-index` (Dimension: **768**, Metric: **Cosine**).

### Installation

1. **Clone the Repo:**

```bash
git clone https://github.com/YOUR_USERNAME/Rag-Agent-w-Chatbot.git

```

2. **Import to n8n:**

- Open n8n.
- Click **Import from File** and select `workflow.json`.

3. **Configure Credentials:**

- Create your **Google Drive OAuth2** credentials.
- Create your **Google Gemini(PaLM) API** credentials.
- Create your **Pinecone API** credentials.

4. **Set Folder ID:**

- Update the **Google Drive Trigger** node with the specific ID of the folder you want to monitor.

---

## 🗺️ Roadmap

- [ ] Add support for PDF/Docx specifically via advanced loaders.
- [ ] Implement a "Source Citation" feature so the bot tells you which file it's reading from.
- [ ] Add a Slack/Discord integration for the chat interface.

---

### One final "Pro" tip:

Since you are using **GitHub Desktop**, once you've saved this text into your `README.md` file, GitHub Desktop will show the changes. Just **Commit** and **Push**, and your repo will look incredible!

**Would you like me to help you generate a simple "How to find your Google Drive Folder ID" guide to include in the README?**
