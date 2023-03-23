# Reset the branch head to a specific commit

*How-to use the JS WOQLClient to reset a branch*

Assuming you have created a database, and made a few commits, you [can time travel](./time-travel.md) to inspect them.
    
This will set the branch to the submitted commit. 

```js
const resetBranch = async () => {
   await  client.resetBracnh(mybranchName, mycommitid)
   console.log("Succesfully reset branch HEAD to mycommitid")
}
```






