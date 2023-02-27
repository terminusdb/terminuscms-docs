# How to group results in WOQL

> :note:
> To use this HowTo, first [clone the Star Wars
> demo](../../use-distributed-features/clone-a-demo.md) into your team on
> TerminusCMS. You will then have full access to the data needed for
> this tutorial.

## How to use `GroupBy`

If we need to group variables according to some criteria, we can
create an aggregate of solutions using `groupBy`.

A group by is composed of a *focus*, a *template*, and a *group*
together with a query.

We will demonstrate this with the following query:

```javascript
let v = Vars("person", "label", "eyes", "group");
limit(1)
.group_by(
  "eyes",
  ["label"],
  v.group,
  and(triple(v.person, "rdf:type", "@schema:People"),
      triple(v.person, "label", v.label),
      triple(v.person, "eye_color", v.eyes)))
```

The first argument, here `"eyes"` refers to the eyes variable, and is
the variable around which to form the group, the *focus*.

The second `["label"]` is the *template*, which refers to the variable
`"label"`. The template will be those things grouped under the first
variable.

The third variable `v.group`, is the *group* variable, which will
include groups of templates for each set of solutions which shares a
*focus*.

This raw query output will be:

```json
{
	"eyes": {
		"@type": "xsd:string",
		"@value": "black"
	},
	"group": [
		[{
			"@type": "xsd:string",
			"@value": "Greedo"
		}],
		[{
			"@type": "xsd:string",
			"@value": "Nien Nunb"
		}],
		[{
			"@type": "xsd:string",
			"@value": "Gasgano"
		}],
		[{
			"@type": "xsd:string",
			"@value": "Kit Fisto"
		}],
		[{
			"@type": "xsd:string",
			"@value": "Plo Koon"
		}],
		[{
			"@type": "xsd:string",
			"@value": "Lama Su"
		}],
		[{
			"@type": "xsd:string",
			"@value": "Taun We"
		}],
		[{
			"@type": "xsd:string",
			"@value": "Shaak Ti"
		}],
		[{
			"@type": "xsd:string",
			"@value": "Tion Medon"
		}],
		[{
			"@type": "xsd:string",
			"@value": "BB8"
		}]
	],
	"label": null,
	"person": null
}
```
