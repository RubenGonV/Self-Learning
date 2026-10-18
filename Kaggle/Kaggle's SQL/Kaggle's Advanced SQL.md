---
tags:
  - SQL
  - Kaggle
First Created: 2025-12-03T14:43:00
---
---
```table-of-contents
maxLevel:1
```
---
# 1. JOINs and UNIONs

Now you'll learn about a few more types of **JOIN**, along with how to use **UNIONs** to pull information from multiple tables.

## JOINs
Recall that we can use an INNER JOIN to pull rows from both tables where the value in the `Pet_ID` column in the owners table has a match in the `ID` column of the pets table.

![[Pasted image 20251203125615.png]]

### LEFT JOIN 
To create a table containing all rows from the `owners` table, we use a **LEFT JOIN**. In this case, "left" refers to the table that appears before the **JOIN** in the query. ("Right" refers to the table that is after the **JOIN**.)

### RIGHT JOIN
If we instead use a **RIGHT JOIN**, we get the matching rows, along with all rows in the right table (whether there is a match or not).

### FULL JOIN
Finally, a **FULL JOIN** returns all rows from both tables. Note that in general, any row that does not have a match in both tables will have NULL entries for the missing values. You can see this in the image below.

![[Pasted image 20251216105733.png]]

![[sql joins.png]]

---
## UNIONs

As you've seen, **JOINs** horizontally combine results from different tables. If you instead would like to vertically concatenate columns, you can do so with a **UNION**. 

Note that with a **UNION**, the data types of both columns must be the same, but the column names can be different.

We use **UNION ALL** to include duplicate values. If you'd like to drop duplicate values, you need only change **UNION ALL** in the query to **UNION DISTINCT**.

>[!example] Select all usernames corresponding to users who wrote stories or comments on January 1, 2014.
>We'll work with the [Hacker News](https://www.kaggle.com/hacker-news/hacker-news) dataset. Specifically the `comments` table, and the `stories` table.
>```python
># Query to select all users who posted stories or comments on January 1, 2014
>union_query = """
>              SELECT c.by
>              FROM `bigquery-public-data.hacker_news.comments` AS c
>              WHERE EXTRACT(DATE FROM c.time_ts) = '2014-01-01'
>              UNION DISTINCT
>              SELECT s.by
>              FROM `bigquery-public-data.hacker_news.stories` AS s
>              WHERE EXTRACT(DATE FROM s.time_ts) = '2014-01-01'
>              """
>
># Run the query, and return a pandas DataFrame
>union_result = client.query(union_query).result().to_dataframe()
>union_result.head()
>```

---

# 2. Analytic Functions

In the Intro to SQL micro-course, you learned how to use **aggregate functions** (Group By, Having & Count), which perform calculations based on sets of rows. In this tutorial, you'll learn how to define **analytic functions**, which also operate on a set of rows. However, unlike aggregate functions, analytic functions return a (potentially different) value for each row in the original table.

![[Pasted image 20260112094836.png]]
All analytic functions have an **OVER** clause, which defines the sets of rows used in each calculation. The **OVER** clause has three (optional) parts:

- The **PARTITION BY** clause divides the rows of the table into different groups. In the query above, we divide by `id` so that the calculations are separated by runner.
- The **ORDER BY** clause defines an ordering within each partition. In the sample query, ordering by the `date` column ensures that earlier training sessions appear first.
- The final clause (`ROWS BETWEEN 1 PRECEDING AND CURRENT ROW`) is known as a **window frame** clause. It identifies the set of rows used in each calculation. We can refer to this group of rows as a **window**. (_Actually, analytic functions are sometimes referred to as **analytic window functions** or simply **window functions**!_)

![[Pasted image 20260112094841.png]]

There are many ways to write window frame clauses:

- `ROWS BETWEEN 1 PRECEDING AND CURRENT ROW` - the previous row and the current row.
- `ROWS BETWEEN 3 PRECEDING AND 1 FOLLOWING` - the 3 previous rows, the current row, and the following row.
- `ROWS BETWEEN UNBOUNDED PRECEDING AND UNBOUNDED FOLLOWING` - all rows in the partition.

Of course, this is not an exhaustive list, and you can imagine that there are many more options!

## Three types of analytic functions

