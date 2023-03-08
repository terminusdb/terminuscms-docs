# Adding a schema to TerminusCMS in the Python Client

After you have imported the `terminusdb_client`, and [created a
client](connect-with-python-client.md), and [connected to a
database](connect-to-a-database.md) you can create a schema.

## Insert schema document(s)

You can update the schema by adding well-formed JSON schema documents:

```python
schema = [{ '@type' : 'Class', '@id' : 'Country'},
          { '@type' : 'Class', '@id' : 'Person',
            'name' : 'xsd:string',
            'nationality' : 'Country'
          }]
results = client.insert_document(schema,graph_type="schema")
```
