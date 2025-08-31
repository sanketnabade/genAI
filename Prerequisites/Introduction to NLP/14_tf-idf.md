## Term Frequency-Inverse Document Frequency

TF-IDF, short for **Term Frequency-Inverse Document Frequency**, is a text vectorization technique that goes beyond simple word counts. It's a numerical statistic that reflects how important a word is to a document in a collection or corpus. TF-IDF is often more effective than Bag of Words (BoW) because it assigns a higher weight to words that are rare across the entire corpus but frequent within a single document, effectively capturing a word's significance.

---

### How TF-IDF Works 📊

TF-IDF is a product of two components:

1.  **Term Frequency (TF)**: This measures how often a word appears in a document. A word that appears frequently is likely important to that specific document.
    $$
    \text{TF}(\text{word}) = \frac{\text{Number of times a word appears in a sentence}}{\text{Total number of words in that sentence}}
    $$
2.  **Inverse Document Frequency (IDF)**: This measures how rare or common a word is across all documents in the corpus. Words that appear in many documents (like "the" or "is") are less informative, so their IDF value is low. Words that are rare have a high IDF.
    $$
    \text{IDF}(\text{word}) = \log_{e} \left( \frac{\text{Total number of sentences}}{\text{Number of sentences containing the word}} \right)
    $$

The final TF-IDF score is the product of these two values:
$$\text{TF-IDF} = \text{TF} \times \text{IDF}$$

### A Simple Example

Consider a corpus of three preprocessed sentences:

- S1: "good boy"
- S2: "good girl"
- S3: "boy girl good"

The vocabulary is: `{'good', 'boy', 'girl'}`.

1.  **Calculate IDF**:

    - `'good'` appears in 3/3 sentences. IDF(good) = $\log_e(3/3) = 0$.
    - `'boy'` appears in 2/3 sentences. IDF(boy) = $\log_e(3/2) \approx 0.405$.
    - `'girl'` appears in 2/3 sentences. IDF(girl) = $\log_e(3/2) \approx 0.405$.

2.  **Calculate TF-IDF Vectors**:

    - **For S1 ("good boy")**:

      - TF('good') = 1/2. TF-IDF = (1/2) \* 0 = 0.
      - TF('boy') = 1/2. TF-IDF = (1/2) \* 0.405 $\approx$ 0.2025.
      - TF('girl') = 0. TF-IDF = 0.
      - **S1 Vector**: `[0, 0.2025, 0]`

    - **For S2 ("good girl")**:

      - TF('good') = 1/2. TF-IDF = 0.
      - TF('boy') = 0. TF-IDF = 0.
      - TF('girl') = 1/2. TF-IDF = (1/2) \* 0.405 $\approx$ 0.2025.
      - **S2 Vector**: `[0, 0, 0.2025]`

    - **For S3 ("boy girl good")**:
      - TF('good') = 1/3. TF-IDF = (1/3) \* 0 = 0.
      - TF('boy') = 1/3. TF-IDF = (1/3) \* 0.405 $\approx$ 0.135.
      - TF('girl') = 1/3. TF-IDF = (1/3) \* 0.405 $\approx$ 0.135.
      - **S3 Vector**: `[0, 0.135, 0.135]`

Notice how the word "good" gets a score of 0 because it appears in every sentence, making it an unhelpful differentiator. This shows that TF-IDF effectively penalizes common words and highlights unique ones.

---

### Advantages and Disadvantages

| Advantage                                                                                                                                                           | Disadvantage                                                                                                                        |
| :------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------- |
| **Captures Word Importance** 🎯: TF-IDF provides a richer representation by weighting words based on their significance, unlike BoW which treats all words equally. | **Sparsity** 📉: Like BoW, TF-IDF still results in sparse matrices with many zero values, which can be computationally inefficient. |
| **Fixed-Size Input** 📏: It creates fixed-length vectors from varying-length documents, making it suitable for machine learning models.                             | **Out-of-Vocabulary (OOV) Problem** 🚫: It cannot handle new words that were not in the original training vocabulary.               |
| **Simple and Intuitive** 🧠: It's easy to understand and implement, making it a strong baseline model for many text classification tasks.                           | **Ignores Context** 🗣️: It still doesn't capture the semantic relationships between words or their order in a sentence.             |
