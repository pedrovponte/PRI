# Web Search

## Questions

### ➡️ What are informational, transactional and navigational information needs?

- **Informational:** seek general information on a broad topic, viewing multiple web pages;
- **Transactional:** is a prelude to the user performing a transaction on the Web, such as purchasing a product, downloading a file or making a reservation;
- **Navigational:** seek the website or home page of a single entity that the user has in mind.

### ➡️ Name some differences between web search and enterprise search.

- The web is of a much larger scale compared to most enterprise search systems;
- Documents on the web vary wildly in terms of language, format, quality, accuracy;
- In the web search, we have to deal with search manipulation, spam, misleading documents;
- Web search users are of a wide variety of backgrounds: queries normally focused on full text search rather tan a more technical syntax.

### ➡️ How do you index images?

Alternate text (or `alt`, which is essentially a description for the image being displayed to improve accessability), as well as file names could be used to index images.

### ➡️ Give examples of ranking signals used by search engines.

- Time of day
- Search location
- PageRank
- HITS
- Previous Searches
- Number of clicks

### ➡️ What are the SCC, IN and OUT components in the view of the web as a bowtie?

- **SCC:** Strongly Connected Component, the pages in this component form a connected graph, meaning that within the SCC we can reach any page from any other page;
- **IN:** Pages that link to pages in SCC. Generally contains newer pages that haven't been referred much yet;
- **OUT:** Pages that are linked to by pages in the SCC, but don't link back to the SCC. Generally contains old pages, pages that are no longer updated, ...