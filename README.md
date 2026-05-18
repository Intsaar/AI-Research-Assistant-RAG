# 📑 AI Research Assistant (Tabular RAG System)

An advanced **Retrieval-Augmented Generation (RAG)** pipeline designed to perform semantic context-aware Search and Q&A over scientific papers and academic datasets. Built using **LangChain**, **ChromaDB**, and **Llama-3 (via Groq Cloud API)**, this system processes tabular academic metadata (CSV formats) from Kaggle to fetch, filter, and answer complex research questions without LLM hallucinations.

---

## 🚀 Features
* **Tabular Document Ingestion:** Custom parsing of structured CSV metadata (Authors, Titles, Publication Dates, Abstracts, and source URLs).
* **Metadata-Enriched Search:** Leverages LangChain's `Document` objects to pair textual abstracts with explicit source metadata for precise lineage tracking.
* **Semantic Chunking & Indexing:** Splitting verbose abstracts into contextual chunks using `RecursiveCharacterTextSplitter`.
* **High-Performance Vector Cache:** Persistent vector storage powered by **ChromaDB** for ultra-fast vector similarity matching.
* **Source-Grounded Generation:** Restricts **Llama-3-8b** responses strictly to the retrieved context, dynamically instructing the model to synthesize answers while citing the original Paper Title, Authors, and direct web URLs.
* **Interactive Dashboard:** Built with **Gradio** for seamless dataset ingestion, real-time query semantic retrieval, and low-latency response generation.

---

## 🛠️ Tech Stack & Architecture

* **Framework:** LangChain (Prompt Templates, Document Processing, Vector Retrievers)
* **Vector Store:** ChromaDB (Persistent local vector storage)
* **Embeddings Model:** HuggingFace `all-MiniLM-L6-v2` (Sentence Transformers)
* **LLM Core:** Llama-3-8b (Deployed via Groq Cloud API for microsecond inference)
* **Data Processing:** Pandas (For robust structured CSV reading)
* **User Interface:** Gradio Web UI

---

## 📸 Interface Preview
*(Place your Gradio interface screenshot here to showcase the system in action!)*

---

## 📦 Installation & Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/AI-Research-Assistant.git
   cd AI-Research-Assistant
   ```

2. **Install Dependencies:**
   ```bash
   pip install langchain langchain-community langchain-groq chromadb sentence-transformers gradio python-dotenv pandas
   ```

3. **Secure Environment Setup:**
   Create a `.env` file in the project root directory and add your secret API key:
   ```text
   GROQ_API_KEY=gsk_your_actual_groq_api_key_here
   ```

4. **Launch the Web Dashboard:**
   ```bash
   python app.py
   ```

---

## 🎯 RAG Evaluation Architecture (Future Roadmap)
To systematically measure the correctness of the Tabular RAG application, the next milestone involves integrating the **Ragas Evaluation Framework** to score the pipeline across the **RAG Triad**:
* **Context Relevance:** Quantifies how well ChromaDB filters and retrieves papers specific to the query.
* **Faithfulness (Groundedness):** Measures if Llama-3's response relies *only* on the retrieved abstracts, preventing hallucinations.
* **Answer Relevance:** Validates that the generated research breakdown addresses the researcher's query completely.
