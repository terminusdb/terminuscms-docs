# Import data with the Python client

This how-to assumes that you are already connected to a database and made a schema that matches the CSV you want to import.

## Importing a CSV file

You can import CSV files easily by importing them into dictionaries using Python's built-in libaries.
Those dictionary objects can be inserted in the database using the `insert_document` function.

```python
import csv

objects = []
with open('test.csv', 'r') as f:
    csv_reader = csv.DictReader(f)
    objects = list(csv_reader)

client.insert_document(objects)
