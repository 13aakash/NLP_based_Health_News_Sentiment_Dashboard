# 🏥 Health News Sentiment Analyzer

A pipeline that fetches real-time health news headlines, runs sentiment analysis using **RoBERTa**, extracts keywords with **spaCy**, and visualizes trends across health topics.

---

## 📌 Overview

This project tracks public sentiment in health-related news by:
- Fetching recent articles across 8 health topics via the **NewsAPI**
- Classifying each headline as **positive**, **neutral**, or **negative** using the `cardiffnlp/twitter-roberta-base-sentiment` model
- Extracting key medical/contextual terms using **spaCy NLP**
- Visualizing sentiment trends with **Plotly**

---

## 🧠 Models & Libraries

| Tool | Purpose |
|------|---------|
| `cardiffnlp/twitter-roberta-base-sentiment` | Sentiment classification (HuggingFace) |
| `spaCy (en_core_web_sm)` | Keyword extraction (nouns & proper nouns) |
| `NewsAPI` | Fetching health news headlines |
| `Plotly` | Interactive visualizations |
| `Pandas` | Data processing & aggregation |

---

## 📂 Project Structure

```
RoBERTa.ipynb               ← Main notebook (run end-to-end)
health_headlines.csv        ← All headlines with sentiment labels
daily_topic_sentiment.csv   ← Daily sentiment trend per topic
topic_summary.csv           ← Overall topic-level sentiment ranking
README.md
```

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
```

### 2. Install dependencies

```bash
pip install transformers torch newsapi-python pandas plotly spacy
python -m spacy download en_core_web_sm
```

### 3. Set up your NewsAPI key

Get a free API key at [newsapi.org](https://newsapi.org/).

**If running in Google Colab:** Add your key as a Colab Secret named `NEWS_API_KEY` (Secrets panel in the left sidebar).

**If running locally:** Replace the secret lookup in the notebook with:
```python
NEWS_API_KEY = "your_api_key_here"
```

### 4. Run the notebook

Open `RoBERTa.ipynb` and run all cells top to bottom.

---

## 📊 Health Topics Tracked

- Flu Symptoms
- Mental Health
- Anxiety
- Diabetes
- Heart Disease
- Fitness & Wellness
- Sleep Disorder
- Obesity

---

## 📈 Sample Output

The notebook produces an interactive bar chart showing average sentiment per topic, and exports three CSV files for further analysis.

**Example findings (last 7-day run):**
- `flu symptoms` and `obesity` had the most negative media coverage
- `fitness wellness` and `anxiety` skewed slightly positive
- `heart disease` had very few positive articles (0%)

---

## ⚙️ Configuration

You can tweak these variables at the top of the notebook:

| Variable | Default | Description |
|----------|---------|-------------|
| `HEALTH_TOPICS` | 8 topics | List of search queries for NewsAPI |
| `days_back` | `7` | How many days of news to fetch |
| `page_size` | `15` | Articles fetched per topic |

---

## 📝 Notes

- The RoBERTa model uses `LABEL_0` = negative, `LABEL_1` = neutral, `LABEL_2` = positive
- Sentiment scores are signed: negative labels get a negative score, positive labels a positive score, weighted by model confidence
- Headlines are deduplicated to avoid counting the same article twice
- Free NewsAPI keys are limited to ~100 requests/day and articles from the past 30 days

---

## 📄 License

MIT License. Feel free to fork and adapt.
