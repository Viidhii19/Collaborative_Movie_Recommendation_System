# 🎬 Transformer-Based Movie Recommendation System

A **sequence-aware collaborative filtering system** that uses a **Transformer architecture** to predict the next movie a user is likely to watch.

Instead of predicting ratings (traditional approach), this system models user behavior as a **sequence prediction problem**, similar to how GPT models generate text.

---

## 🚀 Why This Project Matters

Traditional recommender systems (KNN, SVD):

* Ignore sequence order
* Treat interactions as static

This system:

* Learns **watch patterns over time**
* Captures **contextual relationships between movies**
* Applies **LLM-style learning to recommendation systems**

---

## 🧠 Core Idea

Reframing recommendation as next-token prediction:

* Movies → Tokens
* User history → Sequence
* Next movie → Prediction

Example:

[Movie₁, Movie₂, Movie₃] → Movie₄

This is the same learning paradigm used in GPT models.

---

## 🏗️ System Pipeline

1. **Data Ingestion**

   * Netflix Prize Dataset (~100M ratings, sampled)

2. **Preprocessing**

   * Clean and parse raw data
   * Merge ratings with movie metadata

3. **Filtering**

   * Keep only positive interactions (rating ≥ 4)

4. **Sequence Construction**

   * Convert user histories into sequential training samples

5. **Tokenization**

   * Map movie IDs → integer tokens

6. **Dataset Preparation**

   * Padding and batching for fixed-length input

7. **Model**

   * Transformer Encoder with multi-head self-attention

8. **Prediction**

   * Outputs probability distribution over all movies

---

## 🤖 Model Architecture

* **Embedding Layer**: Converts movie IDs into dense vectors
* **Transformer Encoder**:

  * Multi-head self-attention
  * Captures relationships across watched movies
* **Output Layer**:

  * Fully connected layer for next-movie prediction

---

## 🧪 Training Details

* Loss Function: Cross-Entropy
* Optimizer: Adam
* Objective: Maximize likelihood of correct next movie

---

## 📊 Example Recommendations

Input sequence:

* Reservoir Dogs
* Dogma
* Lilo & Stitch

Predicted next movies:

* North by Northwest
* The Deer Hunter
* Chasing Amy

---

## 📈 Results & Evaluation

(*You MUST fill this section — critical for credibility*)

Suggested metrics to include:

* Top-K Accuracy (Top-5 / Top-10)
* Hit Rate
* Perplexity (optional)

Example format:

* Top-5 Accuracy: XX%
* Top-10 Accuracy: XX%

Without this section, the model’s effectiveness cannot be validated.

---

## ⚖️ Comparison with Traditional Methods

| Method                  | Sequence Awareness | Context Understanding |
| ----------------------- | ------------------ | --------------------- |
| KNN                     | ❌ No               | ❌ Limited             |
| SVD                     | ❌ No               | ❌ Limited             |
| Transformer (This Work) | ✅ Yes              | ✅ Strong              |

---

## 🧠 Key Learnings

* How Transformers generalize beyond NLP
* Importance of sequence modeling in recommendations
* Role of attention in capturing user behavior
* Data pipeline design for large-scale sequential systems

---

## ⚠️ Limitations

* Trained on sampled dataset (not full scale)
* No hyperparameter optimization
* Cold-start problem not addressed

---

## 🚧 Future Improvements

* Incorporate temporal embeddings
* Hybrid model (content + collaborative)
* Fine-tune with larger dataset
* Deploy as real-time recommendation API

---

## 🎥 Demo

https://drive.google.com/file/d/1zblcSgEyVbHYxe5F_LK7qHxMqzkp1MwW/view?usp=sharing
