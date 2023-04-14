# What is 'schema weakening'?

A schema describes the shape of data in a data product. It provides
constraints and assurances about what kind of data will be retrieved.

However, often you need to *change* the schema in the process of
developing a data product.

## What is a weak versus a strong schema change?

A schema change is a *weakening* of the schema if the change can not
possibly invalidate any data which was present in the original schema.

Some examples of weakening include:

* Adding a new class which is not the parent of any existing class is
always valid since there are no elements of this class.

* Adding a new *optional* property to a class is also permitted.

* Changing a required field to *optional* or *set*.

Schema weakening is often a desirable approach to schema change as we
do not require alterations to any of our data. This can ensure a form
of backward compatibility which can avoid problems in long term
maintainence.

## Using weakened schemas safely

The *weakening* approach also suggests an appropriate style for the
consumption of data which is recieved by clients. The exact shape of a
document should not be relied on, as new optional properties could be
added, and required properties could be weakened to become
optional.

We should instead test for the existence of a field, before attempting
to consume it, and we should avoid clients requiring fields which are
not part of a *key*.

## Why do schemas evolve?

Schema evolution can happen at various phases in data product
development.

In the beginning of schema development it is often the case that the
schema evolves very rapidly as we try to capture the important
information for consideration or change the way it should be
represented.

In this phase it is common for schema changes to be *strong*, that is
they require that the data, if it exists, to be modified.

If there is very little data it can sometimes be more convenient to
delete the data and then alter the schema, to avoid schema
violations. Alternatively, one can try to use [schema
migration](../reference-guides/schema-migration.md) to achieve the
desired changes.

Later in schema evolution, there will be clients that rely on the
shape of data, and any strong change will require filling data,
deleting data, or modifying data which is associated with the existing
schema. This strong change will *require* [schema
migration](../reference-guides/schema-migration.md).

This also means that we need to pay special attention to keeping the
two in sync. This can best be done by focusing on schema weakening,
coupled with a defensive client style as described above.
