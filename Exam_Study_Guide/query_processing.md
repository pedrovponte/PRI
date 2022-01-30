# Query Processing

## Questions

### ➡️ Describe and distinguish between the two query processing techniques — document-at-a-time and term-at-a-time.

- **Document-at-a-time:** the system calculates complete scores for documents by processing all term lists, one document at a time.
- **Term-at-a-time:** the system accumulates scores for documents by processing term lists, one at a time. When all terms are processed, the accumulators contain the final scores of all matching documents.
The document-at-a-time approach requires less memory, since the system does not have to keep track of partial scores, but the term-at-a-time approach can be faster since the system only has to obtain the postings list of each term once.

### ➡️ In what contexts is query transformation / expansion advantageous?

When there is a vocabulary mismatch between the terms in the user's query and the terms in the collection's documents, due to factors such as spelling errors or the usage of synonyms, query transformation / expansion can help improve search results by providing not only exact matches but other similar matches that the system thinks could also be relevant. Relevance feedback can be used to improve the results of ambiguous queries: by providing information on which of the returned documents were relevant, the search results are shifted in the direction of similar documents. It also tackles the problem that users may have trouble formulating a query suitable to their information need, but can easily identify if a document is relevant to it.

### ➡️ What techniques can be used to apply transformations / expansions to user queries?

- Use query log mining to find related expansions;
- Using a dictionary or thesaurus in order to return results that contain synonyms of terms in the query;
- Correcting spelling mistakes (did you mean...), ASCII / case folding;
- Query expansion based on relevance feedback (Rocchio Algorithm in vector space model: query vector is moved closed to the documents that were considered relevant);
- Implicit relevant feedback based on  (results that are clicked are considered relevant).

### ➡️ Identify and describe query expansions techniques, such as relevance feedback or pseudo-relevance feedback.

- **Relevance feedback:** the idea of RF is to involve the user in the retrieval process so as to improve the final result set. In particular, the user gives feedback on the relevance of documents in an initial set of results. Then, the system computes a better representation of the information need based on this feedback and displays a revised set of retrieval results;
- **Pseudo relevance feedback:** provides a method for automatic local analysis. It automates the manual part of relevance feedback, so that the user gets improved retrieval performance without an extended interaction. The method is to do normal retrieval to find an initial set of most relevant documents, to then assume that the top k ranked documents are relevant, and finally to do relevance feedback as before under this assumption.