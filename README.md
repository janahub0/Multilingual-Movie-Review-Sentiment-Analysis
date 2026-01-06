# Multilingual Movie Review Sentiment Analysis

## 📌 Project Overview

This project analyzes the sentiment of movie reviews written in **three different languages**:  
**English, French, and Spanish**.

The dataset consists of **30 movies** (10 per language), each containing:
- Title
- Year of release
- Synopsis
- Review text

To enable consistent sentiment analysis, all non-English reviews and synopses are first translated into English using **pretrained HuggingFace transformer models**.  
After translation, sentiment analysis is performed on all reviews and classified as **Positive** or **Negative**.

---

## 🛠️ Tools & Technologies

- **Python**
- **Pandas** – data loading and preprocessing
- **HuggingFace Transformers**
  - MarianMT (French → English, Spanish → English)
  - DistilBERT (Sentiment Analysis)
- **PyTorch**
- **tqdm** – progress bars

---

## 📂 Dataset

Input files:
- `movie_reviews_eng.csv`
- `movie_reviews_fr.csv`
- `movie_reviews_sp.csv`

Each file contains movie metadata, a synopsis, and a review written in its original language.


## 🔄 Project Pipeline

### 1️⃣ Data Preprocessing
- Loaded all three CSV files into Pandas dataframes.
- Standardized column names across datasets.
- Added an `Original Language` column (`en`, `fr`, `sp`).
- Combined all data into a single dataframe.

### 2️⃣ Text Translation
- Used HuggingFace MarianMT models to translate:
  - French → English
  - Spanish → English
- Translated both **Review** and **Synopsis** fields.
- Updated the dataframe with translated English text.

### 3️⃣ Sentiment Analysis
- Used a pretrained **DistilBERT SST-2** sentiment model.
- Classified each review as **Positive** or **Negative**.
- Stored results in a new column called `Sentiment`.
