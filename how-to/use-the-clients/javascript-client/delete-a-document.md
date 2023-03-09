# Delete a  Document

*How-to delete a document to TerminusDB and TerminusCMS using the JavaScript Client*

After you have added some documents in your database you can need to delete them. 
In order to delete a document you need to know the id

```js
const deleteDoc = async () => {
  const docId = "Player/George"
  await client.deleteDoc({id:docId});
  console.log(`the ${docId} has been deleted`)
}
```
