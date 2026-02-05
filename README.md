# Collaborative_Movie_Recommendation_System
## 📌 Project Overview

This project implements a **collaborative movie recommendation system** using the **Netflix Prize Dataset** and a **Transformer architecture**.

Instead of traditional recommendation methods (like KNN or SVD), this system models **user watch history as a sequence**, similar to how Large Language Models (LLMs) model text.

> **Key idea:**
> Movies = tokens
> User history = sentence
> Predict next movie = next-token prediction (GPT logic)

This project is designed to **deeply understand Transformers and LLM fundamentals**, not just to build a recommender.

---

## 🎯 Objectives

* Understand collaborative filtering from first principles
* Learn how **sequential recommendation** works
* Apply **Transformer architecture** to non-text data
* Bridge the conceptual gap between **Recommender Systems and LLMs**
* Focus on **code understanding and data flow**, not just execution

---

## 📂 Dataset Used

**Netflix Prize Dataset** (Kaggle)

* ~17,770 movies
* ~480,000 users
* ~100 million ratings (sampled for feasibility)

### Files Used:

* `movie_titles.csv` – movie metadata
* `combined_data_1.txt` – user ratings (sampled)

---

## 🧠 Core Concept

Traditional recommender systems predict ratings:

```
User + Movie → Rating
```

This project predicts **next movie** instead:

```
(Movie₁, Movie₂, Movie₃) → Movie₄
```

This is the **same training objective used in GPT models**.

---

## 🏗️ Project Architecture

```
Netflix Dataset
      ↓
Data Cleaning & Parsing
      ↓
Filter Positive Ratings (≥ 4)
      ↓
User Watch Sequences
      ↓
GPT-style Input–Target Pairs
      ↓
Padding & Batching
      ↓
Transformer Encoder
      ↓
Next-Movie Prediction
```

---

## 🧹 Data Processing Steps

### 1. Load & Clean Data

* Parse raw Netflix text files
* Merge movie titles with ratings
* Store clean data in `netflix_final.csv`

### 2. Filter Ratings

Only ratings ≥ 4 are kept to model **user preferences**, not dislikes.

### 3. Tokenization

Movie IDs are converted to **continuous integer tokens**, just like word tokenization in NLP.

---

## 🔄 Sequence Construction (Key Learning)

For a user who watched:

```
[10, 25, 80, 91]
```

Training samples created:

```
[10]        → 25
[10, 25]    → 80
[10, 25, 80]→ 91
```

This is **exactly how GPT is trained**.

---

## 📦 Dataset Class

A custom PyTorch `Dataset`:

* Breaks user history into input → target pairs
* Pads sequences to fixed length
* Outputs tensors suitable for Transformer input

---

## 🤖 Model Architecture

### Transformer-Based Recommender

* **Embedding Layer**: Movie → Vector
* **Transformer Encoder**:

  * Multi-head self-attention
  * Learns relationships between past movies
* **Linear Output Layer**:

  * Predicts probability over all movies
---

## 🏋️ Training Objective

* **Loss Function**: Cross-Entropy Loss
* **Optimizer**: Adam
* **Goal**: Maximize probability of correct next movie

---

## 🔍 Recommendation Logic

Given a sequence of watched movies:

1. Convert titles → movie tokens
2. Pad to fixed length
3. Pass through Transformer
4. Select top-K predicted movies
5. Convert tokens → movie titles

---

## 📊 Example Output

**User watched:**

```
Reservoir Dogs
Dogma
Lilo and Stitch
```

**Recommended movies:**

```
North by Northwest
The Deer Hunter
Chasing Amy
```

Recommendations are based on **collaborative patterns across all users**.

---

## 🧠 Why This Project Matters

This project teaches:

* How Transformers work beyond text
* Why padding, batching, and tokenization exist
* How LLMs learn from sequences
* How attention captures long-term dependencies
---

## ⚠️ Limitations

* Sampled dataset used for feasibility
* Not optimized for large-scale deployment

---

## 🚀 Future Improvements

* Add frontend / UI
---

## 🧑‍🏫 Learning Outcome

This project prioritizes:

* Understanding over complexity
* Flow of data over fancy code
* Conceptual clarity for LLM readiness

---



