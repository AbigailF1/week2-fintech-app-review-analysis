# 📱 Ethiopian Fintech App Review Insights

This project analyzes user feedback from major Ethiopian banking apps on the Google Play Store. It applies Natural Language Processing (NLP) techniques to extract sentiment and thematic patterns, helping stakeholders understand user pain points and priorities in mobile banking experiences.

---

## 🔧 Tools & Libraries

- **Python 3.10+**
- `google-play-scraper` – Fetches Google Play reviews
- `pandas`, `numpy` – Data analysis
- `transformers` – BERT-based sentiment classification
- `spaCy` – Lemmatization and text cleaning
- `scikit-learn` – TF-IDF keyword extraction
- `matplotlib`, `seaborn` – Optional visualization

---

## 🗂️ Project Structure

```
.
├── .github/
│   └── workflows/
│       └── preprocessing.yml              # GitHub Actions workflow for preprocessing
├── cleaned_data/
│   └── cleaned_reviews.csv                # Cleaned and merged raw reviews
├── data/
│   ├── all_banks_reviews.csv              # Combined reviews per bank
│   ├── bank_keywords.csv                  # Keywords grouped by bank
│   ├── bank_of_abyssinia_reviews.csv      # Abyssinia reviews with metadata
│   ├── commercial_bank_of_ethiopia_...    # CBE reviews with metadata
│   ├── dashen_bank_reviews.csv            # Dashen reviews with metadata
│   ├── reviews_with_sentiment.csv         # Reviews + sentiment label & score
│   └── reviews_with_themes.csv            # Reviews + assigned themes
├── results/
│   └── tfidf_top_keywords.csv             # Top TF-IDF keywords per bank
├── task-1/
│   ├── preprocess_reviews.py              # Cleans and structures raw review data
│   └── scrape_reviews.py                  # Scrapes reviews from Google Play Store
├── task-2/
│   ├── aggregate_sentiment.py             # Combines sentiment data
│   ├── assign_themes.py                   # Assigns themes based on keywords
│   ├── extract_keywords.py                # TF-IDF keyword extraction
│   └── sentiment_analysis.py              # Uses BERT for review sentiment classification
├── requirements.txt                       # Python package requirements
├── .gitignore
└── README.md

```

---

## 💡 Key Features

- **Bank Coverage:**  
  Reviews are collected for:

  - Commercial Bank of Ethiopia (CBE)
  - Bank of Abyssinia (BoA)
  - Dashen Bank

- **Review Preprocessing:**

  - Emoji mapping (e.g., 😡 → "angry")
  - Lowercasing, punctuation removal
  - Stopword filtering and lemmatization

- **Sentiment Analysis:**

  - Uses `distilbert-base-uncased-finetuned-sst-2-english`
  - Labels each review as **positive** or **negative**
  - Output saved to `reviews_with_sentiment.csv`

- **Keyword & Theme Extraction:**
  - Top keywords per bank via TF-IDF
  - Keywords grouped into meaningful themes:
    - Login & Access Issues
    - App Reliability
    - UI/UX Design
    - Customer Service

---

## Getting Started

1. **Clone the Repository**

   ```bash
   git clone https://github.com/yourusername/fintech-review-analysis.git
   cd fintech-review-analysis
   ```

2. **Create a Virtual Environment**
   Create a virtual environment and install dependencies:

   ```bash
    python -m venv venv
    venv\Scripts\activate  # On Windows
    # source venv/bin/activate  # On macOS/Linux
    pip install -r requirements.txt

   ```

3. **Run Pipeline**
   Ensure `cleaned_reviews.csv` exists in the `cleaned_data` folder, then run:

   ```bash
    # Scrape or use existing review data
    python task-1/preprocess_reviews.py

    # Apply sentiment analysis
    python task-2/sentiment_analysis.py

    # Extract keywords and assign themes
    python task-2/extract_keywords.py
    python task-2/assign_themes.py

   ```

   Output files will be generated in the `data/` directory.

---

## Insights

This analysis helps developers and banks to:

Detect patterns in negative reviews

Identify app-specific issues by theme

Prioritize feature fixes based on real user feedback
