# Query Documents

*How-to perform basic document queries using the JavaScript Client*

Get a list of documents matching a query. For more advanced queries, take a look at the GraphQL and WOQL how-to guides.


```js
const queryDocuments = async () => {

  const queryTemplate = { "position": "Full Back" }

  const result = await client.getDocument({"@type":"Player","as_list":true,"query":queryTemplate});
  console.log("Query Documents",result)
}
```

```json
[{"@type" : "Player",
  "name" : "Doug",
  "position" : "Full Back"}]
```