# IR Concepts

## Questions

### ➡️ What is the bag of words model for a document?

The bag of words model for a document is the representation of a document as a set of words, where ordering is ignored but the number of occurrences of each word is key.

### ➡️ What is… term frequency, collection frequency, document frequency, inverse document frequency?

- **Term frequency:** the number of occurrences of a term in a document;
- **Collection frequency:** total number of occurrences of a term in the collection;
- **Document frequency:** number of documents in the collection that contain a term;
- **Inverse document frequency:** commonly used in conjunction with term frequency to form tf-idf, idf is given by the formula `log(N / df`, meaning that the inverse document frequency of a term is higher when that term appears in a lower portion of the documents in the collection.

### ➡️ How do you calculate tf-idf weights?

`tf-idf(t,d) = tf(t,d) * idf(t)`

tf-idf<sub>t,d</sub> assigns to term t a weight in document d that is:
- highest when t occurs many times in a small number of documents (thus lending high discriminating power to those documents);
- lower when the term occurs fewer times in a document, or occurs in many documents (thus offering a less pronounced relevance signal);
- lowest when the term occurs in virtually all documents.

### ➡️ How do you rank documents in the vector model?

In the vector model, documents and queries are represented as vectors in an n-dimensional space (being n the number of terms in the query), and documents are ranked using cosine similarity (the score of each document is equal to the angle between that document's vector and the query vector, so smaller angles correspond to a higher score).

## Exercises