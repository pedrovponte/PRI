# Entity-oriented Search

## Questions

### ➡️ What is entity-oriented search? What is necessary to implement it?

Entity-Oriented Search is the search paradigm of organizing and accessing information centered around entities (such as people, organizations, places or media), and their attributed and relationships. Implementing it requires having a knowledge base, which is a large, structured repository of information regarding entities and the relationships between them.

### ➡️ Describe the challenges and techniques associated with… building entity descriptions, entity ranking, entity linking.

- **Building entity descriptions:** when our main goal is to select entities that match an ad hoc, textual query, we can approach the problem similarly to document retrieval by constructing documents that aggregate all existing information about entities and applying the indexing and ranking techniques used in document retrieval. There are several techniques for constructing entity descriptions depending on the type of data:
    - **Unstructured data:** manually annotate mentions to specific entities or use automated linking;
    - **Semi-Structured data:** identify specific segments of the document using the markup structure (HTML scraping / parsing) which then map fields in the entity description; include a catch-all field which concatenates the content of all other fields;
    - **Structured data:** consider the immediate vicinity of a node (statements where it appears as subject or object); for knowledge bases with a large number of attributes, collapse attributes or relationships of the same type into a single field or consider only the most important predicates.
- **Entity ranking:** process of ranking entities that match a particular query; we can build entity descriptions, consider these as documents and user retrieval models for a document ranking such as vector space, probabilistic and language models;
- **Entity linking:** process of identifying mentions to specific entities in text and linking it to entities stored in a knowledge base. NLP can be used to automatically detect entity mentions. An entity linking system tackles three main challenges: mention detection (detecting potential entity mentions), candidate selection (selecting potential entities the mention could be referring to) and disambiguation (using context information to choose the correct entity). A possible approach is to build a dictionary containing entity surface forms (name variants), checking all the document's n-grams against this dictionary and filtering out undesired entities.

### ➡️ Describe the data sources typically required for entity oriented search and its characteristics.

A knowledge base is comprised of a large set of assertions about the world. Resource Description Framework (RDF) is a language designed to describe "things", which are referred to as resources. Each resource is assigned a Uniform Resource Identifier (URI), making it uniquely and globally identifiable. Each RDF statement is a triple, consisting of subject (a URI, denoting a resource), predicate (URI, corresponding to a relationship or property of the subject) and object (URI, referring to another resource, or a literal). This way of storing information about entities showcases the strong ties between Entity-Oriented Search and the Property Graph Model and Triplestore Databases.