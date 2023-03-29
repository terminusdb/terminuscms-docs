# Add Documents

*How-to add documents to TerminusDB and TerminusCMS using the Python Client*

After you have imported the terminusdb_client, [created a client](./connect-with-python-client.md), [connected to a database](./connect-to-a-database.md), and [added a schema](./add-a-schema.md), you can insert a document that conforms to the schema.

## Insert documents

You can add documents to the database by using the `add_document` function:
```python
documents = [
    {
        "@type"   : "Player",
        "name"    : "George",
        "position": "Center Back",
    },
    {
        "@type"   : "Player",
        "name"    : "Doug",
        "position": "Full Back",
    },
    {
        "@type"   : "Player", 
        "name"    : "Karen", 
        "position": "Center Forward" 
    }
]
client.insert_document(documents)
```

