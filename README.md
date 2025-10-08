# 🛍️ Multi-Model Recommendation System for Amazon

## Project Overview

This project presents a comprehensive multi-model recommendation system designed for Amazon products. The system integrates four complementary recommendation approaches—popularity-based, content-based, collaborative (SVD), and hybrid filtering—combined with sentiment analysis using NLP.
The goal is to enhance product discovery, personalization, and user engagement in large-scale e-commerce environments while addressing challenges such as cold-start problems, data sparsity, and scalability.

The solution includes:
* Data extraction and preprocessing using PySpark and MongoDB
* Text-based analysis and sentiment classification using NLP models
* Implementation and comparison of multiple recommendation algorithms
* A Streamlit web application for interactive exploration and product recommendation

## Objectives
* Develop a multi-model recommendation system capable of adapting to various user scenarios.
* Compare the performance of distinct recommendation techniques.
* Incorporate sentiment analysis to refine recommendations based on user opinions.
* Build a scalable architecture deployable for real-world e-commerce applications.

## System Architecture
The architecture consists of the following main components:
1. **Data Layer**
  * Data sourced from the Amazon Reviews 2023 dataset (McAuley Lab).
  * Processing and storage using PySpark (for distributed computation) and MongoDB (for persistence).

2. **Processing Layer**

  * **Data Cleaning:** Removal of duplicates, missing values, and noise.
  * **Feature Engineering:** TF-IDF vectorization, review counting, sentiment scoring
  * **Text Preprocessing:** HTML cleaning, stopword removal, stemming with PorterStemmer

3. **Modeling Layer**

  * **Popularity-Based Filtering:** Recommends globally popular products.
  * **Content-Based Filtering:** Uses TF-IDF and cosine similarity to recommend products with similar descriptions.
  * **Collaborative Filtering (SVD):** Learns latent user-product relations via SVD matrix factorization.
  * **Hybrid Model:** Combines all previous methods to improve coverage and personalization.

4. **Sentiment Analysis Module**

  * Sentiment classification using **Bernoulli Naïve Bayes** (70.43% accuracy).
  * Polarity detection of reviews (positive, neutral, negative).

5. **Visualization & Application Layer**

  * **Power BI Dashboard:** Displays data insights, rating distributions, and sentiment analysis.
  * **Streamlit Application:** Allows users to interactively explore products and generate recommendations.


## Model Performance

### Evaluation Metrics:

The models were evaluated using three main metrics:
- **Precision@K** – Relevance of top-K recommendations.
- **Recall@K** – Measures the proportion of relevant items successfully retrieved.
- **Diversity** – Variety in recommendations (1 - average similarity).

### Recommendation Models Evaluation (on 1,000 products sample):

| Method | Precision | Recall | Diversity |
|--------|-----------|--------|-----------|
| Content-Based | 47.4% | 47.4% | 0.986 |
| Collaborative | 0.4% | 0.4% | 0.991 |
| Popularity | 0.04% | 0.04% | 0.984 |


### Sentiment Analysis Models:

| Model | Accuracy | Status |
|-------|----------|--------|
| SVC (C=0.01) | 66.08% | - |
| Multinomial Naïve Bayes | 70.09% | - |
| **Bernoulli Naïve Bayes** | **70.43%** | **Selected** |

> **Note:** Collaborative and popularity-based models show better performance on full dataset (>30% precision) despite low scores on the 1,000-product sample due to data sparsity.

## Key Results

- **Content-based filtering** performs best on small datasets with rich product descriptions
- **Collaborative filtering** requires substantial user interaction data to be effective
- **Sentiment analysis** adds valuable contextual understanding beyond star ratings
- **Hybrid approach** provides the most robust coverage across different scenarios
- **Bernoulli Naïve Bayes** achieved 70.43% accuracy in sentiment prediction.

## Streamlit Application

**Main Features:**

  * Product selection and search functionality
  * Choice between four recommendation models
  * Display of product details: title, image, price, rating
  * Downloadable recommendation results (CSV)
  * Interactive visual components and progress indicators

**UI Highlights:**

  * Responsive design with CSS customization
  * Color-coded cards and animated buttons
  * Sidebar with statistics and model descriptions


## 🚀 Future Improvements

1. **Sentiment Analysis:** Integrate transformer-based models (BERT, RoBERTa) for higher accuracy.
2. **User Profiling:** Incorporate behavioral data such as browsing time and cart activity.
3. **Scalability:** Deploy on cloud with REST API endpoints.
4. **Advanced Modeling:** Explore deep learning and graph-based recommenders (e.g., GNNs).
5. **User Feedback Loop:** Implement A/B testing and real-time feedback integration.

## Installation & Usage

### Prerequisites
- Python 3.8+
- MongoDB
- Java (for PySpark)

### Installation Steps

1. **Clone the repository:**
2. **Set up MongoDB:**

Install and start MongoDB service
Update connection URI in configuration files

3. **Download dataset**:

Obtain Amazon Reviews 2023 dataset from McAuley Lab
McAuley Lab Datasets: https://cseweb.ucsd.edu/~jmcauley/datasets.html

Place in data/raw/ directory

3. **Run data processing pipeline:**

```bash
python data_processing/data_cleaning.py
python data_processing/feature_generation.py
python data_processing/data_merge.py
```
Train models:

```bash
python models/sentiment_analysis.py
python models/collaborative_model_based.py
```
Launch web application:
```bash
streamlit run appstreamlit.py
```

## Interface Demonstration video
[![System Demo](https://img.shields.io/badge/Watch_Demo-FF6B6B?style=for-the-badge&logo=video&logoColor=white)](demo.mp4)

## ✨ Happy Learning &  Shopping ! 🛍️

