# Connect to a Database
How to connect to an existing database using the TerminusDB JavaScript Client

Assuming you have [connected with the JavaScript Client](./connect-to-javascript-client.md), connecting to a database is the same for TerminusDB and TerminusCMS -

The example code below registers your database in woqlClient parameters and then all your calls will be made to this db -

```js

client.db('ExampleDatabase')
client.getSchema().then(result=>{
    console.log(result)
})

```
