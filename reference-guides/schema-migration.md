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

Some operations are known as *weakening* operations, as they can
always be performed without altering the existing instance data. These
are essentially *backward* compatible operations.

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
  "class" : "MyClass" }
```

Which would take the schema:

```json
{ "@id" : "OtherClass",
  "@type" : "Class",
  "some_property" : "xsd:string"}
{ "@id" : "MyClass",
  "@type" : "Class",
  "my_property" : "xsd:string" }
```

to:

```json
{ "@id" : "OtherClass",
  "@type" : "Class",
  "some_property" : "xsd:string"}
```

## CreateClass

The `CreateClass` operation specifies the entire class to be
created. This operation is always a *weakening* operation.

```json
{ "@type" : "CreateClass",
  "class_document" : <ClassDocument> }
```

The migration:

```json
{ "@type" : "CreateClass",
  "class_document" :
  { "@id" : "MyClass",
    "@type" : "Class",
    "my_property" : "xsd:string" } }
```

Would take the schema:

```json
{ "@id" : "OtherClass",
  "@type" : "Class",
  "some_property" : "xsd:string"}
```

to:

```json
{ "@id" : "OtherClass",
  "@type" : "Class",
  "some_property" : "xsd:string"}
{ "@id" : "MyClass",
  "@type" : "Class",
  "my_property" : "xsd:string" }
```

## MoveClass

The `MoveClass` operation renames a class and all of the URIs of
instance data associated with that class. Due to the side-effects on
instance data, this is not a *weakening* operation.

```json

```
