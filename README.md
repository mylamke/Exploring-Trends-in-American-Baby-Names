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

    select first_name, SUM(num) as top_5_baby_name
    from   glass-standard-378403.Baby_trend_name.usa_baby_names
    group by first_name
    order by sum(num) desc
    limit 5
    
![image](https://github.com/user-attachments/assets/0524a950-006c-43f1-8f1f-871568a8161c)




