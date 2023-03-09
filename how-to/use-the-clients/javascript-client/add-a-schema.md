# Add a Schema

*Add a schema to TerminusDB and TerminusCMS using the TerminusDB JavaScript Client*

After you have imported the terminusdb_client, and [created a client](./connect-to-javascript-client.md), and [connected to a database](./connect-to-a-database.md) you can create a schema.

## Create a schema

You can create a JSON schema, in this example we'll create a schema with one object called Player with two properties name and position with the name forming the lexical key:

```js

const schema = { "@type" : "Class",
                 "@id"   : "Player",
                 "@key"  : { "@type": "Lexical", "@fields": ["name"] },
                 name    : "xsd:string",
                 position: "xsd:string" };
```

## Add the schema
Add the schema object with:

```js
const addSchema = async () => {
  const result = await client.addDocument(schema,  { graph_type: "schema" });
  console.log("the schema has been created", result)
}
```
