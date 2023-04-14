# Run a WOQL query

*This how-to guide provides an example of the WOQL query language using the Python client.*

It assumes that you have [installed the client](./install-the-python-client.md), [connected to a database](./connect-to-a-database.md), and [connected with a client](./connect-with-python-client.md).

## WOQLQuery

Writing WOQL queries in Python is fairly simple. We have a WOQLQuery class which can be used to construct WOQL Queries.

A simple example, in which we get all the names of the people in the database:


```python
from terminusdb_client import WOQLQuery, WOQLClient

query = WOQLQuery().woql_and(
    WOQLQuery().triple('v:PersonId', 'rdf:type', '@schema:Person'),
    WOQLQuery().trople('v:PersonId', '@schema:name', 'v:Name')
)
result = client.query(query)
```
