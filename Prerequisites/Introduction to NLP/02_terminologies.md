### NLP Basic Terminologies & Tokenization

In Natural Language Processing (NLP), **tokenization** is a fundamental process that breaks down a given text into smaller units called **tokens**. These tokens can be individual words or sentences, depending on the type of tokenization.

The following are the key terms you need to know:

* **Corpus**: The entire body of text you're working with, typically a paragraph or a collection of documents.
* **Documents**: Individual sentences within the corpus.
* **Vocabulary**: The set of all **unique** words present in the corpus.
* **Words**: The individual units of text, which are also considered tokens after word-level tokenization.

***

### What is Tokenization?

Tokenization is a crucial first step in most NLP pipelines. Its purpose is to prepare text for further processing by converting it into a structured format that can be easily analyzed by a computer.

There are two main types of tokenization:

* **Sentence Tokenization**: The process of splitting a corpus into a list of sentences. Punctuation marks like periods (.), question marks (?), and exclamation points (!) are typically used as delimiters.

    **Example:**
    **Corpus:** "My name is Krish. I have an interest in teaching. Machine learning and NLP and deep learning and DL."

    **Tokens (Sentences):**
    1.  "My name is Krish."
    2.  "I have an interest in teaching."
    3.  "Machine learning and NLP and deep learning and DL."

* **Word Tokenization**: The process of splitting a sentence into a list of individual words.

    **Example:**
    **Sentence:** "My name is Krish."

    **Tokens (Words):** "My", "name", "is", "Krish"

***

### Example Walkthrough: Vocabulary and Words

Let's consider the following corpus to illustrate the concepts of vocabulary and words:

**Corpus:** "I like to drink apple juice. My friend likes mango juice."

* **Total Words**: By counting every word, we find there are 11 words in total.
* **Vocabulary (Unique Words)**: By listing each word only once, we get the vocabulary.
    1.  I
    2.  like
    3.  to
    4.  drink
    5.  apple
    6.  juice
    7.  My
    8.  friend
    9.  likes
    10. mango

There are **10 unique words** in the vocabulary. Note that "like" and "likes" are considered different words in this count. Tokenization is essential because it allows us to handle and process these words individually before converting them into numerical vectors for machine learning models. 