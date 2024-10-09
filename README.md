# Exploratory Data Analysis on Film Data Using PostgreSQL

## Project Overview

This project applies SQL skills to perform exploratory data analysis (EDA) on a film database containing information about films, people, reviews, and roles. The objective is to extract insights related to film performance, distribution, audience engagement, and more, answering key business questions in the film industry.

### Key Objectives:
- Use SQL queries to retrieve and analyze data from the "film" database.
- Answer real-life business questions related to the film industry.
- Present findings using clear and concise visualizations.


## Key Questions Answered

### 1. What are the top 10 highest-grossing films in the database, and when were they released?

```sql
SELECT title, release_year, gross
FROM film
ORDER BY gross DESC
LIMIT 10;

Results:
The top five countries with the most film releases are shown, highlighting where the most movies are produced.


2. How many films were released in each country, and what are the top five countries?

SELECT country, COUNT(film_id) AS num_films
FROM film
GROUP BY country
ORDER BY num_films DESC
LIMIT 5;

Results:
The top five countries with the most film releases are shown, highlighting where the most movies are produced.


3. How many films are available in each language, and what are the top three languages represented?

SELECT language, COUNT(film_id) AS num_films
FROM film
GROUP BY language
ORDER BY num_films DESC
LIMIT 3;

Results:
The query provides the count of films available in each language and displays the top three languages represented.


4. What is the average IMDb score for films in the database?

SELECT AVG(imdb_score) AS avg_imdb_score
FROM film;

Results:
The average IMDb score for all the films in the database is calculated.

5. Which country has made the highest profit from movies?

SELECT country, AVG(gross - budget) AS avg_profit
FROM film
WHERE gross IS NOT NULL AND budget IS NOT NULL
GROUP BY country
ORDER BY avg_profit DESC
LIMIT 1;

Results:
This query finds the country that made the highest average profit from movies, filtering out films with null budget or gross values.

6. Which movie made the highest profit in the 21st century?

SELECT title, (gross - budget) AS profit
FROM film
WHERE release_year >= 2000 AND gross IS NOT NULL AND budget IS NOT NULL
ORDER BY profit DESC
LIMIT 1;

Results:
The movie with the highest profit in the 21st century is identified.

7. How many people in the database are still alive?

SELECT COUNT(*)
FROM person
WHERE death_date IS NULL;

Results:
The query shows the count of people in the database who are still alive based on their birth and death dates.

8. Which year has the highest number of movie releases?

SELECT release_year, COUNT(film_id) AS num_films
FROM film
GROUP BY release_year
ORDER BY num_films DESC
LIMIT 1;

Results:
This query identifies the year with the highest number of movie releases.


Tools and Technologies Used:

1. PostgreSQL and PgAdmin4 for SQL queries and data retrieval.
2. Excel for additional descriptive analysis.
3. Tableau for visualizations and dashboard creation.

Dataset Overview
The dataset contains tables related to films, people (actors, directors, etc.), reviews, roles, and performance metrics such as gross revenue, IMDb scores, and user ratings.

Key Tables:
1. Films: Contains movie titles, release dates, gross revenues, etc.
2. People: Information on actors, directors, and their respective roles.
3. Reviews: User and critic reviews, IMDb scores.
4. Roles: Different film roles (e.g., director, actor, producer).

Data Analysis Process

1. Data Retrieval

Using SQL, I connected to the "film" database and retrieved the necessary information. All the tables were related, ensuring proper analysis. For example:

-- Query to retrieve top-grossing films
SELECT title, release_year, gross
FROM film
ORDER BY gross DESC
LIMIT 10;

2. Film Analysis

I used filtering and aggregation in SQL to address film related questions. Example:

-- Query to find films released in each country
SELECT country, COUNT(film_id) AS num_films
FROM film
GROUP BY country
ORDER BY num_films DESC
LIMIT 5;

3. People and Roles Analysis
For understanding the distribution of roles, I analyzed how many roles each person held in the database:

-- Query to find the top 10 actors and directors with the most roles
SELECT person.name, COUNT(role.role_id) AS role_count
FROM person
JOIN role ON person.person_id = role.person_id
GROUP BY person.name
ORDER BY role_count DESC
LIMIT 10;

4. User Reviews and Votes Analysis
I explored user and critic reviews to gain insights into audience satisfaction:

-- Query to calculate the average number of user and critic reviews
SELECT AVG(num_user) AS avg_user_reviews, AVG(num_critic) AS avg_critic_reviews
FROM review;

5. Visualizations
Using Tableau, I created visualizations to present the findings:

1. Total Sales (Gross) by Movie
2. Sales by Year (Trend Line)
3. Sales by Country (Geographical Map)

Conclusion
This project provided key insights into the film industry, including:

1. Top-grossing films and countries: Highlighting where production efforts are most successful.
2. IMDb scores and trends: Offering insights into audience satisfaction.
3. Yearly film release trends: Identifying periods of high movie production.
4. The analysis helps inform production strategies, marketing, and distribution efforts.




















































































