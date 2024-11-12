# Sequence-Tagger-and-Similar-and-Dissimilar-Diseases

1. **Sequence Labeling and Named Entity Recognition (NER) with Conditional Random Fields (CRFs)**

I used a method called Conditional Random Fields (CRFs) for sequence labeling and Named Entity Recognition (NER) tasks. Entity spans are encoded as tags for each token in the text using BIO tagging: "B-" denotes the beginning of an entity span, "I-" denotes inside an entity span, and "O" denotes a non-entity token. In this dataset, the labels are as follows: {“O”: 0, “B-Chemical”: 1, “B-Disease”: 2, “I-Disease”: 3, and “I-Chemical”: 4}. This task used the BioCreative V dataset to train the CRF tagger.

I defined five main features for the model:
- Using the token itself as a feature.
- Extracting basic word features, including the current word, previous word, next word, capitalization, punctuation, numeric features, and suffix length.
- Part of Speech (PoS) tags.
- Dependency parsing to extract sentence syntax.
- WordNet, a lexical database of English, to identify relationships between words.

Incorporating these features enables the model to gain a deeper understanding of language meaning and relationships, which is essential for tasks like NER.

2. **Identifying Similar and Dissimilar Diseases**
   
For the query disease "diabetes," I used two methods to find similar diseases

Method 1: Term-Document Matrices using TF-IDF. I used a TF-IDF vectorizer to convert text into vector form.

Method 2: Word Embeddings. I used a pre-trained GloVe model from Twitter, glove-twitter-25, to convert words into vectors.

The result shows that Word Embeddings did not identify any diseases with the exact term "diabetes" among the top five similar diseases, even though "diabetes" was the query term. For instance, one of the similar diseases identified by Word Embeddings was "myocardial infarction (MI)," which is indirectly related to diabetes since "chronic hyperglycemia in Type 2 diabetes mellitus can cause myocardial infarction (MI)." These two diseases have an indirect relationship, which explains the high similarity score.

In contrast, TF-IDF showed that all of the top five similar diseases contained the word "diabetes" because TF-IDF creates vectors based on word frequency and occurrence across documents.
