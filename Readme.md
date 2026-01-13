# Netflix Big Data Analysis (MongoDB & Python)

## Project Overview
This project analyzes Netflix catalog metadata (movies and TV shows) using an end-to-end Big Data pipeline. The goal is to demonstrate how **Big Data concepts**, especially **Variety**, **Veracity**, and **Velocity** appear in a real-world dataset and how tools like **Python** and **MongoDB** can be used to manage, analyze, and visualize this data.

The project includes:
- Data cleaning and transformation with Python (Pandas)
- Flexible NoSQL storage using MongoDB
- Batch analytics with MongoDB aggregation pipelines
- Visualizations to extract insights from the data

---

## Dataset
- **Source**: Kaggle – *Netflix Movies & TV Shows*
- **Dataset**: Netflix Movies and TV Shows (Kaggle)
https://www.kaggle.com/datasets/shivamb/netflix-shows
- **File**: `netflix_titles.csv`
- **Size**: 8,800+ titles
- **Time range**: 1925–2021

### Key Fields Used
- `show_id`
- `type` (Movie or TV Show)
- `title`
- `release_year`
- `date_added` → `year_added`
- `country`
- `listed_in` (genres)
- `rating`
- `duration`

---

## Big Data Dimensions

### Variety
- Multiple genres and multiple countries per title
- Mixed formats (movies in minutes, TV shows in seasons)
- Combination of text, numeric, and date fields

### Veracity
- Missing values in country, rating, and date fields
- Inconsistent formatting (e.g., duration strings)
- Required cleaning and standardization before analysis

### Velocity
- Dataset captures how Netflix’s catalog evolves over time
- By analyzing when titles were added, the project measures how quickly Netflix expanded its catalog—especially after 2017

---

## Project Pipeline

1. **Load Data**
   - Read CSV file using Pandas

2. **Clean & Transform**
   - Remove duplicate records
   - Fill missing values
   - Extract `year_added` from `date_added`
   - Split `country` and `listed_in` into arrays
   - Parse `duration` into `duration_value` and `duration_unit`

3. **NoSQL Modeling (MongoDB)**
   - Store each title as a document
   - Use arrays for genres and countries
   - Schema optimized for flexible metadata

4. **Indexes**
   - `release_year`, `year_added`
   - `country`, `listed_in`
   - Compound index: `(type, release_year)`
   - Text index on `title`

5. **Batch Analytics (MongoDB Aggregation Pipelines)**
   - Catalog growth over time (Velocity)
   - Top genres (Variety)
   - Top producing countries
   - Longest movies and longest-running TV shows

6. **Visualization & Insights**
   - Movies vs TV shows
   - Catalog growth after 2017
   - Top countries by content
   - Top genres
   - Runtime and season rankings

---

## Technologies Used
- **Python**: pandas, numpy, matplotlib
- **Database**: MongoDB
- **Driver**: pymongo

---

## How to Run

1. Ensure MongoDB is running locally:
   ```bash
   mongodb://localhost:27017
   ```

2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib pymongo
   ```

3. Place `netflix_titles.csv` in the project directory

4. Run the notebook or Python script from top to bottom

---

## Output
The project generates visualizations such as:
- Movies vs TV Shows distribution
- Titles added per year
- Top genres and countries
- Longest movies and TV shows

---

## Conclusion
This project demonstrates how Big Data concepts apply to Netflix’s catalog data and shows why MongoDB is well-suited for handling flexible, evolving datasets. By combining Python and MongoDB, the pipeline efficiently cleans, stores, analyzes, and visualizes complex metadata.

---



