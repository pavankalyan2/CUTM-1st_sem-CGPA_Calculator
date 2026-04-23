# Hybrid Information Retrieval System

## Overview
This project implements a **Hybrid Information Retrieval System** that combines:
- **BM25 (lexical retrieval)**
- **Dense Retrieval (semantic search using Sentence-BERT)**

The goal is to improve search effectiveness in educational datasets by balancing:
- Keyword matching (precision)
- Semantic understanding (context)

---

## Dataset
The system uses the following files:
- `corpus.csv` → document collection
- `queries.csv` → user queries
- `qrels.csv` → relevance judgments

Dataset details:
- ~450 documents
- 10 queries
- Relevance labels for evaluation

---

## System Architecture
The system follows a pipeline-based approach:

1. Load dataset
2. Perform BM25 retrieval (baseline from HW3)
3. Perform dense retrieval using embeddings + FAISS
4. Normalize scores
5. Apply hybrid fusion
6. Evaluate using Precision@10

---

## Methods Used

### 1. BM25 (Baseline)
- Keyword-based retrieval
- Strong performance for exact matches
- Serves as baseline system

### 2. Dense Retrieval
- Model: `multi-qa-MiniLM-L6-cos-v1`
- Converts text into embeddings
- Uses FAISS for fast similarity search

### 3. Hybrid Retrieval
- Combines BM25 and Dense scores
- Uses normalization for fair comparison
- Applies weighted fusion strategy
- Includes threshold-based boosting

---

## Evaluation Metric

**Precision@10 (P@10)**  
Measures the proportion of relevant documents in the top 10 results.

---

## Results

| Method | P@10 |
|--------|------|
| BM25   | 0.13 |
| Dense  | 0.09 |
| Hybrid | 0.10 |

---

## Key Observations
- BM25 performs best due to keyword-heavy dataset
- Dense retrieval captures semantic meaning but introduces noise
- Hybrid system improves flexibility but does not outperform BM25 in this dataset

---

## How to Run

### 1. Install dependencies
pip install -r requirements.txt

### 2. Update paths in the script
Modify:
DATA_PATH = "your_path/data/"
OUTPUT_PATH = "your_path/outputs/"

### 3. Run the script
python project_sanjana_kurma.py

---

## Outputs Generated
- `run_dense.csv` → Dense retrieval results
- `run_hybrid.csv` → Hybrid retrieval results
- `metrics_summary.csv` → Evaluation results

---

## Future Improvements
- Query expansion techniques
- Learning-to-rank models
- Retrieval-Augmented Generation (RAG)
- Domain-specific embedding models

---

## Author
Sanjana Kurma  
CAP 6776 — Information Retrieval  
Spring 2026
