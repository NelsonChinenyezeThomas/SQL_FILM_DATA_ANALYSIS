# Exploratory Data Analysis on Film Data Using PostgreSQL

## Project Overview

This project applies SQL skills to perform exploratory data analysis (EDA) on a film database containing information about films, people, reviews, and roles. The objective is to extract insights related to film performance, distribution, audience engagement, and more, answering key business questions in the film industry.

### Key Objectives:
- Use SQL queries to retrieve and analyze data from the "film" database.
- Answer real-life business questions related to the film industry.
- Present findings using clear and concise visualizations.

---

## Key Questions Answered

### 1. What are the top 10 highest-grossing films in the database, and when were they released?

```sql
SELECT title, release_year, gross
FROM film
ORDER BY gross DESC
LIMIT 10;

Results:
The top five countries with the most film releases are shown, highlighting where the most movies are produced.

