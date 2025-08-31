N-grams are a way to capture the order and context of words in a text by considering contiguous sequences of $n$ words. While the Bag of Words (BoW) model treats each word independently, ignoring their order, N-grams help solve this by creating features out of word combinations. This is especially important for sentences with similar words but different meanings, such as "The food is good" versus "The food is not good."

---

### The Problem with Bag of Words

The **Bag of Words** model only cares about the presence or frequency of individual words. It fails to capture the grammatical structure or semantic relationships between them. For instance, in the sentences "The food is **good**" and "The food is **not good**," BoW would create very similar vectors because only the word "not" distinguishes them. A machine learning model might struggle to understand that these two sentences have opposite meanings.

---

### How N-grams Work

An **N-gram** is a sequence of $n$ words. By generating features from these word sequences, we can preserve more context and word order than with single words (unigrams) alone.

- **Unigrams (n=1)**: Individual words. Example: "food", "is", "good".
- **Bigrams (n=2)**: Two-word sequences. Example: "food is", "is good".
- **Trigrams (n=3)**: Three-word sequences. Example: "food is good".

Let's apply this to our example sentences, excluding stopwords:

- **Sentence 1**: "food is good"
- **Sentence 2**: "food is not good"

|                | **Unigrams**    | **Bigrams**        | **Trigrams**  |
| :------------- | :-------------- | :----------------- | :------------ |
| **Sentence 1** | food, good      | food good          | food good     |
| **Sentence 2** | food, not, good | food not, not good | food not good |

By using bigrams, we create new features like **"food good"** and **"not good"**. The presence of **"not good"** in the second sentence becomes a strong signal to the model that the sentiment is negative, providing more discriminatory power than the word "not" on its own.

---

### Implementing N-grams with scikit-learn

Libraries like scikit-learn make it easy to incorporate N-grams into your text vectorization pipeline. The `CountVectorizer` and `TfidfVectorizer` classes have an `ngram_range` parameter that you can use.

- `ngram_range=(1, 1)`: Creates **unigrams** only (the default behavior).
- `ngram_range=(1, 2)`: Creates **unigrams and bigrams**.
- `ngram_range=(2, 2)`: Creates **bigrams only**.
- `ngram_range=(1, 3)`: Creates **unigrams, bigrams, and trigrams**.

This flexibility allows you to customize the model to the specific needs of your task, balancing between richer context and higher dimensionality. For many NLP problems, using a combination of unigrams and bigrams (`ngram_range=(1, 2)`) is a common and effective approach.
