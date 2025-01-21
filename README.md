# Movie Recommendation System

## Overview
This project involves building a content-based movie recommendation system using Python and machine learning techniques. The system recommends similar movies based on input titles by analyzing their metadata such as genres, keywords, cast, and crew.

---

## Problem Statement
Finding relevant movies to watch can be challenging with the vast amount of available content. This project aims to simplify the process by recommending movies that are similar to a user’s favorite title.

---

## Dataset
The project uses the **TMDB 5000 Movies** and **TMDB 5000 Credits** datasets.

### Key Features:
1. **Movies Data:**
   - `title`: Title of the movie.
   - `overview`: Brief summary of the movie.
   - `genres`: List of genres associated with the movie.
   - `keywords`: Keywords describing the movie’s themes.

2. **Credits Data:**
   - `cast`: Leading actors in the movie.
   - `crew`: Directors of the movie.

---

## Approach

### 1. **Data Preprocessing:**
- Merged the movies and credits datasets on the `title` column.
- Selected relevant columns: `movie_id`, `title`, `overview`, `genres`, `keywords`, `cast`, and `crew`.
- Handled missing values by dropping rows with null entries.
- Transformed `genres`, `keywords`, `cast`, and `crew` from JSON-like structures into lists of names.
- Created a new column `tags` by combining `overview`, `genres`, `keywords`, `cast`, and `crew`.

### 2. **Text Representation:**
- Applied the **Bag-of-Words (BoW)** model using `CountVectorizer` from scikit-learn to convert the `tags` column into a numerical vector.
- Limited the vocabulary to the top 5000 most frequent words and removed English stop words.

### 3. **Similarity Measurement:**
- Calculated the pairwise **cosine similarity** between movies based on the BoW vectors.
- Used the similarity matrix to identify and recommend movies similar to a given input title.

### 4. **Recommendation Function:**
- Created a function `recommend(movie)` to:
  - Fetch the index of the input movie.
  - Retrieve the top 5 most similar movies based on cosine similarity scores.

---

## Example Usage
```python
recommend('Gandhi')
```
**Recommendations:**
- Gandhi, My Father
- The Wind That Shakes the Barley
- A Passage to India
- Guiana 1838
- Ramanujan

---

## Tools & Libraries
- **Languages:** Python
- **Libraries:**
  - Data Processing: `pandas`, `numpy`
  - Text Processing: `scikit-learn`
  - Visualization: `matplotlib`, `seaborn`

---

## How to Run
1. Clone the repository:
   ```bash
   git clone <repository_url>
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the Python script:
   ```bash
   python movie_recommendation.py
   ```

---

## Results
The recommendation system provides accurate and meaningful movie suggestions based on the content of the input title. 

---

## Future Scope
- Enhance the system with collaborative filtering for better recommendations.
- Integrate the model into a web application using Flask or Streamlit for user-friendly interaction.
- Incorporate user reviews and ratings for more personalized recommendations.

---

