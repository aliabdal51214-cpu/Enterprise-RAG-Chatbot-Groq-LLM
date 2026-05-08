# 🧠 RAG Chatbot — Wikipedia Knowledge Base + Groq LLM

[![Python](https://img.shields.io/badge/Python-3.10-blue?logo=python&logoColor=white)](https://python.org)
[![LangChain](https://img.shields.io/badge/LangChain-0.2-green?logo=chainlink)](https://langchain.com)
[![Groq](https://img.shields.io/badge/LLM-Groq%20LLaMA3-orange)](https://groq.com)
[![FAISS](https://img.shields.io/badge/VectorDB-FAISS-red)](https://faiss.ai)
[![Gradio](https://img.shields.io/badge/UI-Gradio-ff6b00?logo=gradio)](https://gradio.app)
[![Colab](https://img.shields.io/badge/Google%20Colab-Ready-F9AB00?logo=googlecolab&logoColor=white)](https://colab.research.google.com)

---

## 📌 Project Overview

A production-quality **Retrieval-Augmented Generation (RAG)** chatbot that answers questions using a Wikipedia-based knowledge base. Unlike basic chatbots that rely on LLM memory alone, this system **retrieves real, sourced information** before generating answers — reducing hallucinations and improving accuracy.

> Built to demonstrate end-to-end AI/ML engineering: vector embeddings, semantic search, LLM integration, conversational memory, and UI deployment.

---

## 🏗️ System Architecture

```
User Question
     │
     ▼
┌─────────────────────┐
│  Gradio UI Frontend │
└────────┬────────────┘
         │
         ▼
┌─────────────────────────┐
│  ConversationalRetrieval │   ← LangChain RAG Chain
│        Chain             │
└───────┬─────────────────┘
        │
   ┌────┴────┐
   │         │
   ▼         ▼
┌──────┐  ┌──────────────────────┐
│ FAISS│  │  Groq LLM (LLaMA 3) │
│Vector│  │  llama3-8b-8192      │
│Store │  └──────────────────────┘
└──┬───┘
   │
   ▼
HuggingFace Embeddings
(all-MiniLM-L6-v2)
   │
   ▼
Wikipedia Knowledge Base
(8 AI/ML topic articles)
```

---

## 🚀 Tech Stack

| Component | Technology | Purpose |
|---|---|---|
| **LLM** | Groq — LLaMA 3 8B | Answer generation |
| **Vector DB** | FAISS (Facebook AI) | Fast semantic search |
| **Embeddings** | HuggingFace `all-MiniLM-L6-v2` | Text → vector conversion |
| **RAG Framework** | LangChain | Orchestration pipeline |
| **Knowledge Base** | Wikipedia API | Source documents |
| **Memory** | LangChain ConversationBufferMemory | Multi-turn context |
| **UI** | Gradio Blocks | Interactive web interface |
| **Runtime** | Google Colab | Free GPU/CPU compute |

---

## ✨ Key Features

- 🔍 **Semantic Retrieval** — finds relevant chunks using cosine similarity in vector space, not keyword matching
- 🧠 **Multi-turn Memory** — remembers conversation context across multiple questions
- 📎 **Source Citations** — every answer shows which Wikipedia articles were used
- ⚡ **Groq Speed** — LLaMA 3 on Groq runs at ~500 tokens/sec (10× faster than standard APIs)
- 🌐 **Public URL** — instantly shareable via Gradio's `share=True`
- 🔧 **Configurable** — easily swap topics, models, or chunk sizes

---

## ⚙️ How RAG Works (Step by Step)

**Indexing Phase (done once at startup):**
1. Wikipedia articles are fetched for 8 AI/ML topics
2. Articles are split into 500-token chunks with 50-token overlap
3. Each chunk is converted to a 384-dimensional vector using `all-MiniLM-L6-v2`
4. Vectors are stored in a FAISS index for fast nearest-neighbor search

**Query Phase (every user message):**
1. User's question is embedded into the same vector space
2. FAISS retrieves the **top-4 most semantically similar** chunks
3. Chunks + conversation history are injected into the LLM prompt
4. Groq's LLaMA 3 generates a grounded, sourced answer
5. Sources are displayed alongside the answer in the UI

---

## 📁 Project Structure

```
rag-wikipedia-chatbot/
│
├── RAG_Chatbot_Wikipedia_Groq.ipynb   # Main Colab notebook
├── requirements.txt                    # Python dependencies
└── README.md                           # This file
```

---

## 🛠️ Setup & Usage

### Run on Google Colab (Recommended)

1. Open the notebook in Google Colab
2. Go to **🔑 Secrets** (left sidebar) → Add secret named `GROQ_API_KEY`
3. Get your free Groq API key at [console.groq.com](https://console.groq.com)
4. Run all cells top to bottom
5. Click the public Gradio link to use the chatbot

### requirements.txt

```
langchain
langchain-community
langchain-groq
faiss-cpu
sentence-transformers
wikipedia
gradio
tiktoken
```

---

## 📊 Knowledge Base

| Topic | Wikipedia Article |
|---|---|
| Artificial Intelligence | [Link](https://en.wikipedia.org/wiki/Artificial_intelligence) |
| Machine Learning | [Link](https://en.wikipedia.org/wiki/Machine_learning) |
| Deep Learning | [Link](https://en.wikipedia.org/wiki/Deep_learning) |
| Natural Language Processing | [Link](https://en.wikipedia.org/wiki/Natural_language_processing) |
| Large Language Models | [Link](https://en.wikipedia.org/wiki/Large_language_model) |
| Transformers Architecture | [Link](https://en.wikipedia.org/wiki/Transformer_(deep_learning_architecture)) |
| Retrieval-Augmented Generation | [Link](https://en.wikipedia.org/wiki/Retrieval-augmented_generation) |
| Neural Networks | [Link](https://en.wikipedia.org/wiki/Neural_network) |

---

## 🎯 Skills Demonstrated

- ✅ Retrieval-Augmented Generation (RAG) pipeline design
- ✅ Vector embeddings & semantic similarity search
- ✅ FAISS vector database indexing and querying
- ✅ LangChain orchestration (chains, memory, retrievers)
- ✅ LLM API integration (Groq / LLaMA 3)
- ✅ HuggingFace Sentence Transformers
- ✅ Conversational memory management
- ✅ Gradio UI development & deployment
- ✅ Document chunking strategies

---

## 🔮 Future Improvements

- [ ] Expand knowledge base with PDF upload support
- [ ] Add Urdu language support for Pakistani users
- [ ] Deploy permanently on Hugging Face Spaces
- [ ] Implement hybrid search (BM25 + semantic)
- [ ] Add re-ranking with cross-encoder models
- [ ] Integrate streaming responses

---

## 👤 Author

**Ali Abdal**

- 🔗 LinkedIn: [linkedin.com/in/ali-abdal-ml](https://www.linkedin.com/in/ali-abdal-ml/)
- 🐙 GitHub: [github.com/aliabdal51214-cpu](https://github.com/aliabdal51214-cpu)

---

## 📄 License

MIT License — free to use and modify.

---

> ⭐ If this project helped you understand RAG, please give it a star!
