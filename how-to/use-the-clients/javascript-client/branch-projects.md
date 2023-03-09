# Branch a Projects

*How-to create a new branch to TerminusDB and TerminusCMS using the JavaScript Client*

Assuming you have [connected with the JavaScript Client](./connect-to-javascript-client.md), creating a branch is the same for TerminusDB and TerminusCMS -
By deafult in TerminusDB or TerminusCMS you are working in the main branch.

Use this code to create a new branch starting from branch main head.

```js

const createBranch = async () => {
  await client.branch("mybranch");
  client.checkout("mybranch")
    
```

Now you are in branch mybranch.
You can create a new branch starting from "mybranch" head


```js
const createBranchFromMyBranch = async () => {
  await client.branch("branchFromMybranch","mybranch");
  client.checkout("branchFromMybranch")
    
```


