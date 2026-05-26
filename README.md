# FYPUOWCODE# 🧠 Public Sentiment Analysis of Generative AI Across Social Media Platforms

Analysed 1,500 social media posts across YouTube, X (Twitter), and Reddit to map public sentiment towards Generative AI in 2023 using three different NLP models to compare lexicon-based vs transformer-based approaches.

🔗 [Live Streamlit App](https://appfinal-dprojv6xrpyor4vhlybcxc.streamlit.app/)📓 [Source Code](https://github.com/M-FATEH/FYPUOWCODE.git) 


## Problem Statement

Most existing sentiment analysis studies on Generative AI focus on a single platform using a single model, which risks platform-specific bias and model-dependent conclusions. This project addresses that gap with a multi-platform, multi-model design.


## Key Findings

Reddit and X show broadly consistent, positive-leaning sentiment (~31–38% positive across all models), suggesting text-based platforms produce similar discourse patterns around Generative AI

YouTube is a significant outlier: RoBERTa classified 47% of YouTube comments as negative, compared to 28% on Reddit and X, indicating that video-based platforms provoke stronger emotional reactions

Model choice materially affects conclusions: VADER, TextBlob, and RoBERTa produced notably different results on YouTube, validating the need for a multi-model approach. A study using VADER alone would have significantly underestimated negativity on YouTube


## Tech Stack

| Category | Tools |
|---|---|
| Language | Python |
| Data Collection | YouTube Data API v3, Kaggle datasets |
| Data Processing | pandas, NumPy, NLTK, regex |
| NLP / Sentiment | VADER, TextBlob, RoBERTa (HuggingFace Transformers) |
| Deep Learning | PyTorch |
| Visualisation | Matplotlib |
| Web App | Streamlit |
| IDE | Jupyter Notebook, VS Code |

---

## System Architecture

The project follows a 4-layer data pipeline:

Layer 1 — Data Collection
  ├── Reddit (Kaggle CSV)
  ├── X / Twitter (Kaggle CSV)
  └── YouTube (Data API v3)
          ↓
Layer 2 — Data Processing
  ├── Keyword filtering (Generative AI, GenAI, AI, Artificial Intelligence)
  ├── Text cleaning (URLs, hashtags, mentions, contractions)
  ├── Tokenisation & lemmatisation (NLTK)
  └── Random sampling (n=500 per platform, random_state=42)
          ↓
Layer 3 — Sentiment Analysis
  ├── VADER (lexicon-based)
  ├── TextBlob (lexicon-based, polarity + subjectivity)
  └── RoBERTa — cardiffnlp/twitter-roberta-base-sentiment (transformer-based)
          ↓
Layer 4 — Visualisation
  ├── Matplotlib charts (Jupyter Notebook)
  └── Interactive Streamlit web app




## 📊 Results Summary

### RoBERTa (Most Accurate Model)

| Platform | Negative | Neutral | Positive |
|---|---|---|---|
| Reddit | 28% | 35% | 31% |
| X (Twitter) | 28% | 35% | 31% |
| YouTube | **47%** | 16% | 37% |

### VADER

| Platform | Negative | Neutral | Positive |
|---|---|---|---|
| Reddit | 27% | 37% | 28% |
| X (Twitter) | 27% | 37% | 28% |
| YouTube | **44%** | 44% | — |

### TextBlob

| Platform | Negative | Neutral | Positive |
|---|---|---|---|
| Reddit | 28% | 25% | 38% |
| X (Twitter) | 28% | 25% | 38% |
| YouTube | **41%** | 48% | 22% |

---

## 🚀 How to Run

### 1. Clone the repository
```bash
git clone https://github.com/M-FATEH/FYPUOWCODE.git
cd FYPUOWCODE
```

### 2. Install dependencies
```bash
pip install pandas numpy nltk transformers torch textblob vaderSentiment streamlit matplotlib
```

### 3. Download NLTK data
```python
import nltk
nltk.download('punkt')
nltk.download('stopwords')
nltk.download('wordnet')
```

### 4. Run the Jupyter notebooks (in order)
```
notebooks/Data_Collection.ipynb
notebooks/Data_Cleaning.ipynb
```

### 5. Launch the Streamlit app
```bash
streamlit run app.py
```

---

## 📁 Project Structure

```
FYP_SENTIMENT_ANALYSIS/
├── Data/
│   ├── raw/          # Original CSV files from Kaggle + YouTube API
│   ├── cleaned/      # Cleaned per-platform CSVs
│   └── combined/     # combined_df.csv (1,500 rows, all platforms)
├── Notebooks/
│   ├── Data_Collection.ipynb
│   └── Data_Cleaning.ipynb
└── app.py            # Streamlit web application
```

---

## ⚠️ Limitations

- Sample size of 500 posts per platform limits statistical confidence at scale
- Kaggle datasets for Reddit and X may carry unknown sampling biases (YouTube used direct API)
- RoBERTa model was fine-tuned on Twitter data only, which may affect accuracy on Reddit and YouTube
- Data scope is limited to 2023; sentiment towards Generative AI has continued to evolve

---

## 🔮 Future Work

1. Replace Kaggle datasets with direct API collection across all platforms
2. Increase sample size to several thousand posts with stratified sampling
3. Use platform-specific fine-tuned models (e.g. a Reddit-trained or YouTube-trained transformer)
4. Extend the time period beyond 2023 to capture how sentiment has shifted with newer AI tools (GPT-4, Gemini, Claude, etc.)

---

## 👤 Author

**Mohamed Ahmed Nur** — BSc (Hons) Computer Science, University of Westminster (2026)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://linkedin.com/in/mofateh)
[![GitHub](https://img.shields.io/badge/GitHub-M--FATEH-black)](https://github.com/M-FATEH)
