# Reset the branch head to a specific commit

*How-to use the JS WOQLClient to reset a branch*

Assuming you have created a database, and made a few commits, you [can time travel](./time-travel.md) to inspect them.
    
You may want to reset the branch to a specific commit. You will need your branch name and commit ID which can be obtained by time travelling. 

The below code will rest your branch to a specific commit ID - 

```js
const resetBranch = async () => {
   await  client.resetBracnh(mybranchName, mycommitid)
   console.log("Succesfully reset branch HEAD to mycommitid")
}
```






