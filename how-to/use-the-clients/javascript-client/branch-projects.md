# Branch a Projects

*How-to create a new branch to TerminusDB and TerminusCMS using the JavaScript Client*

Assuming you have [connected with the JavaScript Client](./connect-to-javascript-client.md), creating a branch is the same for TerminusDB and TerminusCMS -
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
  await client.branch("branchFromMybranch","mybranch");
  client.checkout("branchFromMybranch")
}   
```

## Get the branch list
you can get the database's branch list using a [WOQL]() library method 

```js

const getBranchList = async () => {
  const branchList = await TerminusClient.WOQL.lib().branches()
  console.log("ExampleDatabase branch list", JSON.stringify(branchList,null,4))
  
}   
```

>Check the [WOQL documentation]()



