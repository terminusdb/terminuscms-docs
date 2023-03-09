# Create a Database

*How-to create a database using the TerminusDB JavaScript Client*

To create a database with an already [connected client](./connect-to-javascript-client.md), you can write:

```js
const createNewDB = async () => {
  try {
​
      await client.createDatabase('ExampleDatabase', {
          label: "ExampleDatabase",
          comment: "Created new ExampleDatabase",
          schema: true
      });
​
      console.log("Database created Successfully!")
​
  } catch (err) {
      console.error(err)
  }
};
​
```

After the database will be created the client will be connected with it.

Try out the five-part tutorial to get to grips with it.

> Try out the [Getting Started with the TerminusDB JavaScript Client](https://github.com/terminusdb/terminusdb-tutorials/blob/main/getting_started/javascript-client/lesson_1.md) five-part tutorial to get to grips with it.
