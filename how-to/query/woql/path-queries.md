# Path Queries in WOQL

> :note:
> To use this HowTo, first [clone the Star Wars
> demo](../../use-distributed-features/clone-a-demo.md) into your team on
> TerminusCMS. You will then have full access to the data needed for
> this tutorial.

## How to use `path`

TerminusCMS gives us [path
queries](../../../reference-guides/path-queries.md) which allow us to
succinctly express chains of relationships.

The `path` keyword allows you to find a path through the graph
traversing intermediate edges. An example would be finding the group
of individuals who have at some point shared a vehicle as pilot, or
piloted another vehicle who in turn was shared with someone. This is a
*transitive* relationship and will explore the entire graph.

For instance

```javascript
let v = Vars("person1", "person2");
path(v.person1, "(<pilot,pilot>)+", v.person2)
```

This `path` means we follow the `pilot` field *backwards* (because of
the `<` arrow), to the vehicle of which the person is a pilot and then
follow it forwards `pilot>` any number of times *but at least once*
which is what the `+` means.

The path itself can also be returned by adding another field, as so:

```javascript
let v = Vars("person1", "person2", "path");
path(v.person1, "(<pilot,pilot>)+", v.person2, v.path)
```

This can be inspected to understand the manner in which we got from
`person1` to `person2`.
