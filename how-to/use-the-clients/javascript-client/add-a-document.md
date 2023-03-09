# Add Documents

*How-to add documents to TerminusDB and TerminusCMS using the JavaScript Client*

After you have imported the terminusdb_client, and [created a client](./connect-to-javascript-client.md), and [connected to a database](./connect-to-a-database.md), and [added a schema](./add-a-schema.md), you can then use this client to insert a document that conforms to the schema.

## Insert documents

Add documents to the schema using addDocument:
```js
const objects = [
    {
        "@type" : "Player",
        name    : "George",
        position: "Center Back",
    },
    {
        "@type" : "Player",
        name    : "Doug",
        position: "Full Back",
    },
    { 
        "@type" : "Player", 
        name    : "Karen", 
        position: "Center Forward" 
    }
];

const addDocs = async () => {
  const result = await client.addDocument(objects);
  console.log("the documents have been added", result)
}
        

```
