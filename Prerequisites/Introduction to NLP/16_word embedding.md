## 1. Introduction to Word Embeddings

In Natural Language Processing (NLP), **Word Embedding** is a technique used to represent words for text analysis. It typically converts words into **real-valued vectors**.

The core objective is to encode the meaning of the word such that words capable of being used in similar contexts are mathematically closer to each other in the vector space.

### 1.1. Core Concept and Intuition

The fundamental idea is mapping semantic similarity to geometric proximity. If we convert words into vectors and plot them on a graph (often using dimensionality reduction techniques like **PCA** to visualize them in 2D), similar words group together.

**Analogy:**
Imagine a 2D graph representing "emotions."

- **Case A:** The words **"Happy"** and **"Excited"** have similar meanings. Their vectors will point to very similar coordinates, meaning the distance between them is **small**.
- **Case B:** The word **"Angry"** is the opposite of happy. Its vector will point to a coordinate far away, meaning the distance between "Happy" and "Angry" is **large**.

---

## 2. Classification of Embedding Techniques

The techniques used to convert words or sentences into vectors can be broadly categorized into two main types based on their underlying approach.

### 2.1. Count or Frequency Based Methods

These are traditional techniques that rely on the occurrence statistics of words. While they convert text to vectors, they often suffer from disadvantages like high sparsity (too many zeros in the vectors) and lack of semantic meaning capture.

**Examples discussed previously:**

- **One Hot Encoding**
- **Bag of Words (BoW)**
- **TF-IDF** (Term Frequency-Inverse Document Frequency)

### 2.2. Deep Learning Based Methods

These methods utilize trained neural network models to generate embeddings. They significantly outperform frequency-based methods by solving issues like sparsity and capturing complex semantic relationships.

**Key Model:** **Word2Vec**

- Word2Vec creates efficient, dense vector representations.
- It can be trained from scratch on large datasets or accessed via pre-trained models (e.g., Google’s pre-trained model which is approx 1.5GB).

---

## 3. Word2Vec Architectures

Word2Vec is a specific deep learning technique for word embeddings. To understand how it trains, one requires prerequisite knowledge of Artificial Neural Networks (ANN), Loss Functions, and Optimizers.

Word2Vec generally utilizes one of two specific architectures to learn these vector representations:

### 3.1. CBOW (Continuous Bag of Words)

CBOW is a model architecture that tries to predict a **target word** based on the context of the surrounding words (context words).

### 3.2. Skip Gram

Skip Gram is the inverse of CBOW. It tries to predict the **surrounding context words** given a specific target word.

Both techniques aim to optimize the vector weights to minimize loss, resulting in vectors that capture deep semantic meanings.

---
