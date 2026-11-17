# Retrieval-Augmented Generation (RAG) Architecture Using LangChain

## Project Overview

This project implements a **Retrieval-Augmented Generation (RAG) pipeline** using Python and the LangChain framework.

The system retrieves relevant information from PDF documents using semantic search and passes the retrieved context to a Large Language Model (LLM) to generate relevant, context-based responses.

The architecture combines document processing, embedding generation, vector storage, semantic retrieval, and LLM integration into a complete RAG workflow.

## Architecture

The project follows two major pipelines:

### 1. Data Ingestion Pipeline

1. **Document Loading:** Loads PDF documents from the `Data` directory using `PyPDFLoader`.
2. **Text Splitting:** Divides documents into smaller chunks using `RecursiveCharacterTextSplitter`.
3. **Embedding Generation:** Converts text chunks into numerical vectors using the Sentence Transformers model.
4. **Vector Storage:** Stores document chunks, embeddings, IDs, and metadata in ChromaDB.

### 2. Retrieval and Generation Pipeline

1. **User Query:** Accepts a natural language query.
2. **Query Embedding:** Converts the query into a vector using the same embedding model.
3. **Semantic Search:** Searches ChromaDB for the most relevant document chunks.
4. **Similarity Scoring:** Calculates similarity scores and applies a score threshold.
5. **Context Preparation:** Combines the retrieved documents into context.
6. **LLM Integration:** Passes the context and user query to an LLM.
7. **Response Generation:** Generates a response based on the retrieved information.

## Technology Stack

| Category | Technologies |
|---|---|
| Programming Language | Python |
| Framework | LangChain |
| Document Loader | PyPDFLoader |
| Text Splitter | RecursiveCharacterTextSplitter |
| Embedding Model | Sentence Transformers |
| Embedding Model Name | all-MiniLM-L6-v2 |
| Vector Database | ChromaDB |
| Similarity Search | Cosine Similarity |
| LLM Integration | OpenAI GPT, Groq |
| Development Environment | Jupyter Notebook |

## Key Features

- Loads multiple PDF documents from a directory.
- Extracts text and document metadata.
- Splits documents into smaller chunks.
- Generates 384-dimensional embeddings.
- Stores embeddings and document metadata in ChromaDB.
- Performs semantic search using vector similarity.
- Retrieves the top-k relevant document chunks.
- Supports similarity score thresholding.
- Integrates with OpenAI and Groq LLMs.
- Generates context-based responses using retrieved documents.

## Project Configuration

The current implementation uses the following configurations:

| Parameter | Value |
|---|---|
| Chunk Size | 500 |
| Chunk Overlap | 50 |
| Embedding Model | all-MiniLM-L6-v2 |
| Embedding Dimensions | 384 |
| Default Top-K | 3 |
| Default Temperature | 0.1 |
| Maximum Output Tokens | 1024 |
| Vector Database | ChromaDB |
| Collection Name | pdf_documents |

## Project Structure

```text
RAG-Architecture/
│
├── Data/
│   └── Research.pdf
│
├── data/
│   └── vector_store/
│
├── RAG_pipeline.ipynb
│
└── README.md
```

## Installation and Setup

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd RAG-Architecture
```

### 2. Install Required Libraries

```bash
pip install langchain
pip install langchain-community
pip install langchain-text-splitters
pip install sentence-transformers
pip install chromadb
pip install scikit-learn
pip install pypdf
pip install langchain-openai
pip install langchain-groq
```

### 3. Configure API Keys

The project supports OpenAI and Groq as LLM providers.

Add your API keys securely using environment variables.

```python
import os

API_KEY_OPENAI = os.getenv("OPENAI_API_KEY")
API_KEY_GROQ = os.getenv("GROQ_API_KEY")
```

Never upload your actual API keys to GitHub.

### 4. Add PDF Documents

Place your PDF documents inside the `Data` directory.

### 5. Run the Notebook

Open the notebook using Jupyter Notebook or JupyterLab:

```bash
jupyter notebook RAG_pipeline.ipynb
```

Execute the cells sequentially to run the complete RAG pipeline.

## Implementation Results

During the implementation:

- Successfully loaded 2 PDF documents.
- Extracted 35 pages from the documents.
- Generated 324 text chunks.
- Generated 384-dimensional embeddings.
- Stored document chunks and their metadata in ChromaDB.
- Retrieved the top 3 relevant document chunks for a sample query.
- Integrated LLMs through OpenAI and Groq.
- Generated responses using retrieved document context.

*Note: The notebook's ChromaDB collection count increased to 972 because documents were added across multiple executions. The ingestion run shown generated 324 chunks.*

## Learning Outcomes

Through this implementation, I gained practical experience with:

- Understanding RAG architecture and its working process.
- Building document ingestion pipelines.
- Working with text splitting and chunk overlap.
- Generating embeddings using Sentence Transformers.
- Managing vector databases using ChromaDB.
- Implementing semantic search and similarity scoring.
- Developing custom retrieval logic.
- Integrating LLMs with retrieved contextual information.
- Understanding the interaction between retrievers and generative models.

## Future Improvements

- Implement a user-friendly interface for document uploads and queries.
- Add support for multiple document formats.
- Implement document deduplication and update handling.
- Improve retrieval using reranking techniques.
- Add source citations to generated responses.
- Experiment with hybrid search techniques.
- Implement conversational memory for multi-turn queries.

## Conclusion

This project demonstrates the implementation of a RAG architecture that connects external PDF knowledge sources with Large Language Models.

It provides practical experience in document processing, embedding generation, vector databases, semantic retrieval, and LLM integration using Python and LangChain.

---

**Project Type:** Generative AI / Natural Language Processing

**Framework:** LangChain

**Language:** Python
