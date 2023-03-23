# Run a WOQl Query
How to connect to an existing database using the TerminusDB JavaScript Client

Assuming you have [connected with the JavaScript Client](./connect-to-javascript-client.md), connecting to a database, create e schema and insert data, now you would like to query you data

The example code below show a simple query that return all you databse triples 

```js
    const runQuery = async () => {
        const WOQL = Terminusdb.WOQL
        const v = WOQL.Vars("subject","predicate","object")
        const query = Terminusdb.WOQL.triple(v.subject,v.predicate,v.object)
        const result = await client.query(query)

        console.log("my query result", JSON.stringyfy(result,null,4))
    }    

```
