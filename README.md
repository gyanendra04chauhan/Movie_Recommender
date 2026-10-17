# 🎬 MovieRec: AI Movie Recommendation System

A movie recommender built with **item-based collaborative filtering** on the MovieLens 100K dataset. Pick a movie you like and get similar titles, or enter a user ID and get a personalised watchlist. The interface is a dark, cinema-style Streamlit app with posters fetched from TMDB.

## 🚀 Live Demo

> **Paste your deployed app link below** (replace `YOUR_LIVE_DEMO_LINK`).

👉 **[Open the live app](https://movierecommender-26vynqh7jnaysdj8j7qycw.streamlit.app/)**

[![Live Demo](https://img.shields.io/badge/Live%20Demo-Open%20App-e52d53?style=for-the-badge&logo=streamlit&logoColor=white)](YOUR_LIVE_DEMO_LINK)

## 📸 Screenshots

Add your screenshots to an `assets/screenshots/` folder and update the paths below.

| Home | Recommendations |
|------|-----------------|
| ![Home](assets/screenshots/home.png) | ![Recommendations](assets/screenshots/recommendations.png) |

## ✨ Features

- **Home:** hero banner with trending and recommended movie rows, plus sidebar filters.
- **Get Recommendations:** two modes:
  - *Item-based:* choose a movie you enjoyed and see the most similar films.
  - *User-based:* enter a MovieLens user ID (1 to 943) and get predicted top picks.
- **Search Movies:** search the whole library by title, with posters and ratings.
- **Similar Movies:** explore similarity scores for the 100 most-rated movies.
- **Movie Insights:** dataset statistics, most reviewed movies, and highest rated classics.
- **Live posters:** posters and ratings from the TMDB API, with a placeholder if the key is missing.

## 🧠 How It Works

1. **Data:** MovieLens 100K (100,000 ratings from 943 users on 1,682 movies).
2. **Item-item similarity:** cosine similarity between movies, computed from the user-rating matrix and saved as `item_similarity.pkl`.
3. **Similar movies:** look up the chosen movie's row in the similarity matrix and return the top-N most similar titles.
4. **Personalised picks:** for every movie a user has not rated, the predicted rating is a similarity-weighted average of the ratings that user has already given. The highest predictions are shown.
5. **Fallback:** the global mean rating (`global_mean.pkl`) is used when there is not enough information.

## 🛠️ Tech Stack

| Area | Tools |
|------|-------|
| Language | Python |
| App framework | Streamlit |
| Data and ML | Pandas, NumPy, Scikit-learn, Joblib |
| Posters and metadata | TMDB API |
| Styling | Custom HTML and CSS inside Streamlit |

## 📁 Project Structure

```
movie_recommender/
├── app.py                  # Streamlit app
├── item_similarity.pkl     # Item-item cosine similarity matrix
├── train_matrix.pkl        # User-movie rating matrix
├── global_mean.pkl         # Global mean rating
├── movie_info.csv          # Movie IDs and titles
├── requirements.txt
├── README.md
├── .gitignore
├── .streamlit/
│   └── secrets.toml        # TMDB key (NOT committed)
└── assets/                 # Optional
    ├── hero_cinema_opt.jpg
    └── posters/            # Local poster images for the Home page
```

## ⚙️ Run Locally

**1. Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO.git
cd YOUR_REPO
```

**2. Create a virtual environment (recommended)**
```bash
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # macOS / Linux
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Add your TMDB API key** (free key from [themoviedb.org](https://www.themoviedb.org/settings/api))

Create `.streamlit/secrets.toml`:
```toml
TMDB_API_KEY = "your_tmdb_api_key"
```
Or set an environment variable instead:
```bash
set TMDB_API_KEY=your_tmdb_api_key        # Windows
# export TMDB_API_KEY=your_tmdb_api_key   # macOS / Linux
```
The app still runs without a key, but movie posters are replaced by placeholders.

**5. Start the app**
```bash
streamlit run app.py
```

## ☁️ Deploy on Streamlit Community Cloud

1. Push the project to a public GitHub repository (include the `.pkl` files and `movie_info.csv`).
2. Go to [share.streamlit.io](https://share.streamlit.io) and click **New app**.
3. Select your repository, branch, and set the main file to `app.py`.
4. Open **Advanced settings → Secrets** and add:
   ```toml
   TMDB_API_KEY = "your_tmdb_api_key"
   ```
5. Click **Deploy**, then paste the generated link into the **Live Demo** section at the top of this README.

## 📦 requirements.txt

```
streamlit
pandas
numpy
scikit-learn
joblib
```

## 🔒 Security Note

Never commit your API key. Add this to `.gitignore`:

```
.streamlit/secrets.toml
venv/
__pycache__/
```

## 🔮 Future Improvements

- Genre-based filtering across all pages using MovieLens genre data
- Hybrid model combining collaborative filtering with content features
- Evaluation metrics (RMSE, precision@k) shown in the Insights page
- Rating input so new users can get recommendations without an existing ID

## 🙏 Acknowledgements

- [MovieLens 100K dataset](https://grouplens.org/datasets/movielens/100k/) by GroupLens Research
- Posters and metadata from [TMDB](https://www.themoviedb.org). *This product uses the TMDB API but is not endorsed or certified by TMDB.*

## 👤 Author

**Gyanendra Chauhan**
B.Tech CSE (AI & ML), Axis Institute of Technology and Management, Kanpur


