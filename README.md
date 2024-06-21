# Keyword_Extraction_Articles
Articles Used: https://aerospace.honeywell.com/us/en/about-us/blogs/in-search-of-artificial-intelligence-and-better-outcomes?utm_source=google&utm_medium=cpc&utm_campaign=23-aero-ww-dsa-blogs&utm_content=dyn-en-lp&gad_source=1&gclid=CjwKCAjwps-zBhAiEiwALwsVYVDcAs1je7oyQrYf0yofFvLKPiJjSNXQ3BYujjC-9l6YDu2bbmhF2BoCUGAQAvD_BwE 
### Summary of the Code and Comparison of TF-IDF vs. TextRank for Keyword Extraction

#### Code Summary:
The provided code demonstrates two methods for extracting keywords from an article fetched from a URL using Python:

1. **TF-IDF (Term Frequency-Inverse Document Frequency)**:
   - **Process**: 
     - The article content is fetched using `requests` and `BeautifulSoup`.
     - Text preprocessing includes tokenization, lowercase conversion, removal of stopwords and punctuation using `nltk`.
     - TF-IDF vectorization is performed using `TfidfVectorizer` from `sklearn.feature_extraction.text`.
     - Top keywords are extracted based on TF-IDF scores.
   - **Advantages**: 
     - Efficient in capturing the importance of terms within a document relative to a corpus.
     - Handles large datasets well and scales with document size.
   - **Parameters**: 
     - `max_df=1`: Ignores terms that appear in all documents (highly frequent terms).
     - `min_df=0.5`: Ignores terms that appear in less than 50% of documents (very rare terms).
   
2. **TextRank**:
   - **Process**: 
     - Uses `spacy` for text processing and dependency parsing.
     - Extracts noun phrases and ranks them based on their frequencies.
     - Top keywords are selected based on frequency rankings.
   - **Advantages**: 
     - Captures semantic relationships and contextually relevant terms.
     - Suitable for extracting key phrases and summarizing text.
   - **Limitations**: 
     - Requires extensive text processing and linguistic analysis.
     - Performance can degrade with noisy or poorly structured text.
   
3. **Evaluation**:
   - **Precision, Recall, and F1-score**:
     - Evaluation metrics are computed to compare the extracted keywords (`tfidf_results` and `textrank_results`) against reference keywords (`reference_keywords`).
     - Metrics provide insights into how well each method identifies relevant keywords compared to a predefined set.
   
4. **Visualization**:
   - **Bar Plot**:
     - Compares precision, recall, and F1-score between TF-IDF and TextRank methods.
     - Demonstrates performance differences graphically.

#### Comparison: TF-IDF vs. TextRank

- **Performance**:
  - **TF-IDF**: 
    - Performs well in identifying keywords based on statistical importance within the document.
    - Effective when keywords are distinguished by their frequency and distribution across the document corpus.
    - Especially suited for scenarios where the importance of a term is related to its frequency within a single document and its rarity across multiple documents.

  - **TextRank**: 
    - Excels in capturing context and semantic relevance by analyzing relationships between terms.
    - Suitable for summarization and extraction of key phrases that encapsulate the main themes of the document.
    - Particularly effective when keywords are not purely frequency-based but depend on their contextual significance and relationships with other terms.

- **Reasons why TF-IDF performs better than TextRank for this scenario**:
  1. **Document Specificity**: TF-IDF directly measures the importance of each term within the document relative to its frequency across all documents. This is beneficial when the goal is to pinpoint specific terms that are highly indicative of the document's content.
  
  2. **Robustness to Noise**: TF-IDF inherently filters out common terms (stopwords) and focuses on distinguishing content-specific keywords. This makes it more robust in scenarios where noisy or less structured text might hinder the performance of more context-sensitive methods like TextRank.
  
  3. **Scalability**: TF-IDF scales well with larger datasets and can handle diverse document collections efficiently. It operates on statistical principles that are computationally efficient and straightforward to implement.

While TextRank offers advantages in capturing semantic relationships and summarizing text, TF-IDF outperforms TextRank in scenarios where the goal is precise identification of document-specific keywords based on statistical importance and frequency considerations.
