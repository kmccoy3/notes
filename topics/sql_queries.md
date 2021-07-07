
Using a sample table:
| ID     | Name | Pet | Animal |
| :----- | :--- | :-- | :----- |
| 1 | Kevin | Squiggles | Dog |
| 2 | Abigail | Scout | Cat |
| 3 | Brittany | Ranger | Cat |
| 4 | Chad | Legolas | Dog |
| 5 | David | Oreo | Dog |

### SELECT ... FROM

```Python
query = """
        SELECT Name
        FROM `bigquery-public-data.pet_records.pets`
        """
```

### SELECT ... FROM ... WHERE

```Python
query = """
        SELECT Name
        FROM `bigquery-public-data.pet_records.pets`
        WHERE Animal = 'Cat'
        """
```

Set up the query using **.query()** method:
```Python
query_job = client.query(query)
```

Use **.to_dataframe()** to print results of query:
```Python
us_cities = query_job.to_dataframe()
```

Can also select multiple columns, or all using `*`
```Python
query = """
        SELECT Name, Pet
        FROM `bigquery-public-data.pet_records.pets`
        WHERE Animal = 'Cat'
        """

query = """
        SELECT *
        FROM `bigquery-public-data.pet_records.pets`
        WHERE Animal = 'Cat'
        """
```

### Estimating Query Size

```Python
dry_run_config = bigquery.QueryJobConfig(dry_run=True)
dry_run_query_job = client.query(query, job_config=dry_run_config)
print("This query will process {} bytes.".format(dry_run_query_job.total_bytes_processed))
```

### Limiting Queries to Certain Size

```Python
ONE_GB = 1000*1000*1000 # file size in bytes
safe_config = bigquery.QueryJobConfig(maximum_bytes_billed=ONE_GB)
safe_query_job = client.query(query, job_config=safe_config)
job_post_scores = safe_query_job.to_dataframe()
```

```Python
first_query = """
              SELECT DISTINCT country
              FROM `bigquery-public-data.openaq.global_air_quality`
              WHERE unit = "ppm"
              """
```
```Python
zero_pollution_query = """
                       SELECT *
                       FROM `bigquery-public-data.openaq.global_air_quality`
                       WHERE value = 0
                       """
```

COUNT() SUM() AVG() MIN() MAX()

GROUP BY ... HAVING

```Python
query_popular = """
                SELECT parent, COUNT(id)
                FROM `bigquery-public-data.hacker_news.comments`
                GROUP BY parent
                HAVING COUNT(id) > 10
                """
```        
```Python
query = """
        SELECT COUNT(consecutive_number) AS num_accidents,
               EXTRACT(DAYOFWEEK FROM timestamp_of_crash) AS day_of_week
        FROM `bigquery-public-data.nhtsa_traffic_fatalities.accident_2015`
        GROUP BY day_of_week
        ORDER BY num_accidents DESC
        """
```

code_count_query = """
                   SELECT indicator_code, indicator_name, COUNT(1) as num_rows
                   FROM `bigquery-public-data.world_bank_intl_education.international_education`
                   WHERE year = 2016
                   GROUP BY indicator_code, indicator_name
                   HAVING COUNT(1) >= 175
                   ORDER BY COUNT(1) DESC
                   """


country_spend_pct_query = """
                          SELECT country_name, AVG(value) AS avg_ed_spending_pct
                          FROM `bigquery-public-data.world_bank_intl_education.international_education`
                          WHERE indicator_code = 'SE.XPD.TOTL.GD.ZS' and year >= 2010 and year <= 2017
                          GROUP BY country_name
                          ORDER BY avg_ed_spending_pct DESC
                          """

A common table expression (or CTE) is a temporary table that you return within your query. CTEs are helpful for splitting your queries into readable chunks, and you can write queries against them.



```Python
# Your code goes here
country_spend_pct_query = """
                          SELECT country_name, AVG(value) as avg_ed_spending_pct
                          FROM `bigquery-public-data.world_bank_intl_education.international_education`
                          WHERE indicator_code = "SE.XPD.TOTL.GD.ZS" and 2010 <= year and year <= 2017
                          GROUP BY country_name
                          ORDER BY AVG(value) DESC
                          """

# Set up the query (cancel the query if it would use too much of
# your quota, with the limit set to 1 GB)
safe_config = bigquery.QueryJobConfig(maximum_bytes_billed=10**10)
country_spend_pct_query_job = client.query(country_spend_pct_query, job_config=safe_config)

# API request - run the query, and return a pandas DataFrame
country_spending_results = country_spend_pct_query_job.to_dataframe()

# View top few rows of results
print(country_spending_results.head())

# Check your answer
q_1.check()
```





```python
rides_per_month_query = """
                        SELECT EXTRACT(MONTH FROM trip_start_timestamp) AS month,
                               COUNT(1) AS num_trips
                        FROM `bigquery-public-data.chicago_taxi_trips.taxi_trips`
                        WHERE EXTRACT(YEAR FROM trip_start_timestamp) = 2017
                        GROUP BY month
                        ORDER BY month
                        """
```

speeds_query = """
               WITH RelevantRides AS
               (
                   SELECT EXTRACT(HOUR FROM trip_start_timestamp) AS hour_of_day,
                          trip_miles,
                          trip_seconds
                   FROM `bigquery-public-data.chicago_taxi_trips.taxi_trips`
                   WHERE trip_start_timestamp > '2017-01-01' AND
                         trip_start_timestamp < '2017-07-01' AND
                         trip_seconds > 0 AND
                         trip_miles > 0
               )
               SELECT hour_of_day,
                      COUNT(1) AS num_trips,
                      3600 * SUM(trip_miles) / SUM(trip_seconds) AS avg_mph
               FROM RelevantRides
               GROUP BY hour_of_day
               ORDER BY hour_of_day
               """
