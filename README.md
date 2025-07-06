# Intelligent Complaint Analysis for Financial Services (RAG Chatbot)

This project is part of the **10 Academy KAIM 5 - Week 6** challenge. It aims to build a **RAG-powered internal chatbot** that allows teams at **CrediTrust Financial** to analyze thousands of customer complaints efficiently using **LLMs + semantic search**.

---

## 🧠 Business Context

**CrediTrust** receives thousands of monthly complaints about its financial products (credit cards, loans, BNPL, etc.). Product managers and compliance teams currently read complaints manually — costing time and losing insights.

We built a **Retrieval-Augmented Generation (RAG)** system to:
- Let users ask questions in natural language
- Retrieve relevant complaint narratives from a vector DB
- Generate grounded, actionable answers using a language model

---

## 🚀 Final Deliverables

- ✅ A cleaned & filtered CFPB complaints dataset
- ✅ Text embeddings chunked and stored in FAISS vector DB
- ✅ RAG core logic with evaluation
- ✅ Streamlit UI for interactive chat
- ✅ 📄 Final blog-style report

---

## 🧰 Tech Stack

| Component      | Tool/Library                        |
|----------------|-------------------------------------|
| Language Model | `sentence-transformers` (MiniLM)    |
| Vector DB      | `FAISS`                             |
| LLM Framework  | `LangChain`, `Transformers`         |
| UI             | `Streamlit` or `Gradio`             |
| Data           | CFPB Complaints Dataset             |
| Hardware       | GPU-enabled via PyTorch             |

---

## 📁 Project Structure

```bash
.
├── data/
│   └── filtered_complaints.csv        # Cleaned dataset
│
├── vector_store/
│   ├── faiss_index.bin               # FAISS vector index
│   └── metadata.pkl                  # Corresponding chunk metadata
│
├── notebooks/
│   └── task_1_eda_and_preprocessing.ipynb
│
├── src/
│   ├── build_vector_store.py         # Task 2 script
│   ├── rag_pipeline.py               # Task 3 logic
│   └── app.py                        # Task 4: Chat UI
│
├── requirements.txt
└── README.md
````

---

## ✅ Task 1: EDA & Preprocessing

### 🔧 Actions:

* Loaded CFPB complaints CSV
* Filtered for 5 relevant products:

  * Credit card, Personal loan, Buy Now Pay Later (BNPL), Savings account, Money transfers
* Removed empty complaint narratives
* Cleaned text (lowercase, removed boilerplate)

### 📁 Output:

* `data/filtered_complaints.csv`

---

## ✅ Task 2: Chunking, Embedding & Indexing

### 🔧 Actions:

* Used `LangChain.RecursiveCharacterTextSplitter` with:

  * `chunk_size = 300`, `chunk_overlap = 50`
* Generated embeddings using:

  * `sentence-transformers/all-MiniLM-L6-v2` (on GPU)
* Stored embeddings + metadata using FAISS

### 📁 Output:

* `vector_store/faiss_index.bin`
* `vector_store/metadata.pkl`

---

## ✅ Task 3: RAG Pipeline + Evaluation

### 🔧 Actions:

* Implemented RAG logic in `rag_pipeline.py`:

  * Embed query → Search FAISS → Prompt LLM with top-k chunks
* Prompt format:

  ```
  You are a financial analyst assistant for CrediTrust.
  Use the following context to answer:
  Context: {context}
  Question: {question}
  Answer:
  ```
* Evaluated the system using 5–10 sample queries

  * Metrics: answer relevance, groundedness, clarity

### 📁 Output:

* Evaluation table (Markdown)
* Analysis & tuning notes in final report

---

## ✅ Task 4: Interactive Chat Interface

### 🔧 Actions:

* Built a Streamlit (or Gradio) UI
* User can:

  * Type a question
  * See LLM-generated answer
  * View sources (retrieved chunks)
  * Optional: Streaming responses

### 📁 Output:

* `src/app.py`
* Screenshots in final report

---

## 🧪 How to Run

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Launch the chat app

```bash
streamlit run src/app.py
```

---
