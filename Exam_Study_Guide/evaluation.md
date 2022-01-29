# Evaluation

## Questions

### ➡️ What is… precision, recall, interpolated precision?

- **Precision:** number of relevant retrieved results / number of retrieved results;
- **Recall:** number of relevant retrieved results / number of relevant results;
- **Interpolated Precision:** the interpolated precision at a certain recall level r is defined as the highest precision found for any recall level r' >= r.

### ➡️ What is… precision at k, R-precision?

- **Precision at k:** precision metric which only considers the top k documents retrieved by the search engine;
- **R-Precision:** precision of the top R documents retrieved, where R is the number ot relevant documents for a given query.

### ➡️ Name the components of a test collection.

A test collection is composed by:
- A document collection;
- A test suite of information needs, expressible as queries;
- A set of relevance judgements, standardly a binary assessment of either relevant or nonrelevant for each query-document pair.

### ➡️ Why is a set of relevance judgements considered a “ground truth” for IR?

A set of relevance judgements are a set of binary statements classifying documents as relevant or nonrelevant with respect to a given information need and therefore can be referred as a "ground truth" with which search documents can be evaluated.

### ➡️ Draw a precision-recall curve for capturing the evolution of precision in the ranked list of results for a query.

### ➡️ What is an average 11-point precision-recall graph for a set of queries?

The average 11-point precision-recall curve is a graph plotting the interpolated precision of an information retrieval (IR) system at 11 standard recall levels, that is, {0.0, 0.1, 0.2, ..., 1.0}. For each recall level, we then calculate the arithmetic mean of the interpolated precision at that recall level for each information need in the test collection.

### ➡️ What is MAP, and do you calculate it for a set of queries in a test collection?

Mean Average Precision is the arithmetic mean of the Average Precision scores for a given set of queries. The Average Precision score is the mean of the precision value obtained for the set of top k documents existing after each relevant document is retrieved.

## Exercises

### 8.1 An IR system returns 8 relevant documents, and 10 nonrelevant documents. There are a total of 20 relevant documents in the collection. What is the precision of the system on this search, and what is its recall?

Precision = 8 / 18 = 0.44

Recall = 8 / 20 = 0.4

### 8.4 What are the possible values for interpolated precision at a recall level of 0?

0 <= p <= 1

### 8.8 Consider an information need for which there are 4 relevant documents in the collection. Contrast two systems run on this collection. Their top 10 results are judged for relevance as follows (the leftmost item is the top ranked search result).

#### a) What is the MAP of each system? Which has a higher MAP?

**System 1**

| | R | N | R | N | N | N | N | N | R | R |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ----
| Precision| 1 | 0.5 | 0.67 | 0.5 | 0.4 | 0.33 | 0.29 | 0.25 | 0.33 | 0.4 |

MAP = AP = (1 + 0.67 + 0.33 + 0.4) / 4 = 0.6

**System 2**

| | N | R | N | N | R | R | R | N | N | N |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ----
| Precision| 0 | 0.5 | 0.33 | 0.25 | 0.4 | 0.5 | 0.57 | 0.5 | 0.44 | 0.4 |

MAP = AP = (0.5 + 0.4 + 0.5 + 0.57) / 4 = 0.493

#### b) Does this result intuitively make sense? What does it say about what is important in getting a good MAP score?

In order to obtain a good MAP score, the relevant documents that are retrieved should be ranked as high as possible in the results list.

#### c) What is the R-precision of each system? (Does it rank the systems the same as MAP?)

**System 1**

R-Precision = 4 / 10 = 0.4

**System 2**

R-Precision = 4 / 7 = 0.57

The R-Precision score is higher for System 2.

### 8.9 The following list of Rs and Ns represents relevant (R) and nonrelevant (N) returned documents in a ranked list of 20 documents retrieved in response to a query from a collection of 10,000 documents. The top of the ranked list (the document the system thinks is most likely to be relevant) is on the left of the list. This list shows 6 relevant documents. Assume that there are 8 relevant documents in total in the collection (R R N N N N N N R N R N N N R N N N N R).

#### a) What is the precision of the system on the top 20?

Precision = 6 / 20 = 0.3

#### b) What is the F1 on the top 20?

Recall = 6 / 8 = 0.75

F1 = (2 * 0.3 * 0.75) / (0.3 + 0.75) = 0.429

#### c) What is the uninterpolated precision of the system at 25% recall?

At 25% recall, the system has retrieved 2 documents and both are relevant, so the uninterpolated precision at 25% recall is 1.

#### d) What is the interpolated precision at 33% recall?

| Recall (%) | P @ Recall |
| ---- | ---- |
| 12.5 | 1.0 |
| 25 | 1.0 |
| 37.5 | 0.33 |
| 50 | 0.36 |
| 62.5 | 0.33 |
| 75 | 0.3 |

As the interpolated precision at a certain recall level r is defined as the highest precision found for any recall level r' >= r, the value for interpolated precision at 33% recall is 0.36.

#### e) Assume that these 20 documents are the complete result set of the system. What is the MAP for the query?

MAP = AP = (1 + 1 + 0.33 + 0.36 + 0.33 + 0.3) / 6 = 0.553

#### f) What is the largest possible MAP that this system could have?

The largest possible is achieved if the next 2 relevant results are ranked as 21th and 22th.

MAP<sub>max</sub> = (1 + 1 + 0.33 + 0.36 + 0.33 + 0.3 + 7 / 21 + 8 / 22) / 8 = 0.502

#### g) What is the smallest possible MAP that this system could have?

MAP<sub>min</sub> = (1 + 1 + 0.33 + 0.36 + 0.33 + 0.3 + 7 / 9999 + 8 / 10000) / 8 = 0.415

#### h) In a set of experiments, only the top 20 results are evaluated by hand. The result in (e) is used to approximate the range (f)–(g). For this example, how large (in absolute terms) can the error for the MAP be by calculating (e) instead of (f) and (g) for this query?

error = max(abs(MAP<sub>20</sub> - MAP<sub>min</sub>), abs(MAP<sub>20</sub> - MAP<sub>max</sub>)) = max(0.138, 0.051) = 0.138