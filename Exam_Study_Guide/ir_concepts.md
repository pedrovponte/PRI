# IR Concepts

## Questions

### ➡️ What is… a document, a collection, a term, a bag of words?

- **Document:** data that is organized into a self-contained, usually unstructured or semi-structured instance; units that are returned by an IR system in response to a query;
- **Collection:** the set of all documents used by an IR system;
- **Term:** indexed units that form a document (usually words);
- **Bag of words:** representation of a document as a set of words, where ordering is ignored but the number of occurrences of each word is key.

### ➡️ Define stemming

Stemming refers to a heuristic process that chops off the ends of words in the hope of reducing inflectional forms.

### ➡️ What is… an inverted index, a vocabulary, a postings list?

- **Inverted Index:** mapping of terms to the documents where those terms occur; aditional information such as frequecy or position where they occur can also be stored;
- **Vocabulary:** list of terms of a document in the collection;
- **Postings List:** set of all documents where a term appears; can contain information about the position of the term occurrences inside each document). 

### ➡️ What is… an information need, a query, a results list?

- **Information Need:** is the topic about which the user wants to know more;
- **Query:** is what the user conveys to the computer in an attempt to communicate the information need;
- **Results list:** ranked list of documents in the collection which match a particular query.

### ➡️ What is a relevant result in a results list?

A result is relevant if it is one that the user perceives as containing information of value with with respect to their personal information need, not necessarily a result which contains all the terms of the query.