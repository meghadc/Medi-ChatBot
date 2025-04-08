# Medical-Chatbot_RAG - Medical Question Answering Bot using RAG and LLM

MediBot is a Retrieval-Augmented Generation (RAG) based chatbot built using the LangChain framework. It integrates a Mistral-7B language model from HuggingFace with document-based context retrieval powered by FAISS vector store. MediBot is designed to answer user queries using relevant information extracted from uploaded PDFs.

## Features

- ✅ Retrieval-Augmented Generation (RAG) pipeline
- ✅ PDF document ingestion and chunking
- ✅ FAISS-based vector store for efficient document similarity search
- ✅ HuggingFace LLM integration using Mistral-7B-Instruct-v0.3
- ✅ Custom prompts to ensure accurate, context-based responses

---

## Project Structure

```
.
├── medibot.py                    # CLI-based chatbot using LangChain and RAG
├── create_memory_for_llm.py     # PDF loading, chunking, and FAISS vector DB creation
├── connect_memory_with_llm.py   # LLM and retriever setup, query answering
├── data/                         # Folder containing PDF documents
├── vectorstore/db_faiss         # Stored FAISS vector index
```

---

## RAG Pipeline

This project utilizes a **Retrieval-Augmented Generation (RAG)** architecture:
1. **Document Loading**: PDFs are loaded from the `data/` directory using `PyPDFLoader`.
2. **Text Chunking**: Text is chunked using `RecursiveCharacterTextSplitter` to preserve context.
3. **Vector Embedding**: Text chunks are embedded using `sentence-transformers/all-MiniLM-L6-v2`.
4. **Vector Store**: FAISS is used to store and retrieve relevant chunks.
5. **LLM Query**: Queries are answered using `Mistral-7B-Instruct-v0.3` LLM from HuggingFace with a retrieval chain.

---

## Setup Instructions

### 1. Install Dependencies

Install the following packages:
- langchain
- langchain-community
- langchain-huggingface
- faiss-cpu
- sentence-transformers
- huggingface_hub
- pypdf

### 2. Create a .env file

```bash
HF_TOKEN=your_huggingface_api_token
```

---

## Running the Project

### Step 1: Create Memory (Embeddings and FAISS Index)

```bash
python create_memory_for_llm.py
```

This script:
- Loads PDFs from `data/`
- Splits content into chunks
- Embeds using MiniLM model
- Saves to FAISS vector store

---

### Step 2: Connect Memory with LLM and Query

```bash
python connect_memory_with_llm.py
```

Enter your query when prompted. The system will return an answer based on retrieved context and also display the source documents.

---

### Step 3: Use the Chatbot Interface

```bash
python medibot.py
```

MediBot will continuously prompt you for questions until you type "exit".

