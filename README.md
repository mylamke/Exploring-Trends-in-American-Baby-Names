# Exploring-Trends-in-American-Baby-Names

# 1 Project Description

How have American baby name tastes changed since 1920? Which names have remained popular for over 100 years, and how do those names compare to more recent top baby names? These are considerations for many new parents, but the skills you'll practice while answering these queries are broadly applicable. After all, understanding trends and popularity is important for many businesses, too!

You'll be working with data provided by the United States Social Security Administration, which lists first names along with the number and sex of babies they were given to in each year. For processing speed purposes, the dataset is limited to first names which were given to over 5,000 American babies in a given year. The data spans 101 years, from 1920 through 2020.

## The Data

### `baby_names`

| column         | type    | description                                                                  |
| -------------- | ------- | ------------------------------------------------------------------------ |
| `year`         | int     | year                                                                     |
| `first_name`   | varchar | first name                                                               |
| `sex`          | varchar | `sex` of babies given `first_name`                                       |
| `num`          | int     | number of babies of `sex` given `first_name` in that `year`              |

1/ Top 5 baby name 

    SELECT first_name, SUM(num) as top_5_baby_name
    FROM   glass-standard-378403.Baby_trend_name.usa_baby_names
    GROUP BY first_name
    ORDER BY sum(num) desc
    LIMIT 5

| first_name | top_5_baby_name |
|------------|-----------------|
| James      | 4748138         |
| John       | 4510721         |
| Robert     | 4495199         |
| Michael    | 4278824         |
| William    | 3614424         |


2/  the classic name and trendy name over the years

    SELECT
    first_name,
    SUM(num) as num,
    CASE WHEN COUNT(year) > 80 THEN 'Classic'
         WHEN COUNT(year) > 50 THEN 'Semi-classic'
         WHEN COUNT(year) > 20 THEN 'Semi-trendy'
         ELSE 'Trendy' END AS popularity_type
    FROM glass-standard-378403.Baby_trend_name.usa_baby_names
    GROUP BY first_name
    ORDER BY num desc
    LIMIT 20
    
| first_name  | num     | popularity_type |
|-------------|---------|-----------------|
| James       | 4748138 | Classic         |
| John        | 4510721 | Classic         |
| Robert      | 4495199 | Classic         |
| Michael     | 4278824 | Classic         |
| William     | 3614424 | Classic         |
| David       | 3571498 | Classic         |
| Mary        | 3215850 | Classic         |
| Richard     | 2414838 | Classic         |
| Joseph      | 2361382 | Classic         |
| Thomas      | 2166802 | Classic         |
| Charles     | 2112352 | Classic         |
| Christopher | 2012792 | Semi-classic    |
| Daniel      | 1824274 | Classic         |
| Matthew     | 1567204 | Semi-classic    |
| Patricia    | 1479802 | Semi-classic    |
| Elizabeth   | 1436286 | Classic         |
| Jennifer    | 1404743 | Semi-trendy     |
| Linda       | 1361021 | Semi-trendy     |
| Anthony     | 1344352 | Classic         |
| Barbara     | 1343901 | Semi-classic    |


