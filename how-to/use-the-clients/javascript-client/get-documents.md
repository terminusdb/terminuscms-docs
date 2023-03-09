# Get Documents

*How-to get documents to TerminusDB and TerminusCMS using the JavaScript Client*

After you have added some documents in your database you can get a list of documents using getDocument as_list.  The 
results are shown further below.

```js
const getDocs = async () => {
  const documents = await client.getDocument({ as_list: "true" });
  console.log("All Documents", documents)
}
```

```json
[
  {
    '@id'   : 'Player/Doug',
    '@type' : 'Player',
    name    : 'Doug',
    position: 'Full Back'
  },
  {
    '@id'   : 'Player/George',
    '@type' : 'Player',
    name    : 'George',
    position: 'Center Back'
  },
  {
    '@id'   : 'Player/Karen',
    '@type' : 'Player',
    name    : 'Karen',
    position: 'Center Forward'
  }
]
```