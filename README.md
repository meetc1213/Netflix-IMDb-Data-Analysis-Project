# Netflix & IMDb Analysis

*What makes a movie highly rated? How has cinema evolved over decades? This project analyses IMDb titles and Netflix's full catalogue to answer these questions through exploration, machine learning, and an interactive dashboard.*

## What This Project Analyses

1. **exploration.ipynb** — Identifies which countries, directors, and genres dominate Netflix and IMDb; tracks how genre popularity and audience ratings have shifted decade-by-decade from the 1950s to 2020
2. **ML.ipynb** — Builds a model to predict a movie's IMDb rating using features like genre, director track record, and language. Five regression algorithms are compared (Linear, Ridge, Lasso, Random Forest, Gradient Boosting) — Gradient Boosting achieves the best result with an R² of 0.52 and RMSE of 0.88
3. **Power BI Dashboard** — Interactive dashboard for drilling into model predictions vs actuals, genre breakdowns, and director performance. Can be opened by downloading `powerbi_report.pbix`

## Key Findings

- Drama is the most produced genre every decade since the 1950s, but its average rating has declined as volume grew
- `total_votes` is the strongest predictor of IMDb rating (20.9% feature importance) — more popular films tend to rate higher
- 50.5% of rating predictions land within ±0.5 of the actual score; only 3.6% of predictions are off by more than 2 points
- The USA dominates Netflix content (4,000+ titles), followed by India and the UK
- Tree-based models significantly outperform linear models, suggesting non-linear relationships between a film's features and its rating

## Architecture

```
Kaggle CSVs
    │
    ▼
Azure Blob Storage (raw-data/)       ← raw source files
    │
    │  Azure Data Factory pipeline
    │  "IngestRawToProcessed"
    │  3 sequential Copy activities
    ▼
Azure Blob Storage (processed/)      ← cleaned, pipeline-verified data
    │
    ▼
Python Notebooks                     ← read via azure-storage-blob SDK
    │
    ├── exploration.ipynb → SQLite (local, for SQL queries)
    └── ML.ipynb          → Scikit-learn → Power BI exports
```

## Technologies

- Cloud: Azure Blob Storage, Azure Data Factory
- Machine Learning: Python, Scikit-learn
- Data Handling: SQL (SQLite), Pandas
- Visualization: Matplotlib, Seaborn, Power BI

## Setup

1. Download the full CSV datasets from Kaggle:
   - Netflix (1 csv): https://www.kaggle.com/datasets/shivamb/netflix-shows
   - IMDb (2 csvs): https://www.kaggle.com/datasets/stefanoleone992/imdb-extensive-dataset
2. Upload the three CSVs to the `raw-data/` container in Azure Blob Storage, then run the `IngestRawToProcessed` ADF pipeline to populate the `processed/` container
3. Create a `.env` file in the project root with your Azure connection string:
   ```
   AZURE_STORAGE_CONNECTION_STRING=your_connection_string_here
   ```
4. Install dependencies with `pip install -r requirements.txt`
5. Run `exploration.ipynb` first, then `ML.ipynb` — the exploration notebook creates the SQLite database that ML.ipynb depends on
