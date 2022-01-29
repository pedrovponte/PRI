# IR Tasks and Systems

## Questions

### ➡️ What is the difference between information retrieval and data retrieval?

Data retrieval generally deals with highly structured data, and aims at finding the subset of items which are valid for a particular query (ex: relational databases). On the other hand, information retrieval systems generally deal with semi-structured or unstructured data, and query results are ranked based on relevance. In data retrieval, only items that are an exact match are returned, whereas information retrieval allows for partial matches, and a document which contains all search terms can still be considered irrelevant to the query.

### ➡️ Give examples of IR and data retrieval systems

IR -> web search systems
DR -> relational databases

### ➡️ Give some examples of retrieval tasks evaluated in TREC

- Deep Learning
- Precision Medicine
- Podcast Search
- Health Misinformation

### ➡️ What are the modules of an IR system?

An IR system is generally split into the following modules:
- **Document collection:** how documents are stored;
- **Indexing:** how indices are created from documents to provide search functionality;
- **Query processing:** deals with the expected format of queries and how the system maps them to a list of ranked search results;
- **Evaluation:** what metrics are used to gauge the effectiveness / efficiency of the search system (such as precision, recall, query throughput, etc).