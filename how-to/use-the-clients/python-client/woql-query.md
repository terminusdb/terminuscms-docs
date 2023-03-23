# Run a WOQL query

In this how-to, we will guide you through ways of using the WOQL query language by
using the Python client.

This how-to assumes that you know how to use the [client](./install-the-python-client.md) and [connect to a database](./connect-to-a-database.md) already.

## WOQLQuery

Writing WOQL queries in Python is fairly simple. We have a WOQLQuery class which can be used to construct WOQL Queries.

A simple example, in which we get all the names of all the persons in the database. We assume that a client is already
constructed:


```python
from terminusdb_client import WOQLQuery, WOQLClient

query = WOQLQuery().woql_and(
    WOQLQuery().triple('v:PersonId', 'rdf:type', '@schema:Person'),
    WOQLQuery().trople('v:PersonId', '@schema:name', 'v:Name')
)
result = client.query(query)
```
