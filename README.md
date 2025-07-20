# Course Recommendation System using edX Data
by: Deira Aisya Refani

This project implements a **content-based course recommendation system** using course metadata scraped from edX. It includes data collection, preprocessing, semantic vectorization, similarity computation, and evaluation using standard information retrieval metrics.
---

## 📌 Objective

To recommend relevant online courses based on user learning goals expressed in natural language, by measuring semantic similarity between user requests (from dummy data) and course content.

## 🤖 Semantic Embedding

Text data was embedded using **Sentence-BERT** with the pre-trained model: **paraphrase-MiniLM-L6-v2**.

Each course’s preprocessed content was combined into a single `combined_text` column and encoded into a dense vector. Similarly, 1,000 synthetic user queries (`user_request`) were generated and encoded using the same model. The results are saved in `course_vectors.csv` and `query_vectors.csv`.

---

## 📈 Cosine Similarity

We compute the pairwise **cosine similarity** between user request vectors and course vectors. The result is saved in:

- `similarity_matrix.csv`

Each row corresponds to a course, and each column corresponds to a user request.

---

## 🧠 Recommendation Logic

Courses are ranked using a combination of:
- **Cosine similarity score** (higher is better)
- **Course difficulty level** (`level_rank`, lower is better)

### Level ranking:
- `0` = introductory / includes introductory
- `1` = intermediate only
- `2` = advanced only

Top-N recommendations are selected based on this hybrid scoring.

---

## 🧪 Evaluation

We use the following metrics:
- **Precision@K**: How many of the top-K recommended courses are relevant?
- **Recall@K**: How many of the relevant courses are captured in the top-K?


