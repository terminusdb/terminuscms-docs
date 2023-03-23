# Cloning a database

*How-to use the JS WOQLClient to clone a database*

## Clone a database from terminusdb.com to your local machine

Assuming you have [connected with the JavaScript Client](../../use-the-clients/javascript-client/connect-to-javascript-client.md) locally

Cloning a database pulls down a full copy of all the data that the db has at that point in time, including all versions of every documents and schema.

If the database that you are cloning is not public, you need to provide an APIKey to the client setting the remoteAuth
For more info see [How to get your API key](https://terminusdb.com/docs/terminuscms/get-api-key)

```js
const cloneLocally = async () => {
   client.remoteAuth( {"type":"apikey" , "key":myApiKey})
   const cloneDetails = {remote_url: "http://cloud.terminusdb.com/MyTeam/MyTeam/mydb", 
                        label "Cloned DB",
                        comment: "Cloned from mydb"}
   await  client.clonedb(cloneDetails, "new_mydb")

   console.log("the database has been cloned")
}
```





