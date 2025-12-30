## Setup

1. Download the full CSV datasets from Kaggle:
   - Netflix (1 csv): https://www.kaggle.com/datasets/shivamb/netflix-shows
   - IMDb (2 csvs): https://www.kaggle.com/datasets/lakshmi25npathi/imdb-dataset-of-50k-movie-reviews
2. Extract the three CSVs, keeping the same name, and place the CSVs in the `data/` folder
3. Run the exploration.ipynb first and then ML.ipynb to first create a SQLite database

## Details

1. exploration.ipynb explores the IMDb and netflix datasets to see top directors, top actors, rating trends across time, past decades, etc.
2. ML.ipynb uses the some common dataset features and derived features (like top directors) to predict the IMDb rating. Multiple regression algorithms are compared: Linear, Ridge, Lasso, Random Forest, and Gradient Boosting.
