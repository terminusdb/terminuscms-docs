# Read documents in WOQL

> :note:
> To use this HowTo, first [clone the Star Wars
> demo](../../use-distributed-features/clone-a-demo.md) into your team on
> TerminusCMS. You will then have full access to the data needed for
> this tutorial.

You can read a document after finding the document id as follows:

```javascript
let v = Vars("doc", "id");
and(isa(v.id, "People"),
    triple(v.id, "label", string("Bossk")),
    read_document(v.id, v.doc))
```

This find a `People` document, makes sure it has the label `"Boosk"`
and then reads the document into the variable `doc`.
