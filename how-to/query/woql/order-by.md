# How to order results in WOQL

> :note:
> To use this HowTo, first [clone the Star Wars
> demo](../../use-distributed-features/clone-a-demo.md) into your team on
> TerminusCMS. You will then have full access to the data needed for
> this tutorial.

## Ordering results using `order_by`

The `order_by` keyword will allow you to sort results.

```javascript
let v = Vars("person", "label", "eyes", "group");
limit(2)
.order_by(["eyes", "desc"])
.select(v.eyes, v.group)
.group_by(
  "eyes",
  ["label"],
  v.group,
  and(triple(v.person, "rdf:type", "@schema:People"),
      triple(v.person, "label", v.label),
      triple(v.person, "eye_color", v.eyes)))
```

This returns the first two results of people, who have a given eye
color, sorted by eye color, in reverse order.

To get the alternative order, you can write:

```javascript
let v = Vars("person", "label", "eyes", "group");
limit(2)
.order_by(["eyes", "asc"])
.select(v.eyes, v.group)
.group_by(
  "eyes",
  ["label"],
  v.group,
  and(triple(v.person, "rdf:type", "@schema:People"),
      triple(v.person, "label", v.label),
      triple(v.person, "eye_color", v.eyes)))
```

Or simply:

```javascript
let v = Vars("person", "label", "eyes", "group");
limit(2)
.order_by("eyes")
.select(v.eyes, v.group)
.group_by(
  "eyes",
  ["label"],
  v.group,
  and(triple(v.person, "rdf:type", "@schema:People"),
      triple(v.person, "label", v.label),
      triple(v.person, "eye_color", v.eyes)))
```
