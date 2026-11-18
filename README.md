# A-semantic-search-and-AI-powered-interview-preparation-assistant-using-ChromaDB-and-Gemini.
An AI-powered interview preparation assistant using RAG, ChromaDB, Sentence Transformers and Google Gemini to retrieve relevant interview questions and generate structured study guides.


# AI Interview Preparation Assistant | RAG with ChromaDB & Gemini

An AI-powered interview preparation assistant built using **Retrieval-Augmented Generation (RAG)**. The system uses semantic search to retrieve previously asked interview questions from a dataset of 21,013 interview records and Google's Gemini API to generate structured study guides and explanations.

## Project Overview

Preparing for technical and analytical interviews can be challenging when interview questions are scattered across different companies, job roles and platforms.

This project addresses that problem by building a RAG pipeline that retrieves relevant historical interview questions and uses an LLM to generate contextualised preparation guides.

## Architecture

1. **Data Collection:** Aggregate interview question datasets from multiple CSV files.
2. **Data Cleaning:** Remove duplicate records and missing context values.
3. **Feature Engineering:** Combine interview questions, company names and job positions into contextual text.
4. **Metadata Preparation:** Store interview dates alongside contextual documents.
5. **Vector Database:** Use ChromaDB to store and index document embeddings.
6. **Semantic Retrieval:** Retrieve the most relevant interview questions using vector similarity.
7. **LLM Generation:** Use Google's Gemini API to analyse retrieved information and generate structured study guides.

## Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming |
| Pandas | Data manipulation and cleaning |
| ChromaDB | Vector database |
| Sentence Transformers | Text embeddings |
| all-MiniLM-L6-v2 | Embedding model |
| Google Gemini API | LLM response generation |
| Google GenAI SDK | Gemini integration |
| Matplotlib | Data visualisation |
| Google Colab | Development environment |

## Dataset

The project uses interview question datasets containing information such as:

- Interview questions
- Company names
- Job positions
- Interview ratings
- Interview dates
- Comments

**Dataset source:** [AshishJangra27/datasets](https://github.com/AshishJangra27/datasets)

After cleaning and deduplication, the pipeline processes **21,013 unique interview records**.

## RAG Implementation

### 1. Data Processing
- Consolidated multiple CSV datasets into a single DataFrame.
- Created contextual documents by combining questions, companies and job positions.
- Removed duplicate and missing records.
- Exported processed documents and metadata into JSON.

### 2. Vector Database Ingestion
- Initialised a persistent ChromaDB database.
- Generated embeddings using Sentence Transformers (`all-MiniLM-L6-v2`).
- Stored 21,013 documents with associated date metadata.
- Used batch ingestion of 500 records.

### 3. Semantic Search
ChromaDB retrieves the top relevant interview questions based on the semantic similarity between the user's query and stored document embeddings.

### 4. Augmented Response Generation
Retrieved documents are passed to Gemini with a structured prompt.

The LLM is instructed to:
- Identify repeated interview questions and patterns.
- Highlight important interview topics.
- Explain relevant technical concepts.
- Generate structured interview preparation guides.
- Ground its analysis in retrieved interview information.

## Example Query

**User Query:**

"What are the questions asked in Google interviews?"

**Retrieved Information:**

- Basic algorithm questions.
- Probability and statistics.
- Machine learning concepts.
- Personal introduction and project discussions.
- Google products and ecosystem knowledge.

**Generated Output:**

Gemini analyses the retrieved questions, identifies recurring themes and produces an organised interview preparation guide with explanations and suggested answers.

## Project Structure

```text
interview-rag-assistant/
│
├── interview_rag.ipynb
├── README.md
├── requirements.txt
│
├── data/
│   └── interview_questions_metadata.json
│
└── chroma_db/
    └── (Generated locally)
```

## Installation & Setup

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/interview-rag-assistant.git

cd interview-rag-assistant
```

### 2. Install dependencies

```bash
pip install -r requirements.txt
```

### 3. Configure API credentials

Set your Google Gemini API key as an environment variable:

```python
import os

os.environ["GOOGLE_API_KEY"] = "YOUR_API_KEY"
```

For Google Colab, use Colab Secrets instead of hardcoding your API key.

### 4. Run the notebook

Open `interview_rag.ipynb` in Google Colab or Jupyter Notebook and execute the cells sequentially.

## Future Improvements

- Develop an interactive chatbot interface using Streamlit.
- Implement hybrid search combining keyword and semantic retrieval.
- Add similarity scores and source references to retrieved questions.
- Introduce conversation history and multi-turn question answering.
- Evaluate retrieval quality using Precision@K and Recall@K.
- Add filters for companies, job positions and interview dates.

## Key Learning Outcomes

- Understanding Retrieval-Augmented Generation architecture.
- Working with vector databases and embeddings.
- Implementing semantic search.
- Processing and preparing unstructured text data.
- Integrating LLM APIs into AI applications.
- Building end-to-end RAG pipelines.

---

**Author:** Fazil

**Domain:** Artificial Intelligence | Data Science | Generative AI | RAG

