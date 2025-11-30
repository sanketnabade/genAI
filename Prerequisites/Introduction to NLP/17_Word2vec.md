## 1. Introduction to Word2Vec

**Word2Vec** is a specific deep learning-based technique for Natural Language Processing (NLP), published by **Google in 2013**.

Unlike previous methods (like Bag of Words or TF-IDF) which produce **sparse matrices** (mostly zeros) and do not capture context, Word2Vec produces **dense vector representations**. Its primary goal is to learn word associations from a large corpus of text.

### 1.1. Key Characteristics

- **Semantic Meaning:** Words with similar meanings are placed closer together in the vector space.
- **Dimensionality:** While TF-IDF dimensions equal the vocabulary size (huge), Word2Vec usually creates vectors of fixed dimensions (e.g., 300 dimensions).
- **Neural Network:** It uses a neural network to learn these associations, though the output we care about is the weights (vectors), not the prediction itself.

---

## 2. Feature Representation

The core intuition behind Word2Vec is that every word in a vocabulary can be represented by a set of "features." In a real model trained on billions of words, these features are abstract, but for understanding, we can visualize them as specific attributes.

### 2.1. The Feature Matrix Analogy

Imagine we have a vocabulary (Boy, Girl, King, Queen, Apple, Mango) and we score them against specific features (Gender, Royal, Age, Food).

| Vocabulary | Gender (-1: Male, +1: Female) | Royal | Age  | Food |
| :--------- | :---------------------------- | :---- | :--- | :--- |
| **Boy**    | -1.0                          | 0.01  | 0.03 | 0.02 |
| **Girl**   | +1.0                          | 0.02  | 0.02 | 0.02 |
| **King**   | -0.95                         | 0.95  | 0.75 | 0.05 |
| **Queen**  | +0.93                         | 0.96  | 0.68 | 0.04 |
| **Apple**  | 0.01                          | 0.01  | -0.2 | 0.95 |
| **Mango**  | 0.02                          | 0.00  | -0.1 | 0.96 |

- **Boy vs. Girl:** They are opposite in the "Gender" feature (-1 vs +1) but similar in others (neither are royal, neither are food).
- **Apple vs. Mango:** They have high values for "Food" but near-zero values for "Royal" or "Gender."

**Note:** In Google's pre-trained model (trained on 3 billion words), each word is represented by **300 dimensions** (300 features), though we don't label them "Royal" or "Gender" explicitly—the model learns them automatically.

---

## 3. Vector Arithmetic and Relations

One of the most famous capabilities of Word2Vec is performing algebraic operations on words. Because the vectors capture semantic meaning, we can add and subtract them to find relationships.

### 3.1. The "King - Man + Woman" Equation

If we take the vector for **King**, subtract the vector for **Man**, and add the vector for **Woman**, the resulting vector is mathematically closest to **Queen**.

$$Vector(King) - Vector(Man) + Vector(Woman) \approx Vector(Queen)$$

This proves that the model has learned the semantic concept of "Royalty" and "Gender" and stored them as numerical relationships.

---

## 4. Cosine Similarity

How do we mathematically decide if "Apple" is similar to "Mango"? We calculate the distance between their vectors.

In high-dimensional spaces, we rarely use Euclidean distance (straight line). Instead, we use **Cosine Similarity**.

### 4.1. The Formula

Cosine similarity measures the cosine of the angle ($\theta$) between two vectors.

$$Distance = 1 - CosineSimilarity$$

$$CosineSimilarity = \cos(\theta)$$

![Cosine similarity](https://encrypted-tbn3.gstatic.com/licensed-image?q=tbn:ANd9GcTTl5nn9Y7RX-QqRUxI6YI-USb3y2lVh0KN5e__RamkFW2ovtNmUhCd-QgrLSXYTOVqaUAFNaJqYObe254FxfG1FgjurBMUuSTuWXH_yAYRZKxtfc4)

### 4.2. Interpreting the Angle

- **If $\theta = 0^\circ$ (Parallel):**
  - $\cos(0) = 1$.
  - Distance = $1 - 1 = 0$.
  - **Meaning:** The words are identical or synonyms.
- **If $\theta = 90^\circ$ (Perpendicular):**
  - $\cos(90) = 0$.
  - Distance = $1 - 0 = 1$.
  - **Meaning:** The words are unrelated (e.g., "King" and "Apple").
- **If $\theta = 180^\circ$ (Opposite):**
  - $\cos(180) = -1$.
  - **Meaning:** The words are completely opposite.

### 4.3. Application in Recommender Systems

This logic is used in recommendation engines (like Netflix or Amazon).

- If a user likes _Avengers_, the system looks for vectors close to the _Avengers_ vector in the feature space (e.g., Action, Comic Book).
- _Iron Man_ will have a very small angle ($\theta$) relative to _Avengers_, so it is recommended.

---
