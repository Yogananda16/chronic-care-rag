# Chronic Care RAG: Diabetes & Hypertension Question Answering

Retrieval-Augmented Generation (RAG) system for answering clinical questions about diabetes and hypertension using MiniLM embeddings, FAISS retrieval, and GPT-2 family models.

---

## 1. System Overview

This project builds a lightweight medical question-answering system using Retrieval-Augmented Generation (RAG).  
It evaluates three GPT-2 family models under baseline and RAG settings to measure improvements in correctness, groundedness, and hallucination reduction.

---

## 2. Architecture

### **Figure 1 — RAG System Workflow**
<img width="1084" height="298" alt="Screenshot 2025-12-07 124635" src="https://github.com/user-attachments/assets/e401d3c0-2b43-44aa-802d-77a779a9b205" />


A user query is embedded using MiniLM, relevant text chunks are retrieved using a FAISS index, and the selected GPT-2 model generates an answer conditioned on the retrieved evidence.

---

## 3. Dataset & Corpus Processing

### **Link — [Dataset / Corpus Pipeline](https://onlinelibrary.wiley.com/doi/10.1111/j.1751-7176.2011.00434.x)**

The dataset consists of 9 medical documents across three categories:  
- Diabetes  
- Hypertension  
- Common / Overlap  

Pipeline steps:
1. Cleaning & normalization  
2. Chunking into 200-word windows (40-word overlap)  
3. Embedding with MiniLM-L6-v2  
4. Building a FAISS index for retrieval  

---

## 4. Retrieval Example

### **Figure 3 — Example of Retrieved Chunks**
<img width="2335" height="346" alt="Screenshot 2025-12-07 130125" src="https://github.com/user-attachments/assets/efc79303-8354-40c7-bf7d-6a38a8a05daf" />


This figure shows a sample question and the top-k chunks retrieved from the FAISS index, illustrating how contextual grounding improves answer quality.

---

## 5. Baseline vs RAG Comparison

RAG reduces hallucinations and produces more accurate, medically relevant responses by using retrieved context.

---

## 6. Model Evaluations

Below are the results for all three GPT-2 family models evaluated on the three domain-specific questions.

---

## 6.1 Model 1 — DistilGPT-2 (Smallest Model)

### **Figure 5 — Model 1 Results**
<img width="1960" height="254" alt="image" src="https://github.com/user-attachments/assets/a09439e9-cacc-48f2-9e0a-ca15a6da1527" />

DistilGPT-2 struggles the most under baseline conditions, often hallucinating or producing incomplete responses.  
RAG improves relevance but the model still lacks medical depth.

---

## 6.2 Model 2 — GPT-2 Medium

### **Figure 6 — Model 2 Results**
<img width="2093" height="242" alt="image" src="https://github.com/user-attachments/assets/e0927476-1ace-40c4-a3b0-a0615332713e" />

GPT-2 Medium shows better fluency and correctness.  
RAG stabilizes the output and reduces off-target content.

---

## 6.3 Model 3 — GPT-2 Large

### **Figure 7 — Model 3 Results**
<img width="2055" height="252" alt="image" src="https://github.com/user-attachments/assets/b966a483-c234-4e69-9e13-6bf0605f3d9a" />


GPT-2 Large performs the best across all metrics.  
RAG improves grounding and accuracy, although medical depth is still limited.

---

## 6.4 Combined Evaluation Table

### **Figure 8 — Combined Model Comparison**
<img width="2441" height="560" alt="image" src="https://github.com/user-attachments/assets/f69b68e2-e6f6-46f7-b1d6-493b8ad85a46" />

This summarizes correctness, groundedness, and hallucination tendencies across all models in baseline and RAG modes.

---

## 7. Key Insights

- RAG improves factual grounding for all models.  
- Larger models produce more consistent and coherent answers.  
- Smaller models hallucinate frequently without retrieval support.  
- Medical QA still requires domain-specific LLMs for high reliability.

---

## 8. Conclusion

This project shows how Retrieval-Augmented Generation (RAG) can improve the
quality and reliability of GPT-2 family models for medical question answering.
By grounding responses in a curated corpus on diabetes and hypertension, the
system reduces hallucinations and delivers more context-aligned answers.

Larger models perform better overall, but even they show limits in clinical
reasoning, highlighting the need for domain-specific medical LLMs. The RAG
pipeline offers a lightweight and practical improvement that makes smaller
models more usable without heavy computational requirements.

This repository provides all code, figures, and documentation needed to
reproduce or extend the system.


