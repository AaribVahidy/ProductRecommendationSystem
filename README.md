# ProductRecommendationSystem

A hybrid recommendation system for Amazon products using content-based and collaborative filtering, evaluated with Precision@10, Recall@10, F1@10, Hit Rate@10, NDCG@10, and MAP@10.

A personalized **hybrid recommender system** for Amazon products, built using content-based filtering and item-based collaborative filtering. This project intelligently combines product metadata with user interaction data to generate meaningful top-N recommendations.

---

## 📦 Dataset Description

This dataset is a curated collection of Amazon product listings and customer reviews, specifically focused on products under the **Electronics** category — ranging from charging cables and mobile phones to kettles.

Each row represents detailed information about a specific product and its corresponding user reviews.

**Key Features:**

- **Product Details**:  
  Includes `product_id`, `product_name`, `category`, `discounted_price`, `actual_price`, `discount_percentage`, and `product_link`, offering insights into the product's metadata and pricing strategy.

- **Ratings and Reviews**:  
  Contains the numerical `rating` and total number of ratings (`rating_count`).

- **User Reviews**:  
  Associated `user_id`, `user_name`, `review_id`, `review_title`, and `review_content` provide multi-perspective views on consumer satisfaction.

- **Product Description**:  
  The `about_product` column captures a rich textual summary of features, warranty details, compatibility, and performance claims.

- **Multimedia Links**:  
  Columns like `img_link` and `product_link` offer visual and direct references to the product on Amazon.

---

## 📌 Features

- ✅ Product Level Analysis and Visualization  
- ✅ Sentiment Analysis using review content  
- ✅ Feature Engineering  
- ✅ Content-Based Recommender System  
- ✅ **Hybrid Recommendation System** (Content + Collaborative)  
- ✅ Personalized top-10 product recommendations  
- ✅ TF-IDF based product similarity  
- ✅ Item-based collaborative filtering with cosine similarity  
- ✅ Support for sparse rating matrices  
- ✅ Evaluated using multiple metrics: Precision@10, Recall@10, F1@10, Hit Rate@10, NDCG@10, MAP@10  
- ✅ Modular design for easy extensibility  

---

## 📊 Final Evaluation Results (@10)

Tested on **1301 products**:

| Metric         | Score   |
|----------------|---------|
| Precision@10   | 0.4251  |
| Recall@10      | 0.7986  |
| F1@10          | 0.5113  |
| Hit Rate@10    | 0.9523  |
| NDCG@10        | 0.7692  |
| **MAP@10**     | **0.7068** |

---

## 🧠 Recommendation Approach

### 1. **Content-Based Filtering**

- Vectorized product metadata using `TF-IDF` (product title, description, category, etc.)
- Computed pairwise cosine similarity to find similar items.

### 2. **Collaborative Filtering**

- Constructed a sparse user-product rating matrix.
- Used cosine similarity between item vectors (item-based filtering).
- Handled cold-start issues by backing off to content-based recommendations.

### 3. **Hybrid Strategy**

- Combined both content-based and collaborative filtering scores using weighted addition:  
  `Final Score = w_content × Content Score + w_collab × Collaborative Score`

- The weights `w_content` and `w_collab` were manually tuned to balance the contribution of each recommendation signal.

- This approach provided greater flexibility to emphasize one model over the other based on domain knowledge and validation performance.



## Running the Frontend Web Application

The frontend is a Flask-based web application located in the `frontend/` folder of this repository. The main app file is `app.py`.

### Features
- Product browsing with dynamic recommendations  
- Product detail pages with customer reviews  
- Review pages showing all reviews for a product  
- Advanced content-based recommendation system with MAP metrics  
- Dynamic extraction of reviews from comma-separated data  

### Setup Instructions

- **Navigate to the frontend folder:**  

  ```bash
  cd frontend

- **Install Dependencies:**

  ```bash
  pip install flask pandas numpy nltk scikit-learn wordninja textblob

Download NLTK Components (run in Python shell or script):

import nltk

nltk.download('stopwords')

nltk.download('wordnet')

-**Data Preparation:**

Place amazon.csv dataset file inside the frontend/ folder.

- Generate the similarity matrix and ground truth by running:
  ```bash
  python export_similarity_matrix.py

This creates:

cosine_similarity_matrix.pkl (precomputed similarity matrix)

ground_truth.pkl (precomputed recommendation ground truth)

- **Run the Flask Application:**
  ```bash
  python app.py

**Access the Application:**

Open http://127.0.0.1:5000/ in your web browser.

**Fronend File Structure:**

app.py — Main Flask application

export_similarity_matrix.py — Script to generate cosine similarity matrix and ground truth

cosine_similarity_matrix.pkl — Precomputed similarity matrix (generated)

ground_truth.pkl — Precomputed recommendation ground truth (generated)

templates/ — HTML templates for the web interface

index.html — Home page

product.html — Product detail page with recommendations and MAP metrics

reviews.html — Page showing all reviews for a product

amazon.csv — Dataset file with product info and reviews
