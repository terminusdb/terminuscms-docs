# Using the Model Builder UI

The model builder UI allows you to construct classes of objects and
define what data they have, and what links (or relationships) they
have between them.

## Make a New Data Product

First, log in to TerminusCMS, choose (or create) a team, and then
click on `New Data Product`.

<img src="https://assets.terminusdb.com/docs/new-data-product.png" alt="Create a new data product using the TerminusDB/TerminusCMS dashboard">

## Create a Class

Now click on the pink-bubbles on the left pannel. This takes you to
the schema builder page.

Hover over the gray schema bubble in the centre of the graph view.

<img src="https://assets.terminusdb.com/docs/schema-ui-no-docs.png" alt="JSON schema editor in the TerminusCMS dashboard">

This will give you a `+` icon. This will allow you to add either a
document class, or an enum. Choose *document*.

The document will appear as an orange Square and on the right hand
side you will have a panel for editing the schema. You can choose a
name for your new document class under the field `Unique ID*`.

Once you have chosen an id, you can (optionally) choose the *printed*
name of the document under `Label`.

## Add Properties

<img src="https://assets.terminusdb.com/docs/schema-ui-doc-properties.png" alt="Add document properties using the schema builder UI">

Now you can switch the properties tab, and click on `Add
Property`. This will give you a choice of a number of different
property types. You can choose `String` for instance for various
string properties.

Again you will have to give it a unique id, and by default the
property will be *optional*, but you can change this to *mandatory*,
*list* or *set*.

When you are done, click the Disk icon above (meaning save).

## Add Link Property

<img src="https://assets.terminusdb.com/docs/schema-ui-doc-link-properties.png" alt="Add link properties to a document using the schema builder UI">

You can also add a link property by choosing `Link Property` under the
`AddProperty` selector once you have saved at least one document
class.

You must again specify an ID, and link to an already created document class.

## Add Enum

<img src="https://assets.terminusdb.com/docs/schema-ui-doc-enum.png" alt="Create an enum for your schema using the schema builder UI">

You can add an enum by clicking the `+` on the gray schema bubble and
selecting `Add Enum`.

After you have chosen a name for your enum, click on the `Values` tab
on the right, and begin entering valid values for this enum.

## Add an Enum Property

<img src="https://assets.terminusdb.com/docs/schema-ui-doc-add-enum-property.png" alt="Add an enum property to a document using the schema builder UI">

Now it is possible to link to this enum from any document class. You
can do this by selecting `Enum Property` under the `AddProperty`
selector.
