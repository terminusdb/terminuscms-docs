# Schema Migration

Schema migration allows us to move schema and instance data together
automatically in a replayable fashion. This is essential for allowing
flexible schemas to co-exist nicely with change-requests and merges.

The schema operations can be performed directly on the branch of
interest, or you can *target* the schema of a given branch in another
branch, allowing the migrations to be re-performed such that a new
common schema is obtained.

In addition, schema migrations can be *inferred* in some cases, and
TerminusCMS will attempt to silently infer migrations which will not
impact instance data.

However, some schema operations require instance data to change, and
such alterations must be asked for explicitly.

## Schema Migration Operations

There are a number of schema operations which can be performed which
will change one schema into another. These are specified by passing an
ordered list of operations. The operations are sometimes order
dependent so different operations orders can lead to different changes
to the instance data.

Some operations are known as [weakening](../explanations/weakening.md)
operations, as they can always be performed without altering the
existing instance data. These are essentially *backward compatible*
operations. This includes changing a range to a less specific or
optional range, adding new optional fields, or adding new classes.

## DeleteClass

The `DeleteClass` operation will remove a class from a schema. This
does not change the *range* of properties, so these properties must
first be dropped before deleting a class is possible.

Due to the fact that existing instance data of this class will be
deleted, this is not a *weakening* operation.

```json
{ "@type" : "DeleteClass",
  "class" : <ClassName> }
```

An example of the operation would be:

```json
{ "@type" : "DeleteClass",
  "class" : "Person" }
```

Which would take the schema:

```json
{ "@id" : "Dog",
  "@type" : "Class",
  "name" : "xsd:string"}
{ "@id" : "Person",
  "@type" : "Class",
  "name" : "xsd:string" }
```

to:

```json
{ "@id" : "Dog",
  "@type" : "Class",
  "name" : "xsd:string"}
```

## CreateClass

The `CreateClass` operation specifies the entire class to be
created. This operation is always a *weakening* operation.

```json
{ "@type" : "CreateClass",
  "class_document" : <ClassDocument> }
```

### Example

The migration:

```json
{ "@type" : "CreateClass",
  "class_document" :
  { "@id" : "Person",
    "@type" : "Class",
    "name" : "xsd:string" } }
```

Would take the schema:

```json
{ "@id" : "Dog",
  "@type" : "Class",
  "name" : "xsd:string" }
```

to:

```json
{ "@id" : "Dog",
  "@type" : "Class",
  "name" : "xsd:string"}
{ "@id" : "Person",
  "@type" : "Class",
  "name" : "xsd:string" }
```

## MoveClass

The `MoveClass` operation renames a class and all of the URIs of
instance data associated with that class. Due to the side-effects on
instance data, this is not a *weakening* operation.

```json
{ "@type" : "MoveClass",
  "from" : <FromClassName>,
  "to" : <ToClassName> }
```

### Example

```json
{ "@type" : "MoveClass",
  "from" : "Person",
  "to" : "Dog" }
```

Would take the schema:

```json
{ "@id" : "Person",
  "@type" : "Class",
  "name" : "xsd:string"}
```

to:

```json
{ "@id" : "Dog",
  "@type" : "Class",
  "name" : "xsd:string"}
```

## ReplaceClassMetadata

The `ReplaceClassMetadata` operation replaces the metadata on a class
(if it exists). This operation is always a *weakening* operation and
has no effect on instance data.

```json
{ "@type" : "ReplaceClassMetadata",
  "class" : <ClassName>
  "metadata" : <Metadata> }
```

### Example

The operation:

```json
{ "@type" : "ReplaceClassMetadata",
  "class" : "Person",
  "metadata" : { "ui_preferences" : { "colour" : "blue" } } }
```

Would take the schema:

```json
{ "@id" : "Person",
  "@type" : "Class",
  "@metadata" : { "ui_preferences" : { "colour" : "red" } },
  "name" : "xsd:string"}
```

to:

```json
{ "@id" : "Dog",
  "@type" : "Class",
  "@metadata" : { "ui_preferences" : { "colour" : "blue" } },
  "name" : "xsd:string" }
```

## ReplaceClassDocumentation

The `ReplaceClassDocumentation` operation replaces the documentation
on a class (if it exists). This operation is always a *weakening*
operation and has no effect on instance data.


```json
{ "@type" : "ReplaceClassDocumentation",
  "class" : <ClassName>
  "documentation" : <Documentation> }
```

### Example

The operation:

```json
{ "@type" : "ReplaceClassDocumentation",
  "class" : "Person",
  "documentation" : { "@comment" : "This is a person class",
                      "@properties" : { "name" : { "@comment" : "The name of a person",
                                                    "@label" : "name" } },
                      "@label" : "Person" } }
```

Would take the schema:

```json
{ "@id" : "Person",
  "@type" : "Class",
  "@documentation" : { "@comment" : "A Person",
                       "@properties" : { "name" : { "@comment" : "Name of a person",
                                                    "@label" : "name" } },
                       "@label" : "Person" },
  "name" : "xsd:string"}
```

to:

```json
{ "@id" : "Person",
  "@type" : "Class",
  "@documentation" : { "@comment" : "This is a person class",
                      "@properties" : { "name" : { "@comment" : "The name of a person",
                                                   "@label" : "name" } },
                      "@label" : "Person" },
  "name" : "xsd:string"}
```

## ReplaceContext

The `ReplaceContext` operation will update the context object, which
will change how URIs are compressed when returning data.

This operation is a *weakening* operation only when prefixes other than
`@base` and `@schema` are changed. Otherwise, all data in the database
will be moved to the new `@base` and `@schema` designations.

```json
{ "@type" : "ReplaceContext",
  "context" : <Context> }
```
