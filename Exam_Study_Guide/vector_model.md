# IR Concepts

## Questions

### ➡️ What is the bag of words model for a document?

The bag of words model for a document is the representation of a document as a set of words, where ordering is ignored but the number of occurrences of each word is key.

### ➡️ What is… term frequency, collection frequency, document frequency, inverse document frequency?

- **Term frequency:** the number of occurrences of a term in a document;
- **Collection frequency:** total number of occurrences of a term in the collection;
- **Document frequency:** number of documents in the collection that contain a term;
- **Inverse document frequency:** commonly used in conjunction with term frequency to form tf-idf, idf is given by the formula `log(N / df)`, meaning that the inverse document frequency of a term is higher when that term appears in a lower portion of the documents in the collection.

### ➡️ How do you calculate tf-idf weights?

`tf-idf(t,d) = tf(t,d) * idf(t)`

tf-idf<sub>t,d</sub> assigns to term t a weight in document d that is:
- highest when t occurs many times in a small number of documents (thus lending high discriminating power to those documents);
- lower when the term occurs fewer times in a document, or occurs in many documents (thus offering a less pronounced relevance signal);
- lowest when the term occurs in virtually all documents.

### ➡️ How do you rank documents in the vector model?

In the vector model, documents and queries are represented as vectors in an n-dimensional space (being n the number of terms in the query), and documents are ranked using cosine similarity (the score of each document is equal to the angle between that document's vector and the query vector, so smaller angles correspond to a higher score).

## Exercises

### 6.8 Why is the idf of a term always finite?

If we assume that DF(T) != 0 (i.e. that the respective query term appears at least once, we can give an upper bound for the IDF (for DF(T) = 1) as well as a lower bound (for DF(T) = N)). Because we are dealing with a fixed, finite document set, there also is a finite set of possible values for the IDF which are all between these two extreme values.

### 6.9 What is the idf of a term that occurs in every document? Compare this with the use of stop word lists.

It is 0 (log(N/N) = log(1) = 0). For a word that occurs in every document, putting it on the stop list has the same effect as idf weighting: the word is ignored.

### 6.10 Consider the table of term frequencies for 3 documents denoted Doc1, Doc2, Doc3 in Figure 6.9. Compute the tf-idf weights for the terms car, auto, insurance, best, for each document, using the idf values from Figure 6.8.

tf-idf<sub>car,Doc1</sub> = 27 * 1.65 = 44.55
tf-idf<sub>car,Doc2</sub> = 4 * 1.65 = 6.6
tf-idf<sub>car,Doc3</sub> = 24 * 1.65 = 39.6

tf-idf<sub>auto,Doc1</sub> = 3 * 2.08 = 6.24
tf-idf<sub>auto,Doc2</sub> = 33 * 2.08 = 68.64
tf-idf<sub>auto,Doc3</sub> = 0 * 2.08 = 0

tf-idf<sub>insurance,Doc1</sub> = 0 * 1.62 = 0
tf-idf<sub>insurance,Doc2</sub> = 33 * 1.62 = 53.46
tf-idf<sub>insurance,Doc3</sub> = 29 * 1.62 = 46.98

tf-idf<sub>best,Doc1</sub> = 14 * 1.5 = 21
tf-idf<sub>best,Doc2</sub> = 0 * 1.5 = 0
tf-idf<sub>best,Doc3</sub> = 17 * 1.5 = 25.5

### 6.11 Can the tf-idf weight of a term in a document exceed 1?

Yes, as we can see in exercise 6.10.

### 6.15 Recall the tf-idf weights computed in Exercise 6.10. Compute the Euclidean normalized document vectors for each of the documents, where each vector has four components, one for each of the four terms.

**Document 1**

```
lenght = sqrt(44.55^2 + 6.24^2 + 0^2 + 21^2) = 49.65

v = (0.897, 0.126, 0, 0.423)
```

**Document 2**

```
lenght = sqrt(6.6^2 + 68.64^2 + 53.46^2 + 0^2) = 

v = (0.076, 0.788, 0.613, 0)
```

**Document 3**

```
lenght = sqrt(39.6^2 + 0^2 + 46.98^2 + 25.5^2) = 66.52

v = (0.595, 0, 0.706, 0.383)
```

### 6.16 Verify that the sum of the squares of the components of each of the document vectors in Exercise 6.15 is 1 (to within rounding error). Why is this the case.

Doc1: 0.897<sup>2</sup> + 0.126<sup>2</sup> + 0.423<sup>2</sup> = 0.999414

Doc2 = 0.076<sup>2</sup> + 0.788<sup>2</sup> + 0.613<sup>2</sup> = 1.002489

Doc3 = 0.595<sup>2</sup> + 0.706<sup>2</sup> + 0.383<sup>2</sup> = 0.99915

Because they’re normalized (unit) vectors.

### 6.17 With term weights as computed in Exercise 6.15, rank the three documents by computed score for the query `car insurance`, for each of the following cases of term weighting in the query:

#### 1. The weight of a term is 1 if present in the query, 0 otherwise.

q = (1, 0, 1, 0)

s1 = (1, 0, 1, 0) . (0.897, 0.126, 0, 0.423) = 0.897

s2 = (1, 0, 1, 0) . (0.076, 0.788, 0.613, 0) = 0.076 + 0.613 = 0.689

s3 = (1, 0, 1, 0) . (0.595, 0, 0.706, 0.383) = 0.595 + 0.706 = 1.301

Ranking: Doc3, Doc1, Doc2

#### 2. Euclidean normalized idf.

idf = (1.65, 2.08, 1.62, 1.5)

q = (1.65, 0, 1.62, 0)

length = sqrt(1.65<sup>2</sup> + 1.62<sup>2</sup>) = 2.312

q<sub>norm</sub> = (1.65/2.312, 0, 1.62/2.312, 0) = (0.714, 0, 0.701, 0)

s1 = (0.714, 0, 0.701, 0) . (0.897, 0.126, 0, 0.423) = 0.640

s2 = (0.714, 0, 0.701, 0) . (0.076, 0.788, 0.613, 0) = 0.054 + 0.430 = 0.484

s3 = (0.714, 0, 0.701, 0) . (0.595, 0, 0.706, 0.383) = 0.424 + 0.495 = 0.920

Ranking: Doc3, Doc1, Doc2