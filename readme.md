# Spotify Streams Prediction 🎵

A machine learning project to predict the number of streams for songs on Spotify using various audio features and metadata.

## 📋 Project Overview

This project analyzes popular Spotify songs and builds a predictive model to estimate the number of streams based on features such as:
- Audio characteristics (BPM, danceability, energy, valence, acousticness, etc.)
- Platform metrics (Spotify playlists, Apple playlists, Deezer playlists, Shazam charts)
- Release information (year, month, day)
- Artist information

## 🎯 Objective

The main goal is to predict the popularity of a song (measured by stream count) using machine learning algorithms, specifically Random Forest Regression with hyperparameter optimization using Optuna.

## 📊 Dataset

The dataset contains 953 songs with 24 features including:

### Key Features:
- **Track Information**: track name, artist(s) name, artist count
- **Release Data**: year, month, day
- **Streaming Metrics**: 
  - Spotify playlists and charts
  - Apple playlists and charts
  - Deezer playlists and charts
  - Shazam charts
- **Audio Features**:
  - BPM (tempo)
  - Key and Mode
  - Danceability %
  - Valence % (positivity)
  - Energy %
  - Acousticness %
  - Instrumentalness %
  - Liveness %
  - Speechiness %

### Target Variable:
- **streams**: Total number of streams on Spotify

## 🛠️ Technologies Used

- **Python 3.11**
- **Libraries**:
  - `pandas` - Data manipulation
  - `numpy` - Numerical computing
  - `matplotlib` - Data visualization
  - `seaborn` - Statistical visualizations
  - `scikit-learn` - Machine learning models
  - `optuna` - Hyperparameter optimization

## 🔍 Methodology

### 1. Data Preprocessing
- Handling missing values (imputation for `in_shazam_charts` and `key`)
- Label encoding for categorical variables (`mode`, `key`)
- Feature engineering:
  - Created `Spotify_Pop_charts` metric
  - Created `Spotify_Pop_Playlists` metric
- Data cleaning and type conversion

### 2. Exploratory Data Analysis
- Distribution analysis of streams and mode
- Feature correlation analysis
- Statistical summary of all features

### 3. Model Development
- **Models Evaluated**:
  - Linear Regression
  - Decision Tree Regressor
  - Random Forest Regressor ✅ (Best performer)
  - Gradient Boosting Regressor

### 4. Hyperparameter Optimization
- Used **Optuna** for automated hyperparameter tuning
- Optimized parameters:
  - `n_estimators`: Number of trees (50-300)
  - `max_depth`: Maximum tree depth (3-20)
  - `min_samples_split`: Minimum samples for splitting (2-10)

- Used **GridSearchCV** for final model refinement

## 📈 Results

### Model Performance:

| Model | RMSE | R² Score |
|-------|------|----------|
| Linear Regression | 7.01e+16 | 0.7135 |
| Decision Tree | 7.15e+16 | 0.7080 |
| **Random Forest** | **5.43e+16** | **0.7780** |
| Gradient Boosting | 5.81e+16 | 0.7628 |

### Best Model Configuration (GridSearchCV):
- **n_estimators**: 200
- **max_depth**: None
- **min_samples_split**: 2
- **Final RMSE**: 2.29e+08
- **Final R² Score**: 0.7862

## 📁 Project Structure

```
.
├── Number of stream on Spotify.ipynb   # Main notebook
├── README.md                           # This file
├── requirements.txt                    # Python dependencies
└── Popular_Spotify_Songs.csv          # Dataset (not included in repo)
```

## 🚀 Getting Started

### Prerequisites

Make sure you have Python 3.8+ installed on your system.

### Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/spotify-streams-prediction.git
cd spotify-streams-prediction
```

2. Create a virtual environment (recommended):
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# Mac/Linux
python3 -m venv venv
source venv/bin/activate
```

3. Install required packages:
```bash
pip install -r requirements.txt
```

### Running the Project

1. Ensure the dataset `Popular_Spotify_Songs.csv` is in the correct path (D:/Datasets/ML/ or update the path in the notebook)

### Running the Project

1. Clone this repository:
```bash
git clone https://github.com/yourusername/spotify-streams-prediction.git
cd spotify-streams-prediction
```

2. Ensure the dataset `Popular_Spotify_Songs.csv` is in the correct path

3. Open and run the Jupyter notebook:
```bash
jupyter notebook "Number of stream on Spotify.ipynb"
```

## 📊 Key Insights

- The Random Forest model performed best with an R² score of 0.7862
- Platform metrics (playlists and charts) are strong predictors of stream count
- Audio features like danceability, energy, and valence contribute to prediction accuracy
- Hyperparameter optimization significantly improved model performance

## 🔮 Future Improvements

- [ ] Feature importance analysis
- [ ] Deep learning models (Neural Networks)
- [ ] Time series analysis for trend prediction
- [ ] Additional feature engineering
- [ ] Cross-validation with more folds
- [ ] Ensemble methods combining multiple models

## 👨‍💻 Author

Created for analyzing and predicting Spotify music popularity trends.

## 📝 License

This project is for educational and research purposes.

## 🙏 Acknowledgments

- Dataset source: Spotify API data compilation
- Inspiration: Music streaming analytics and prediction

---

**Note**: Stream counts and predictions are based on historical data and may not reflect current streaming trends.