The example above uses only one of many analytic functions. BigQuery supports a wide variety of analytic functions, and we'll explore a few here.

### 1) Analytic aggregate functions

As you might recall, **AVG()** (from the example above) is an aggregate function. The **OVER** clause is what ensures that it's treated as an analytic (aggregate) function. **Aggregate functions** take all of the values within the window as input and return a single value.

- **MIN()** (or **MAX()**) - Returns the minimum (or maximum) of input values
- **AVG()** (or **SUM()**) - Returns the average (or sum) of input values
- **COUNT()** - Returns the number of rows in the input

### 2) Analytic navigation functions

**Navigation functions** assign a value based on the value in a (usually) different row than the current row.

- **FIRST_VALUE()** (or **LAST_VALUE()**) - Returns the first (or last) value in the input
- **LEAD()** (and **LAG()**) - Returns the value on a subsequent (or preceding) row

### 3) Analytic numbering functions

**Numbering functions** assign integer values to each row based on the ordering.

- **ROW_NUMBER()** - Returns the order in which rows appear in the input (starting with `1`)
- **RANK()** - All rows with the same value in the ordering column receive the same rank value, where the next row receives a rank value which increments by the number of rows with the previous rank value. ==IT DOESN'T TAKE AN ARGUMENT==


---

# 3. Nested and Repeated Data

## Nested data

![[Pasted image 20260118124530.png]]
We refer to the "Toy" column in the `pets_and_toys` table as a **nested** column, and say that the "Name" and "Type" fields are nested inside of it. Nested columns have type **STRUCT** (or type **RECORD**). This is reflected in the table schema below.

To query a column with nested data, we need to identify each field in the context of the column that contains it:
- `Toy.Name` refers to the "Name" field in the "Toy" column, and
- `Toy.Type` refers to the "Type" field in the "Toy" column.

## Repeated data

Now consider the (more realistic!) case where each pet can have multiple toys. In this case, to collapse this information into a single table, we need to leverage a different datatype.

