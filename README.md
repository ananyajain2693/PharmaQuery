# PharmaQuery
AI-Powered Retrieval-Augmented Generation for Pharmaceutical Sciences
# 💊 PharmaQuery

### AI-Powered Retrieval-Augmented Generation for Pharmaceutical Sciences

PharmaQuery is an AI-powered **Retrieval-Augmented Generation (RAG)** application designed to answer pharmaceutical science questions using information retrieved from uploaded research documents.

The system combines **LangChain, HuggingFace embeddings, ChromaDB, Groq LLaMA, and Gradio** to create an interactive question-answering assistant for pharmaceutical and biomedical literature.

---

## 🚀 Project Overview

PharmaQuery allows users to upload pharmaceutical PDF documents and ask natural-language questions about their contents.

Instead of relying only on the language model's pre-trained knowledge, PharmaQuery first retrieves relevant information from the uploaded documents and then provides an answer based on that retrieved context.

### Core workflow

```text
PDF Documents
      ↓
Document Loading
      ↓
Text Extraction
      ↓
Text Chunking
      ↓
HuggingFace Embeddings
      ↓
Chroma Vector Database
      ↓
Semantic Retrieval
      ↓
Groq LLaMA
      ↓
Generated Answer
      ↓
Gradio Interface
```

---

## ✨ Key Features

* 📄 Upload multiple pharmaceutical PDF documents
* 🔎 Semantic document retrieval
* 🧠 Retrieval-Augmented Generation (RAG)
* 🤖 Groq-powered LLaMA language model
* 🔤 HuggingFace sentence-transformer embeddings
* 🗄️ Persistent Chroma vector database
* 🧩 LangChain-based RAG pipeline
* 🖥️ Simple Gradio web interface
* 💊 Designed for pharmaceutical science use cases
* 🔐 API key entered securely through the application interface

---

## 🧪 Knowledge Domains

The current project demonstrates questions from several pharmaceutical and biomedical domains:

| Domain               | Example Question                                             |
| -------------------- | ------------------------------------------------------------ |
| AI in Drug Discovery | What role does AI play in drug repurposing and discovery?    |
| Pharmacokinetics     | How is paracetamol metabolized in the body?                  |
| Vaccine Development  | What are the main stages of vaccine development?             |
| Gene Therapy         | How does CRISPR help in gene therapy?                        |
| Pharmacovigilance    | Why is pharmacovigilance important after a drug is released? |

The supplied source material describes AI techniques such as machine learning and deep learning for identifying drug candidates, predicting molecular interactions, and supporting drug repurposing.

The vaccine-development material covers target identification, preclinical testing, three phases of clinical trials, regulatory approval, and manufacturing scale-up.

---

## 🏗️ Technology Stack

### Artificial Intelligence

* Groq
* LLaMA
* LangChain

### Embeddings

* HuggingFace
* `sentence-transformers/all-mpnet-base-v2`

### Vector Database

* ChromaDB

### Document Processing

* PyPDF
* Sentence-transformer text splitting

### User Interface

* Gradio

### Development

* Python
* Jupyter Notebook

---

## ⚙️ How It Works

### 1. Document Upload

The user uploads one or more pharmaceutical PDF documents through the Gradio interface.

### 2. PDF Processing

PyPDF extracts the text and metadata from each document.

### 3. Text Chunking

Large documents are divided into smaller overlapping chunks so that relevant sections can be efficiently retrieved.

### 4. Embedding Generation

Each text chunk is converted into a numerical vector using:

```text
sentence-transformers/all-mpnet-base-v2
```

### 5. Vector Storage

The embeddings are stored in a persistent ChromaDB collection.

### 6. Semantic Retrieval

When the user asks a question, PharmaQuery searches the vector database for the most relevant document chunks.

The current implementation retrieves the top five similar chunks.

### 7. LLM Generation

The retrieved context is passed to a Groq-hosted LLaMA model.

The prompt instructs the model to answer using the retrieved context and avoid introducing information that is not present in that context.

### 8. Response

The generated answer is displayed through the Gradio interface.

---

## 📁 Repository Structure

```text
PharmaQuery/
│
├── README.md
├── requirements.txt
├── .gitignore
├── LICENSE
├── app.py
├── config.py
│
├── data/
│   └── README.md
│
├── notebooks/
│   ├── PharmaQuery.ipynb
│   └── PharmaQuery_Exploration.ipynb
│
├── src/
│   ├── embeddings.py
│   ├── document_processor.py
│   ├── retriever.py
│   └── rag_pipeline.py
│
├── docs/
│   └── pharmaceutical reference PDFs
│
└── screenshots/
    └── pharmaquery-ui.png
```

