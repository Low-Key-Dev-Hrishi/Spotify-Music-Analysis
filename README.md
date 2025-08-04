An Analysis of Popular Music Trends on Spotify (1922-2021)
1. Project Objective
This project performs an end-to-end analysis of a comprehensive Spotify dataset containing over 600,000 tracks. The objective is to uncover long-term trends in music characteristics, identify the most prolific artists in the catalog, and pinpoint the highest-energy songs of each decade. The analysis demonstrates skills in data cleaning, database management, advanced SQL querying, and data visualization.

Tools Used: PostgreSQL, Python, Pandas, Matplotlib, Seaborn, Jupyter Notebook

2. Data Cleaning and Preparation
The initial dataset was loaded into a Pandas DataFrame for cleaning and preparation before being loaded into a PostgreSQL database for analysis. Key cleaning steps included:

Handling Missing Values: Dropped rows with missing song names (name column).

Correcting Data Types: The release_date column, initially an object, was inconsistent (containing both full dates and just years). A release_year column was engineered by extracting the first four characters of the string to create a clean, consistent numeric feature.

Feature Engineering: The artists column, which contained a string representation of a list, was parsed to create a primary_artist column containing only the first artist's name.

Duplicate Removal: Removed duplicate rows to ensure data integrity.

The cleaned data was then loaded into a PostgreSQL table named spotify_tracks_clean for analysis.

3. Analysis & Findings
Question 1: How have the characteristics of music evolved over the decades?
To analyze the evolution of music, the average danceability and energy were calculated for each decade since 1950.

SQL Query:
SELECT
  FLOOR(release_year / 10) * 10 AS decade,
  AVG(danceability) AS avg_danceability,
  AVG(energy) AS avg_energy
FROM
  spotify_tracks_clean
WHERE
  release_year >= 1950
GROUP BY
  decade
ORDER BY
  decade;

Visualization & Insight:

The analysis reveals a clear, decades-long increase in both the energy and danceability of popular music, peaking in the 2000s. The 2020s show the first slight decline in average energy, suggesting a potential shift in musical trends, possibly influenced by the rise of lower-energy, mood-based genres on streaming platforms.

Question 2: Who are the most prolific artists?
To identify the artists with the largest number of tracks in the catalog, a query was run to count the tracks for each artist.

SQL Query:


  