![repeated data](https://storage.googleapis.com/kaggle-media/learn/images/S93FJTE.png)

We say that the "Toys" column contains **repeated data**, because it permits more than one value for each row. This is reflected in the table schema below, where the mode of the "Toys" column appears as **'REPEATED'**. Each entry in a repeated field is an **ARRAY**, or an ordered list of (zero or more) values with the same datatype.

When querying repeated data, we need to put the name of the column containing the repeated data inside an **UNNEST()** function.
![[Pasted image 20260118131204.png]]

## Nested and repeated data

![[Pasted image 20260118131344.png]]
Since the "Toys" column is repeated, we flatten it with the **UNNEST()** function. And, since we give the flattened column an alias of `t`, we can refer to the "Name" and "Type" fields in the "Toys" column as `t.Name` and `t.Type`, respectively.

![[Pasted image 20260118131403.png]]

---

# 4. Writing Efficient Queries

Most database systems have a **query optimizer** that attempts to interpret/execute your query in the most effective way possible. But several strategies can still yield huge savings in many cases.

We will use two functions to compare the efficiency of different queries:
- `show_amount_of_data_scanned()` shows the amount of data the query uses.
- `show_time_to_run()` prints how long it takes for the query to execute.

## Strategies

### 1) Only select the columns you want

It is tempting to start queries with **SELECT * FROM ...**. It's convenient because you don't need to think about which columns you need. But it can be very inefficient.

This is especially important if there are text fields that you don't need, because text fields tend to be larger than other fields.

> [!example]
> 
> ```python
> star_query = "SELECT * FROM `bigquery-public-data.github_repos.contents`"
> show_amount_of_data_scanned(star_query)
> 
> basic_query = "SELECT size, binary FROM `bigquery-public-data.github_repos.contents`"
> show_amount_of_data_scanned(basic_query)
> ```
> ```output
> Data processed: 2682.118 GB
> Data processed: 2.531 GB
> ```


### 2) Read less data

Both queries below calculate the average duration (in seconds) of one-way bike trips in the city of San Francisco.

> [!example]
> ```sql
> more_data_query = """
>                   SELECT MIN(start_station_name) AS start_station_name,
>                       MIN(end_station_name) AS end_station_name,
>                       AVG(duration_sec) AS avg_duration_sec
>                   FROM `bigquery-public-data.san_francisco.bikeshare_trips`
>                   WHERE start_station_id != end_station_id 
>                   GROUP BY start_station_id, end_station_id
>                   LIMIT 10
>                   """
> show_amount_of_data_scanned(more_data_query)
> 
> less_data_query = """
>                   SELECT start_station_name,
>                       end_station_name,
>                       AVG(duration_sec) AS avg_duration_sec                  
>                   FROM `bigquery-public-data.san_francisco.bikeshare_trips`
>                   WHERE start_station_name != end_station_name
>                   GROUP BY start_station_name, end_station_name
>                   LIMIT 10
>                   """
> show_amount_of_data_scanned(less_data_query)
> ```
> 
> ```output
> Data processed: 0.076 GB
> Data processed: 0.06 GB
> ```

Since there is a 1:1 relationship between the station ID and the station name, we don't need to use the `start_station_id` and `end_station_id` columns in the query. By using only the columns with the station names, we scan less data.

### 3) Avoid N:N JOINs

Most of the JOINs that you have executed in this course have been **1:1 JOINs**. In this case, each row in each table has at most one match in the other table.

![[Pasted image 20260118182847.png]]

Another type of JOIN is an **N:1 JOIN**. Here, each row in one table matches potentially many rows in the other table.

![[Pasted image 20260118182906.png]]

Finally, an **N:N JOIN** is one where a group of rows in one table can match a group of rows in the other table. Note that in general, all other things equal, this type of JOIN produces a table with many more rows than either of the two (original) tables that are being JOINed.

![[Pasted image 20260118182938.png]]

> [!example]
> Now we'll work with an example from a real dataset. Both examples below count the number of distinct committers and the number of files in several GitHub repositories.
> 
> ```sql
> big_join_query = """
>                  SELECT repo,
>                      COUNT(DISTINCT c.committer.name) as num_committers,
>                      COUNT(DISTINCT f.id) AS num_files
>                  FROM `bigquery-public-data.github_repos.commits` AS c,
>                      UNNEST(c.repo_name) AS repo
>                  INNER JOIN `bigquery-public-data.github_repos.files` AS f
>                      ON f.repo_name = repo
>                  WHERE f.repo_name IN ( 'tensorflow/tensorflow', 'facebook/react', 'twbs/bootstrap', 'apple/swift', 'Microsoft/vscode', 'torvalds/linux')
>                  GROUP BY repo
>                  ORDER BY repo
>                  """
> show_time_to_run(big_join_query)
> 
> small_join_query = """
>                    WITH commits AS
>                    (
>                    SELECT COUNT(DISTINCT committer.name) AS num_committers, repo
>                    FROM `bigquery-public-data.github_repos.commits`,
>                        UNNEST(repo_name) as repo
>                    WHERE repo IN ( 'tensorflow/tensorflow', 'facebook/react', 'twbs/bootstrap', 'apple/swift', 'Microsoft/vscode', 'torvalds/linux')
>                    GROUP BY repo
>                    ),
>                    files AS 
>                    (
>                    SELECT COUNT(DISTINCT id) AS num_files, repo_name as repo
>                    FROM `bigquery-public-data.github_repos.files`
>                    WHERE repo_name IN ( 'tensorflow/tensorflow', 'facebook/react', 'twbs/bootstrap', 'apple/swift', 'Microsoft/vscode', 'torvalds/linux')
>                    GROUP BY repo
>                    )
>                    SELECT commits.repo, commits.num_committers, files.num_files
>                    FROM commits 
>                    INNER JOIN files
>                        ON commits.repo = files.repo
>                    ORDER BY repo
>                    """
> 
> show_time_to_run(small_join_query)
> ```
> 
> ```output
> Time to run: 13.028 seconds
> Time to run: 4.413 seconds
> ```
> The first query has a large N:N JOIN. By rewriting the query to decrease the size of the JOIN, we see it runs much faster.


---

# Learn more

These strategies and many more are discussed in [this thorough guide](https://www.oreilly.com/library/view/google-bigquery-the/9781492044451/) to Google BigQuery. If you'd like to learn more about how to write more efficient queries (or deepen your knowledge of all things BigQuery), you're encouraged to check it out!