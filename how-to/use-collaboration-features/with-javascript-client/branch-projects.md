# Branch a Projects

*How-to create a new branch to TerminusDB and TerminusCMS using the JavaScript Client*

Assuming you have [connected with the JavaScript Client](../../use-the-clients/javascript-client/connect-to-javascript-client.md), creating a branch is the same for TerminusDB and TerminusCMS -
By deafult in TerminusDB or TerminusCMS you are working in the main branch.

## Create a new branch from main branch
Use this code to create a new branch starting from branch main head.

```js

const createBranch = async () => {
  await client.branch("mybranch");
  client.checkout("mybranch")
}   
```
## Create a new branch from mybranch branch

Now you are in branch mybranch.
You can create a new branch starting from "mybranch" head


```js
const createBranchFromMyBranch = async () => {
  await client.branch("branch_from_mybranch","mybranch");
  client.checkout("branch_from_mybranch")
}   
```

## Get the branch list
you can get the database's branch list using a [WOQL]() library method 

```js

const getBranchList = async () => {
  const branchList = await TerminusClient.WOQL.lib().branches()
  console.log("ExampleDatabase branch list", JSON.stringify(branchList.bindings,null,4))
  
}   
```

Response example

```json
[
      {
         "Branch":"terminusdb://ref/data/Branch/main",
         "Head":"terminusdb://ref/data/InitialCommit/ohj33rrh5kmnmr9cq6vzfajfxog0629",
         "Name":{
            "@type":"xsd:string",
            "@value":"main"
         },
         "Timestamp":{
            "@type":"xsd:decimal",
            "@value":1678385706.694406
         },
         "commit_identifier":{
            "@type":"xsd:string",
            "@value":"ohj33rrh5kmnmr9cq6vzfajfxog0629"
         }
      },
      {
         "Branch":"terminusdb://ref/data/Branch/mybranch",
         "Head":"terminusdb://ref/data/ValidCommit/prh0yvftqmsrgctn8gqvdxv7gc4i8p8",
         "Name":{
            "@type":"xsd:string",
            "@value":"mybranch"
         },
         "Timestamp":{
            "@type":"xsd:decimal",
            "@value":1678385762.7790234
         },
         "commit_identifier":{
            "@type":"xsd:string",
            "@value":"prh0yvftqmsrgctn8gqvdxv7gc4i8p8"
         }
      },
      {
         "Branch":"terminusdb://ref/data/Branch/branch_from_mybranch",
         "Head":"terminusdb://ref/data/ValidCommit/prh0yvftqmsrgctn8gqvdxv7gc4i8p8",
         "Name":{
            "@type":"xsd:string",
            "@value":"branch_from_mybranch"
         },
         "Timestamp":{
            "@type":"xsd:decimal",
            "@value":1678385762.7790234
         },
         "commit_identifier":{
            "@type":"xsd:string",
            "@value":"prh0yvftqmsrgctn8gqvdxv7gc4i8p8"
         }
      }
   ]
```

>Check the [WOQL documentation]()



