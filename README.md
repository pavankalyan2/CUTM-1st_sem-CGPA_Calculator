# Hybrid Information Retrieval System for Medical Text Search

## Overview
This project implements a **Hybrid Information Retrieval (IR) system** for medical text data by combining:

- **BM25 (Lexical Retrieval)** → exact keyword matching  
- **Dense Retrieval (Sentence Transformers + FAISS)** → semantic understanding  
- **Hybrid Fusion** → integrates both approaches  

**Goal:**  
Evaluate whether combining lexical and semantic retrieval improves search performance in the medical domain.

---

##Dataset

- **corpus.csv** → medical documents  
- **queries.csv** → user queries  
- **qrels.csv** → relevance judgments  

---

## Methods Implemented

### BM25 Retrieval
- Token-based lexical search  
- Strong performance for structured medical terminology  

### Dense Retrieval
- Model: `multi-qa-MiniLM-L6-cos-v1`  
- Converts text into embeddings  
- Uses FAISS for fast similarity search  

### Hybrid Retrieval
- Combines BM25 + Dense scores  
- Prioritizes exact matches while incorporating semantic signals  

---

## Evaluation

**Metric Used:** Precision@10 (P@10)

| Method  | P@10 |
|--------|------|
| BM25   | 0.89 |
| Dense  | 0.75 |
| Hybrid | 0.85 |

---

## Key Observations

- BM25 performs best due to precise medical terminology  
- Dense retrieval captures meaning but introduces noise  
- Hybrid retrieval balances both approaches but does not outperform BM25  

---

## How to Run

### 1. Install dependencies

pip install -r requirements.txt

### 2. Open the notebook

code/code.ipynb

3. Run all cells

4. Outputs will be generated in:
outputs/



Author

Abhiram Sunkari
CAP 6776 — Information Retrieval
Spring 2026
