
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
