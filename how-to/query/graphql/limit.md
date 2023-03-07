# Using `limit` to limit results in GraphQL

> :note:
> To use this HowTo, first [clone the Star Wars
> demo](../use-distributed-features/clone-a-demo.md) into your team on
> TerminusCMS. You will then have full access to the data needed for
> this tutorial.

<img src="https://assets.terminusdb.com/docs/how-to-clone-a-demo.png" alt="Clone the Star Wars demo from the TerminusCMS dashboard">

Once you have cloned the database, go to the GraphQL icon (triangle in
hexagon) on the left hand side and select the filing cabinet icon.

<img src="https://assets.terminusdb.com/docs/how-to-query-graphql.png" alt="GraphQL query playground in TerminusCMS">

There are two panels, one on the left for query, and one
on the right for results.

## Adding a limit

The `limit` keyword is an argument which can be passed to a query to
restrict the number of results to precisely the number supplied by the
argument.

For instance we can get exactly 5 people from the Star Wars universe
by specifying the query here:

```graphql
query{
   People(limit: 5){
      label
   }
}
```

This will result in

```json
{
  "data": {
    "People": [
      {
        "label": "Luke Skywalker"
      },
      {
        "label": "Obi-Wan Kenobi"
      },
      {
        "label": "Anakin Skywalker"
      },
      {
        "label": "Wilhuff Tarkin"
      },
      {
        "label": "Chewbacca"
      }
    ]
  }
}
```

If you want to page, to get the next results, you can use an
[offset](./offset.md)
