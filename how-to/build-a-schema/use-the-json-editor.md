# Using the JSON View for building a Schema

You can edit a schema directly as JSON in the TerminusCMS user
interface using the JSON view.

## Make a New Data Product

First, log in to TerminusCMS, choose (or create) a team, and then
click on "New Data Product".

[Picture]

## Create a schema as JSON

Now click on the pink-bubbles on the left pannel. This takes you to
the schema builder page. In this page, you'll see displayed your
entire schema as JSON.

[Picture]

If you click on the Edit button in the upper right hand corner, you'll
be able to directly edit the schema.

If you have no data in your database, it should be possible to freely
edit the schema. However, if you have data, then you may not be able
to make arbitrary edits. The schema editor will warn you upon
submission if some restrictions are violated.

Essentially it should *always* be possible to
[weaken](../explanations/weakening.md) the schema safely through the
interface. However, other changes will require [schema
migration](../reference-guides/schema-migration.md).
