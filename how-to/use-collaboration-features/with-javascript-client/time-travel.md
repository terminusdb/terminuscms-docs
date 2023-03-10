# Time Travel through your database history

*How-to Time Travel To navigate to a specific commit*

Assuming you have [connected with the JavaScript Client](../../use-the-clients/javascript-client/connect-to-javascript-client.md), created different [branches](./branch-projects.md)

## Get the branch commits list

You can use the WOQL library method to get you branch commit using pagination
In the example below, you are get the last 10 commits starting from the branch head 

```js
const getCommits= async () => {
    const commits = await TerminusClient.WOQL.lib().commits("mybranch", 10 ,0);
    console.log("Show the last 10 commits", JSON.stringify(commits.bindings,null,4))
}
```
## Get the branch commits list starting by a specific timestamp

```js
const getCommitsByTime= async () => {
    const commits = await TerminusClient.WOQL.lib().commits("mybranch", 10 ,0, 1678385999.7790234);
    console.log("Show the last 10 commits before the timestamp", JSON.stringify(commits.bindings,null,4))
}
```

a response example

```json
[
      {
         "Author":{
            "@type":"xsd:string",
            "@value":"myuser@terminusdb.com"
         },
         "Commit ID":{
            "@type":"xsd:string",
            "@value":"prh0yvftqmsrgctn8gqvdxv7gc4i8p8"
         },
         "Message":{
            "@type":"xsd:string",
            "@value":"Update from model builder"
         },
         "Parent ID":"terminusdb://ref/data/ValidCommit/onckvm1q9u98j5momtsfxia3optjkdi",
         "Time":{
            "@type":"xsd:decimal",
            "@value":1678385762.7790234
         }
      },
      {
         "Author":{
            "@type":"xsd:string",
            "@value":"myuser@terminusdb.com"
         },
         "Commit ID":{
            "@type":"xsd:string",
            "@value":"onckvm1q9u98j5momtsfxia3optjkdi"
         },
         "Message":{
            "@type":"xsd:string",
            "@value":"Update from model builder"
         },
         "Parent ID":null,
         "Time":{
            "@type":"xsd:decimal",
            "@value":1678385749.9860663
         }
      }
   ]
```

## To time travel to you changes make the client point to a specific commit

You are registering your commit id in woqlClient parameters, all your calls will be made 
for this point 

```js
const getDocumentsAtCommit= async () => {
    client.ref("onckvm1q9u98j5momtsfxia3optjkdi")
    const docs = await client.getDocument({graph_type:"schema"})
}

```



