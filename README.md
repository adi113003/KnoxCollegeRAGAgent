# 📘 Knox College RAG Assistant
*A Retrieval-Augmented Generation (RAG) system that answers questions using official Knox College documents.*

## 📌 Overview
This project is a Retrieval-Augmented Generation (RAG) agent built as part of my Data Science Capstone at Knox College. The system ingests institutional PDFs such as the Course Catalog, processes them through an n8n workflow, and answers user questions using evidence directly retrieved from the documents. The goal is to provide fast, transparent, and document-grounded information for students, faculty, and staff.

## 🔍 Features
- Loads and processes multiple PDF documents  
- Splits text into chunks for efficient retrieval  
- Generates embeddings using Google Gemini  
- Stores vectors in Pinecone for similarity search  
- Uses an n8n agent to enforce retrieval before answering  
- Provides grounded, non-hallucinated responses  
- Automatically updates when source PDFs change

## 🏗️ Architecture
**Workflow:**  
Google Drive → PDF Loader → Text Splitter → Gemini Embeddings → Pinecone VectorDB → Retrieval Agent → Chat Response  

**Chunking:** Recursive character text splitter (size 1200, overlap 150)  
**Namespace:** `KnoxCollege` for organized vector storage

## 🛠 Tech Stack
- n8n workflow automation  
- Google Drive API  
- Gemini Embeddings  
- Pinecone Vector Database  
- JavaScript / TypeScript within n8n nodes  
- PDF text extraction tools

## ⚙️ How It Works
1. PDFs are fetched from Google Drive.  
2. Text is cleaned, split into overlapping chunks, and embedded.  
3. Embeddings are pushed to Pinecone.  
4. When a user asks a question, the agent retrieves the most similar chunks.  
5. The LLM generates a grounded response using only the retrieved evidence.

## 🚀 Future Improvements
- Add more Knox College documents  
- Deploy a web-based chat interface  
- Add usage analytics and conversation history  
- Automate scheduled re-embedding when PDFs change
