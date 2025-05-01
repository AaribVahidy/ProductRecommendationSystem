# ProductRecommendationSystem
A hybrid recommendation system for Amazon products using content-based and collaborative filtering, evaluated with Precision@10, Recall@10, F1@10, Hit Rate@10, NDCG@10, and MAP@10.

A personalized **hybrid recommender system** for Amazon products, built using content-based filtering and collaborative filtering (item-based). This project intelligently combines product metadata with user interaction data to generate meaningful top-N recommendations.

---

## 📌 Features
- ✅ Product Level Analysis and Visualization
- ✅ Sentiment analysis using review content
- ✅ Feature Engineering
- ✅ Content Based Recommender System
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

### 3. Hybrid Strategy

- Combined both content-based and collaborative filtering scores using weighted addition:

  **Final Score = w_content × Content Score + w_collab × Collaborative Score**

- The weights `w_content` and `w_collab` were manually tuned to balance the contribution of each recommendation signal.

- This approach provided greater flexibility to emphasize one model over the other based on domain knowledge and validation performance.
