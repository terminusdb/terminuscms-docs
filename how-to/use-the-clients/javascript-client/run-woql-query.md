# Run a WOQl Query
*A quick example showing you how to query using WOQL*

Assuming you have [connected with the JavaScript Client](./connect-to-javascript-client.md), have a database, added a schema and some data, you now would like to query the database.

The example code below shows a simple query that returns all of the database's triples 

```js
    const runQuery = async () => {
        const WOQL = Terminusdb.WOQL
        const v = WOQL.Vars("subject","predicate","object")
        const query = Terminusdb.WOQL.triple(v.subject,v.predicate,v.object)
        const result = await client.query(query)

        console.log("my query result", JSON.stringyfy(result,null,4))
    }    

```

For more information and examples about querying with WOQL please see the [how-to query with WOQL guide](../../how-to/query/woql)
