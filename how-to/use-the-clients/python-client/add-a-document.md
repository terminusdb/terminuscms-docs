# Adding a Document to TerminusCMS in the Python Client

After you have imported the `terminusdb_client`, and [created a
client](connect-with-python-client.md), and [connected to a
database](connect-to-a-database.md), as well as [added some
schema](add-a-schema.md), you can then use this client to insert a
document which conforms to the schema.

## Insert a document

To insert a document, you should use `insert_document`:

```python
docment = { '@type' : 'Person', 'name' : "Jim" }
results = client.insert_document(document)
```

## Insert multiple documents

To insert multiple documents you can also invoke `insert_document`:

```python
docments = [{ '@type' : 'Person', 'name' : "Jim" },
            { '@type' : 'Person', 'name' : "Jill" }]
results = client.insert_document(document)
```

## Insert schema document(s)

Additionally, you can update the schema itself by adding schema
documents:

```python
schema = { '@type' : 'Class', '@id' : 'Person', 'name' : 'xsd:string'}
results = client.insert_document(schema,graph_type="schema")
```
