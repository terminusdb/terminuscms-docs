# Edit a  Document

*How-to update a  document to TerminusDB and TerminusCMS using the JavaScript Client*

After you have added some documents in your database you can need to update them. 
You need to [get you document](./get-documents.md) and make your change and update it.

```js
const docs = {
    '@id'   : 'Player/George',
    '@type' : 'Player',
    name    : 'George',
    position: 'Center Back' 
  }

docs.position = "Full Back"

const updateDocs = async () => {
  const result = await client.updateDocument(docs);
  console.log("updated document", result)
}

```
