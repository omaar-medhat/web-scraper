# Search Engine Project

## Overview
This project implements a search engine for Twitter data using the PyTerrier framework, natural language processing (NLP) techniques, and a Flask-based web interface. The system processes a dataset of tweets, indexes them for efficient retrieval, and supports query expansion and embedding-based ranking. The user interface mimics a Google-like search experience.

## Features
- **Tweet Preprocessing**: Cleans and normalizes tweet text by removing URLs, handles, special characters, stopwords, and applying Porter stemming.
- **Indexing**: Uses PyTerrier to create an inverted index of processed tweets for fast retrieval.
- **Retrieval Models**: Supports TF-IDF and BM25 ranking models.
- **Query Expansion**: Implements RM3 query expansion to improve retrieval performance.
- **Embedding-Based Ranking**: Uses ELMo and BERT embeddings to compute cosine similarity for ranking.
- **Web Interface**: A Flask application with a Google-like UI, hosted via ngrok for public access.

## Requirements
- Python 3.11
- Libraries: `python-terrier`, `nltk`, `pandas`, `tensorflow`, `tensorflow-hub`, `transformers`, `flask`, `pyngrok`, `pytrec_eval`
- Dataset: `twitter_dataset.csv` (contains `Tweet_ID` and `Text` columns)

## Installation
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Install additional Terrier PRF package:
   ```bash
   git clone https://github.com/terrierteam/terrier-prf/
   cd terrier-prf
   mvn install
   cd ..
   ```
4. Download NLTK data:
   ```python
   import nltk
   nltk.download('punkt')
   nltk.download('stopwords')
   nltk.download('punkt_tab')
   ```

## Usage
1. **Prepare the Dataset**:
   - Place `twitter_dataset.csv` in the project directory.
   - The dataset should have columns `Tweet_ID` and `Text`.

2. **Run the Application**:
   ```bash
   python web_scraper.py
   ```
   - The script processes the dataset, builds the index, and starts the Flask server.
   - A public URL is generated via ngrok for accessing the web interface.

3. **Search**:
   - Open the ngrok URL in a browser.
   - Enter a query in the search bar and click "Search".
   - Results display tweet text and document IDs, ranked by TF-IDF.

## Project Structure
- `web_scraper.py`: Main script for preprocessing, indexing, and running the Flask app.
- `twitter_dataset.csv`: Input dataset of tweets.
- `DatasetIndex/`: Directory storing the PyTerrier index.
- `README.md`: This file.

## Notes
- The dataset is assumed to be located at `/content/twitter_dataset.csv`. Update the path in `web_scraper.py` if necessary.
- The ngrok authentication token is hardcoded. Replace it with your own token for production use.
- ELMo and BERT embeddings require significant computational resources. Ensure sufficient memory and GPU support if available.
- The web interface is basic and uses placeholder links (`http://example.com/doc/{docno}`). Customize link generation for real-world use.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Acknowledgments
- PyTerrier for information retrieval.
- NLTK and Transformers for NLP processing.
- Flask and ngrok for web deployment.
