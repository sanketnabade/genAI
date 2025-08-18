## One-hot encoding

One-hot encoding is a simple yet foundational method in NLP for converting text data into a numerical format that machine learning models can understand. It represents each word as a binary vector where only one element is `1` and all others are `0`. The length of this vector is equal to the size of the entire vocabulary.

### How it Works ⚙️

1.  **Identify the Vocabulary**: First, all unique words from the text documents are collected to form a vocabulary. For example, from the documents "The food is good," "The food is bad," and "Pizza is amazing," the unique words are `{'the', 'food', 'is', 'good', 'bad', 'pizza', 'amazing'}`. The vocabulary size is 7.

2.  **Assign a Vector to Each Word**: Each word in the vocabulary is assigned a unique index. A one-hot vector is then created for each word, with a `1` at its corresponding index and `0` everywhere else.

| Word      | Vector Representation   |
| :-------- | :---------------------- |
| `the`     | `[1, 0, 0, 0, 0, 0, 0]` |
| `food`    | `[0, 1, 0, 0, 0, 0, 0]` |
| `is`      | `[0, 0, 1, 0, 0, 0, 0]` |
| `good`    | `[0, 0, 0, 1, 0, 0, 0]` |
| `bad`     | `[0, 0, 0, 0, 1, 0, 0]` |
| `pizza`   | `[0, 0, 0, 0, 0, 1, 0]` |
| `amazing` | `[0, 0, 0, 0, 0, 0, 1]` |

3.  **Represent a Document as a Matrix**: A document or sentence is represented as a matrix where each row is the one-hot vector for a word in that sentence. For example, "The food is good" would be a 4x7 matrix.

| Document           | Matrix Representation                                                  |
| :----------------- | :--------------------------------------------------------------------- |
| "The food is good" | `[[1,0,0,0,0,0,0], [0,1,0,0,0,0,0], [0,0,1,0,0,0,0], [0,0,0,1,0,0,0]]` |

---

### Advantages & Disadvantages of One-Hot Encoding

| Advantage                                                                                                                                                               | Disadvantage                                                                                                                                                                                                                                                           |
| :---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Easy to Implement** 🛠️: Libraries like `scikit-learn` and `pandas` provide straightforward functions (`OneHotEncoder`, `pd.get_dummies`) to perform one-hot encoding. | **Sparse Matrix** 📉: Vectors consist mostly of zeros, which can lead to inefficient storage and computation and can also cause **overfitting**.                                                                                                                       |
|                                                                                                                                                                         | **Variable Input Size** 📐: Since each word is represented by its own vector, sentences of different lengths result in matrices of varying sizes. Most machine learning models require a fixed-size input.                                                             |
|                                                                                                                                                                         | **Lack of Semantic Meaning** 🧠: One-hot encoding treats every word as a completely independent entity. The vectors for similar words like "food" and "pizza" are orthogonal (perpendicular) to each other, so the model can't understand their semantic relationship. |
|                                                                                                                                                                         | **Out of Vocabulary (OOV) Problem** 🚫: If a new word appears in a test set that wasn't in the training vocabulary, it cannot be encoded. This is a major limitation.                                                                                                  |
|                                                                                                                                                                         | **Scalability Issues** 📈: As the vocabulary grows, the vectors become extremely long and sparse, increasing memory usage and computational complexity.                                                                                                                |
