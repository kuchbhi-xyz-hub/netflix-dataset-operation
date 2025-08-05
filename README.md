# Netflix Data Engineering Pipeline

This project implements a mini data engineering pipeline using Netflix's public catalog dataset from Kaggle. It includes steps for extraction, transformation, normalization of genres, and visualization of key insights using Matplotlib and Seaborn.

## Dataset

- **Source**: [Netflix Movies and TV Shows on Kaggle](https://www.kaggle.com/datasets/shivamb/netflix-shows)
- **File used**: `netflix_titles.csv`

The dataset contains metadata about 6,000+ movies and TV shows available on Netflix, including attributes like title, type, release year, cast, country, duration, and genres.

---

## Features

### 1. ETL Pipeline

- **Extract**: Reads CSV data using Pandas
- **Transform**:
  - Cleans null values and formats `date_added` column
  - Extracts `added_year` and `added_month` from `date_added`
  - Assigns unique `title_id` to each record
- **Load**: Stores transformed data into a local SQLite database (`netflix_genre_pipeline.db`)

### 2. Genre Normalization (Many-to-Many Schema)

- Explodes the `listed_in` genre field to support multiple genres per title
- Creates two normalized tables:
  - `genres`: Unique list of genres with `genre_id`
  - `title_genre`: Mapping table linking each `title_id` to one or more `genre_id`s
- Enables relational querying and genre-level analytics

### 3. Data Visualization

Visualizations created using Seaborn and Matplotlib:

- Top 10 most common Netflix genres
- Netflix content trend over time (Movies vs TV Shows)
- Top 10 countries producing Netflix titles

---

## Database Schema

- **netflix_titles**: Main table with cleaned Netflix metadata
- **genres**: List of unique genres with `genre_id`
- **title_genre**: Mapping of titles to genres (many-to-many relationship)

---

## Requirements

- Python 3.x
- Pandas
- Seaborn
- Matplotlib
- SQLAlchemy

Install requirements (if running locally):

```bash
pip install pandas matplotlib seaborn sqlalchemy
