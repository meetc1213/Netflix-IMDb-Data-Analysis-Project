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

## Technologies

- Machine Learning: Python, Scikit-learn
- Data Handling: SQL, Pandas
- Visualization: Matplotlib, Seaborn, Power BI

## Setup

1. Download the full CSV datasets from Kaggle:
   - Netflix (1 csv): https://www.kaggle.com/datasets/shivamb/netflix-shows
   - IMDb (2 csvs): https://www.kaggle.com/datasets/stefanoleone992/imdb-extensive-dataset
2. Extract the three CSVs, keeping the same names, and place them in the `data/` folder
3. Install dependencies with `pip install -r requirements.txt`
4. Run `exploration.ipynb` first, then `ML.ipynb` — the exploration notebook creates the SQLite database that ML.ipynb depends on
