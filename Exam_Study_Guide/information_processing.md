# Information Processing

## Questions

### ➡️ Distinguish between data, metadata, and information

* **Data** is a measurement of something on a certain scale (for example 10ºC or 20m);
* **Metadata** is data about data, not the content of data but data providing information about one or more aspects of the data, such as description (date, time, author), structure (format, version), administrative (permissions), legal, etc;
* **Information** is data that is interpreted within a specific context, it's data that has been processed, organized and structured (for example, the temperature in Porto yesterday at noon was 11ºC).

### ➡️ Identify and describe the phases of a typical information lifecycle

* **Occurrence:** information is generated or discovered;
* **Transmission:** information is shared / retrieved / accessed;
* **Processing / Management:** information is refined / validated / modified / indexed / filtered / sorted / stored ...;
* **Usage:** information is explored and used to guide decision-making or as the basis of a system or systems.

### ➡️ Describe typical data processing patterns, pipelines and frameworks, e.g. ETL, EtLT, OSEMN

* **ETL**, or Extract-Transform-Load, is a data processing pattern where data is obtained from the source system, transformed into suitable format and subsequently loaded into the desired application;
* For systems capable of handling large volumes of data, a new pattern emerged: **ELT**, where data is first loaded and then transformed by experts in the domain. This is a pattern more well-suited to the division of responsibilities in multidisciplinary teams. EtLT is a variation of ELT that introduces a small transformation step before the loading, typically associated with data cleaning;
* **OSEMN** presents a series of data processing steps (Obtain, Scrub, Explore, Model, Interpret), but for many projects these steps aren't always followed in a linear fashion.

### ➡️ Describe the challenges associated with data processing

Data processing tackles a variety of challenges, such as:
- Data is available in several different formats, some more structured and well-defined than others;
- Data often contains missing or duplicate values, deciding how these should be handled is an important step that frequently demands specific domain knowledge;
- Data can contain outliers, which can either be useful data points in some domains or observations that distort statistics and hinder data analysis;
- Normalization, discretization and the synthesis of new attributes are often used to increase the usefulness of data;
- Data can be of poor quality or outdated and have unsuitable dimensions, requiring filtering or sampling procedures.

### ➡️ Identify and describe challenges and techniques related to: data cleaning, data preparation, and data presentation

* **Data cleaning:** duplicate values, missing values, inconsistent or invalid values, outdated values, outliers;
* **Data preparation:** normalization, discretization, sysntesis of new data, format conversion;
* **Data presentation:** adjusting how data is presented depending on the target audience (more or less technical), investigating data quality and properties, justifying the existence of certain properties or relationships; many types of visualizations (bar charts, box plots, line plots, scatter plots, histograms).

### ➡️ Describe the importance of data pipelines and how Makefiles can be used to implement them

Data collection and preparation is usually an ad-hoc and exploratory process, easily leading to a dispersion in threads and activities. These problems can be prevented by designing and maintaining a well-documented, versionable and reproducible data processing pipeline, similarly to how the development of other types of software is handled.
The Make build tool lets us define targets and rules that should be followed in order to generate them. Targets can depend on the existence of other files, forming a dependency graph. In the context of data processing pipeline, we could have targets for downloading an HTML file off the web, extracting segments using BeautifulSoup or converting between different data formats.