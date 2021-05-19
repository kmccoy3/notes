
### SQL = "Structured Query Language"

BigQuery is an example of a big data database that you can work with:
```Python
from google.cloud import bigquery
```

First, you must create a `Client` object
```Python
client = bigquery.Client()
```

Now, construct a `reference` to the dataset of choice, using the name of the dataset and the project it is contained in using the `.dataset()` method:
```Python
dataset_ref = client.dataset("hacker_news", project="bigquery-public-data")
```

Next, obtain the dataset itself using the `.get_dataset()` method:
```Python
dataset = client.get_dataset(dataset_ref)
```

To list all of the tables in the dataset:
```Python
tables = list(client.list_tables(dataset))

for table in tables:  
    print(table.table_id)
```

Just like you fetch a database, you can fetch tables with the `.table()` and `.get_table()` methods:

```Python
table_ref = dataset_ref.table("full")

table = client.get_table(table_ref)
```

Client Organization:
* Client - hold projects, serves as connection to server
* Project - collection of datasets
* Dataset - collection of tables
* Table

### Schema

The structure of a table is called its `schema`
```python
# Print out schema
table.schema
```

Here, a column is synonymous with the term `field`, and contains the following information:
* name
* field type
* mode - NULLABLE, e.g.
* description

Use `.list_rows()` to preview table:
```Python
client.list_rows(table, max_results=5).to_dataframe()
```

To look at specific column:
```Python
client.list_rows(table, selected_fields=table.schema[:1], max_results=5).to_dataframe()
```
