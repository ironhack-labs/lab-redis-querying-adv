![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Lab | Redis: Querying the Movies Dataset (Advanced)

## Objective

This lab will help you practice querying data in Redis using Redis modules (RediSearch).  
You will learn how indexing enables more advanced and efficient queries.

## Dataset & Setup (Required)

This lab uses the Redis Movies dataset that includes:
- Movies
- Theaters
- Users
- Ratings
- Search indexes

Dataset and import instructions:  
https://github.com/RediSearch/redisearch-getting-started/blob/master/docs/006-import-dataset.md

Make sure the dataset is imported before starting the lab.

## Indexed Data Overview

RediSearch indexes are created during dataset import.

Example index:

* `idx:movies`

Indexes enable:

* Text search
* Numeric filtering
* Sorting
* Aggregation

## 1. Find Movies by Title Prefix

Find movies that start with "The Lord of the Rings".

```sh
FT.SEARCH idx:movies "The Lord of the Rings*"
```

## 2. Find Movies Released After 2010

```sh
FT.SEARCH idx:movies "@year:[2011 +inf]"
```

## 3. Get Movies by Genre

Find all movies labeled as "Action".

```sh
FT.SEARCH idx:movies "@genre:{Action}"
```

## 4. Get Movies with Ratings Between 7 and 9

```sh
FT.SEARCH idx:movies "@rating:[7 9]"
```

## 5. Get Top-Rated Movies

Retrieve the top 5 highest-rated movies.

```sh
FT.SEARCH idx:movies "*" SORTBY rating DESC LIMIT 0 5
```

## Additional Challenges

* Modify query #10 to return the top 10 rated movies
* Find Action movies released after 2015 with a rating above 8
* Compare performance between Basic Redis queries and RediSearch queries

---

**Happy querying!** :rocket: