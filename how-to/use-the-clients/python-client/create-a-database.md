# Create a Database

To create a database with an already [connected
client](connect-with-python-client.md), you can write:

```python
dbid="MyDatabase"
label="My Database",
description="This is a database which is mine"
prefixes = {'@base' : 'iri:///mydatabase/',
            '@schema' : 'iri:///mydatabase#'}
team="MyTeam"
client.create_database(
    dbid,
    team,
    label=label,
    description=description,
    prefixes=prefixes)
```
