# Comparing Reranking and Fusion Retrieval Techniques for Technical Manual Processing

This repository contains my implementation and analysis of advanced Retrieval-Augmented Generation (RAG) techniques applied to the Fervi T999 technical manual.

## Project Overview

In this project, I explore how specific advanced RAG techniques can improve information retrieval from technical documentation. Using the Fervi T999 lathe manual as a test case, I implement and compare two approaches:

1. **Reranking**: A technique that improves retrieval precision using a cross-encoder to better evaluate document relevance
2. **Fusion Retrieval**: A hybrid approach that combines vector search with keyword-based (BM25) search

## Repository Contents

- `rag_techniques_comparison.ipynb`: The main Jupyter notebook containing all code, experiments, and analysis
- Link: https://colab.research.google.com/drive/1Mp9EvatPF9zHde5RZKhg4sUbUy4sfDpr?usp=sharing

## Key Findings

My qualitative analysis of the responses revealed significant differences in how each technique handled technical documentation:

### Answer Quality and Relevance

For the question "Where is the rotation reverse lever located on the T999?":
- Baseline produced a verbose answer with model confusion
- Reranking delivered a direct, precise answer: "The rotation reverse lever is located to the right of the tool holder carriage"
- Fusion provided correct information with appropriate context

For technical specifications:
- Fusion Retrieval excelled at providing comprehensive information, including additional context like "The machine has 8 different spindle speeds"
- Reranking was most precise but sometimes missed contextual details
- Baseline often included irrelevant information

### Information Synthesis

For complex maintenance and safety questions:
- Fusion Retrieval produced the most well-rounded answers, effectively combining information from different sections
- Reranking created well-structured safety guidelines with excellent organization
- Baseline answers were adequate but less comprehensive

### Impact of Fusion's Alpha Parameter

Testing with different alpha values revealed:
- α=0.2 (BM25-heavy): Direct answers focused on explicit terms
- α=0.5 (balanced): Optimal combination of keyword precision and semantic understanding
- α=0.8 (vector-heavy): More contextual information but occasionally irrelevant details

### Overall Assessment

The comparison demonstrated that both techniques significantly improved information retrieval quality compared to baseline RAG:

- **Reranking** proved exceptional for direct factual queries where precision matters most
- **Fusion Retrieval** showed superior performance for questions requiring comprehensive information synthesis

These findings highlight how combining different retrieval methods can effectively address the unique challenges of technical documentation, improving both the precision and completeness of extracted information.
