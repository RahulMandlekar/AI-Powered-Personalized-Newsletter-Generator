# AI-Powered-Personalized-Newsletter-Generator
This project builds an intelligent, automated newsletter system that delivers personalized news articles to users based on their interests and behavior profiles. It utilizes semantic similarity via Sentence Transformers, abstractive summarization with Transformers, and offers in-depth evaluation with visual insights.
## Features

- RSS Feed Aggregation from multiple sources across Tech, Finance, Science, Sports, Entertainment, and News.
- Semantic Matching using SentenceTransformer (`all-mpnet-base-v2`) to match articles with user interests.
- Article Summarization using `facebook/bart-large-cnn` transformer model.
- Performance Evaluation of matching logic via multiple user-centric metrics.
- Markdown-based Newsletters automatically generated per user.
- Visual Analytics via matplotlib graphs for interpretability.

## Personas

Each user is represented by a profile with age, title, country, and detailed interest summary. Example personas include:

- Alex Parker – Tech Enthusiast
- Priya Sharma – Finance & Business Guru
- David Martinez – Science & Space Nerd
- Lisa Thompson – Entertainment Buff
- Marco Rossi – Sports Journalist

## Project Structure

```
📦 PersonalizedNewsletter/
├── all_fetched_articles.csv
├── model_evaluation_metrics.csv
├── newsletters/
├── PersonalisedNewsLetter.ipynb
├── articles_matched_per_user.png
├── similarity_std_dev_per_user.png
├── user_radar.png
└── README.md
```

## How It Works

### 1. Fetch & Clean Articles
- RSS feeds parsed via `feedparser`.
- Encoding fixed via `ftfy` and `html.unescape`.

### 2. Match Articles to Users
- Each user's interest is encoded using `SentenceTransformer`.
- Cosine similarity used to filter articles (threshold = 0.27).

### 3. Generate Summary
- Top matched articles are summarized with `facebook/bart-large-cnn`.

### 4. Markdown Newsletter
- Newsletters contain:
  - Summary Overview
  - Top Highlights
  - Full Articles (title, link, similarity, summary)

## Evaluation Metrics

| Metric                  | Description                                                  |
|-------------------------|--------------------------------------------------------------|
| Articles Matched        | Count of articles matched to the user                        |
| Avg. Similarity         | Mean similarity score of matched articles                    |
| Max Similarity          | Highest similarity score                                     |
| Std Dev of Similarity   | Spread of similarity scores                                  |
| Similarity Lift         | Max Sim / Avg Sim                                            |
| Diversity Score         | Uniqueness based on cosine distance                          |

Data available in `model_evaluation_metrics.csv`

## Visualizations

- Articles Matched Per User: `articles_matched_per_user.png`
- Similarity Spread: `similarity_std_dev_per_user.png`
- Radar Comparison Chart: `user_radar.png`

## Tech Stack

- Python 3.10
- sentence-transformers
- transformers
- feedparser, ftfy, pandas, matplotlib
- Hugging Face models: all-mpnet-base-v2, facebook/bart-large-cnn

## Output

All newsletters are saved in the `newsletters/` folder.

## License

This project is for educational and research purposes only.