---

## 🔧 Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/PharmaQuery.git
cd PharmaQuery
```

Create a virtual environment:

```bash
python -m venv venv
```

Activate it.

### Windows

```bash
venv\Scripts\activate
```

### Linux / macOS

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## 🔑 API Key

PharmaQuery requires a Groq API key.

Create an API key through the Groq platform and provide it through the application's password field.

**Never commit your API key to GitHub.**

Do not place secrets directly inside Python files or notebooks.

A `.env` file can be used locally:

```text
GROQ_API_KEY=your_api_key_here
```

Make sure `.env` is included in `.gitignore`.

---

## ▶️ Running the Application

Start the Gradio application:

```bash
python app.py
```

The application will launch a local Gradio interface.

Upload your pharmaceutical PDFs, enter your API key, and ask a question such as:

```text
What are the main stages of vaccine development?
```

---

## 📚 Example Questions

### AI & Drug Discovery

```text
What role does AI play in drug repurposing and discovery?
```

### Pharmacokinetics

```text
How is paracetamol metabolized in the body?
```

### Vaccine Development

```text
What are the main stages of vaccine development?
```

### CRISPR

```text
How does CRISPR help in gene therapy?
```

### Pharmacovigilance

```text
Why is pharmacovigilance important after a drug is released?
```

The supplied pharmacokinetics document states that paracetamol is absorbed rapidly, is primarily metabolized in the liver, and is eliminated through the kidneys; it also identifies toxic metabolites as a cause of hepatotoxicity in overdose.

The CRISPR source describes CRISPR-Cas9 as enabling precise DNA editing and its use for correcting mutations associated with diseases including cystic fibrosis and sickle cell anemia.

The pharmacovigilance material emphasizes detection, assessment, and prevention of adverse drug reactions and the role of post-marketing surveillance in patient safety.

---

## 🧠 Why RAG?

Large language models can generate impressive answers, but a standalone model may not have access to the specific documents a researcher wants to analyze.

RAG addresses this by combining:

```text
Information Retrieval
        +
Large Language Model
        =
Context-Aware Answers
```

This makes PharmaQuery particularly useful for document-based pharmaceutical question answering.

---

## ⚠️ Limitations

PharmaQuery is an educational and research-oriented prototype and should not be treated as a replacement for qualified pharmaceutical, medical, regulatory, or clinical expertise.

Current limitations include:

* Answer quality depends on the uploaded documents.
* Retrieval quality depends on chunking and embedding performance.
* The application does not independently verify scientific claims.
* API access is required for the Groq-powered LLM.
* The current implementation does not provide a full citation interface for every generated answer.
* Pharmaceutical information should be independently validated before clinical or regulatory use.

---

## 🔮 Future Improvements

Potential improvements include:

* [ ] Add document-level and page-level citations
* [ ] Add source previews for retrieved chunks
* [ ] Add conversation history
* [ ] Add streaming responses
* [ ] Add configurable retrieval parameters
* [ ] Add hybrid keyword + semantic search
* [ ] Add reranking
* [ ] Add evaluation datasets
* [ ] Add automated RAG evaluation
* [ ] Add Docker support
* [ ] Add deployment configuration
* [ ] Add authentication
* [ ] Add support for additional document formats
* [ ] Add a dedicated pharmaceutical terminology layer

---

## 📊 Project Architecture

```text
                    ┌──────────────────┐
                    │ Pharmaceutical   │
                    │ PDF Documents    │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │   PyPDF Loader   │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ Text Chunking    │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │ HuggingFace      │
                    │ Embeddings       │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │    ChromaDB      │
                    │ Vector Database  │
                    └────────┬─────────┘
                             │
                       User Question
                             │
                             ▼
                    ┌──────────────────┐
                    │ Semantic Search  │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │   Groq / LLaMA   │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │  RAG Answer      │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │     Gradio       │
                    │       UI         │
                    └──────────────────┘
```

---

## 🎯 Project Objective

The goal of PharmaQuery is to demonstrate how modern generative AI and information retrieval techniques can be applied to pharmaceutical science documents.

It serves as a practical example of building a domain-focused RAG system that combines document retrieval, semantic embeddings, vector databases, and large language models.

---

## 👨‍💻 Author

**Ananya Paiya**
## ⭐ If You Find This Project Useful

Consider giving the repository a ⭐ on GitHub and contributing improvements through pull requests.

---

## 📄 License

This project is intended for educational and research purposes. Add an appropriate open-source license before distributing the repository.
