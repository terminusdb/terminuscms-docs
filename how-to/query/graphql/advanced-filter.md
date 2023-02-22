# Advanced Filtering with GraphQL

To use this HowTo, first [clone the Star Wars
demo](../use-distributed-features/clone-a-demo.md) into your team on
TerminusCMS. You will then have full access to the data needed for
this tutorial.

[Picture here]

Once you have cloned the database, go to the GraphQL icon (triangle in
hexagon) on the left hand side and select the filing cabinet icon.

TerminusDB exposes a *filter* object, which can be used to select
specific documents.

## Using a filter

You can type the following in the query panel:

```graphql
query{
   People(filter: { █ }){

   }
}
```

If at cursor point you type: `Ctrl-c` you'll get the list of options
you can choose from.

Let's choose `homeworld`


```graphql
query{
   People(filter: { homeworld: { █ }}){

   }
}
```

Now we can filter the homeworld from which the people we are
interested in come. We will use a `regex` because Tatooine is hard to
spell.

```graphql
query{
   People(filter: { homeworld: { label: { regex : "Tat.*" }}}){
     label
     homeworld{
       label
     }
   }
}
```

You can also find out what fields are available with the same `Ctrl-c`
trick.  Now, fire off the query above, and you'll see something like:

```
{
  "data": {
    "People": [
      {
        "label": "Luke Skywalker",
        "homeworld": {
          "label": "Tatooine"
        }
      },
      {
        "label": "Anakin Skywalker",
        "homeworld": {
          "label": "Tatooine"
        }
      },
      {
        "label": "C-3PO",
        "homeworld": {
          "label": "Tatooine"
        }
      },
      {
        "label": "Darth Vader",
        "homeworld": {
          "label": "Tatooine"
        }
      },
      {
        "label": "Shmi Skywalker",
        "homeworld": {
          "label": "Tatooine"
        }
      },
      {
        "label": "Owen Lars",
        "homeworld": {
          "label": "Tatooine"
        }
      },
      {
        "label": "Cliegg Lars",
        "homeworld": {
          "label": "Tatooine"
        }
      },
      {
        "label": "Beru Whitesun lars",
        "homeworld": {
          "label": "Tatooine"
        }
      },
      {
        "label": "R5-D4",
        "homeworld": {
          "label": "Tatooine"
        }
      },
      {
        "label": "Biggs Darklighter",
        "homeworld": {
          "label": "Tatooine"
        }
      }
    ]
  }
}
```

## A Bit of GraphQL theory

The filter is defined as part of the query for objects. If we look at
the `People` query in the Star Wars demo we see the following:

```graphql
type Query {
  People(
    id: ID
    ids: [ID!]

    """skip N elements"""
    offset: Int

    """limit results to N elements"""
    limit: Int
    filter: People_Filter

    """order by the given fields"""
    orderBy: People_Ordering
  ): [People!]!
}
```

This query exposes a `filter` argument, with the type of `People_Filter`.

A `People_Filter` in turn looks like:

```graphql
input People_Filter {
  birth_year: StringFilter
  created: DateTimeFilter
  desc: CollectionStringFilter
  edited: DateTimeFilter
  eye_color: StringFilter
  film: Film_Collection_Filter
  gender: StringFilter
  hair_colors: StringFilter
  height: StringFilter
  homeworld: Planet_Filter
  label: StringFilter
  mass: StringFilter
  skin_colors: StringFilter
  species: Species_Filter
  starship: Starship_Collection_Filter
  url: StringFilter
  vehicle: Vehicle_Collection_Filter
  _and: [People_Filter!]
  _or: [People_Filter!]
  _not: People_Filter
}
```

In this way we can recursively qualify all of the objects to which a
`People` might point to, terminating at leaves which use the various
concrete type filters.

For instance, the `StringFilter` looks like:

```graphql
input StringFilter {
  eq: String
  ne: String
  lt: String
  le: String
  gt: String
  ge: String
  regex: String
  startsWith: String
  allOfTerms: [String!]
  anyOfTerms: [String!]
}
```

We can specify any of these operands to narrow down our search. For
more information on the operations against concrete datatypes, see the
[GraphQL Reference](reference_here) section.
