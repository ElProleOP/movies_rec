
# Movie Recommendation System

This project aims to develop a movie recommendation system by collecting, cleaning, and storing movie-related data for further analysis and processing.

## Completed Steps

### 1. Data Collection
- A dataset containing movie information was sourced from Kaggle, specifically a comprehensive dataset of TMDb movies in CSV format.

### 2. Data Cleaning
The dataset was cleaned to ensure data consistency and quality:
- **Dropped Null Values:** Rows with null `release_date` were removed, as this field is critical for analysis.
- **Filled Missing Values:**
  - `genres`: Replaced missing values with `"No genre"`.
  - `overview`: Replaced missing values with `"No overview"`.
- **Filtered Values:**
  - Removed movies with `vote_average` or `vote_count` equal to zero.
  - Removed entries with `runtime` equal to zero.
- **Standardized Columns:**
  - Extracted the year from `release_date` and stored it in a new `release_year` column.
  - Reformatted the `genres` column into a consistent format and created a mapping of genres to unique IDs.

### 3. Data Storage
The cleaned data was organized into a relational database schema using PostgreSQL. Key tables include:
- **movies:** Contains details about each movie.
- **genres:** Stores unique genre information.
- **movie_genres:** A join table connecting movies with their associated genres.

#### Database Schema
The following schema was implemented:

```sql
table movies {
	movie_id INT 
	title VARCHAR(255) 
	release_year DATE 
	vote_average FLOAT 
	vote_count INT 
	runtime INT 
	popularity FLOAT 
	original_language VARCHAR(10) 
	overview TEXT
}
table genres {
  id SERIAL PRIMARY KEY
  genre VARCHAR NOT NULL
}

table movie_genres {
  movie_id INT REFERENCES movies(id)
  genre_id INT REFERENCES genres(id)
}
```

### 4. Data Loading
- Used SQLAlchemy to load the cleaned data into the PostgreSQL database.
- Verified that all tables were populated correctly.

## Next Steps
- **Data Processing:** Design and implement ETL pipelines to process the data for analysis and model training.
- **Data Analysis:** Perform exploratory data analysis (EDA) to uncover insights.
- **Modeling:** Develop and train recommendation models.
- **Deployment:** Build a REST API to provide recommendations based on user preferences.

## Tools and Technologies
- **Python**: Data manipulation and database interaction.
- **PostgreSQL**: Relational database management.
- **SQLAlchemy**: Database ORM for data loading.
- **Pandas**: Data cleaning and transformation.

---

Feel free to contribute or suggest improvements to the current progress!


