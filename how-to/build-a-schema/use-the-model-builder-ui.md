# Using the Model Builder UI

The model builder UI allows you to construct classes of objects and
define what data they have, and what links (or relationships) they
have between them.

## Make a New Data Product

First, log in to TerminusCMS, choose (or create) a team, and then
click on "New Data Product".

[Picture]

## Create a Class

Now click on the pink-bubbles on the left pannel. This takes you to
the schema builder page.

Hover over the grey schema bubble in the centre of the graph view.

[Picture]

This will give you a `+` icon. This will allow you to add either a
document class, or an enum. Choose *document*.

The document will appear as an orange Square and on the right hand
side you will have a panel for editing the schema. You can choose a
name for your new document class under the field `Unique ID*`.

Once you have chosen an id, you can (optionally) choose the *printed*
name of the document under `Label`.

## Add Properties

[Picture]

Now you can switch the properties tab, and click on `Add
Property`. This will give you a choice of a number of different
property types. You can choose `String` for instance for various
string properties.

Again you will have to give it a unique id, and by default the
property will be *optional*, but you can change this to *mandatory*,
*list* or *set*.

When you are done, click the Disk icon above (meaning save).

## Add Link Property

[Picture]

You can also add a link property by choosing `Link Property` under the
`AddProperty` selector once you have saved at least one document
class.

You must again specify an ID, and link to an already created document class.

## Add Enum

[Picture]

You can add an enum by clicking the `+` on the grey schema bubble and
selecting `Add Enum`.

After you have chosen a name for your enum, click on the `Values` tab
on the right, and begin entering valid values for this enum.

## Add an Enum Property

[Picture]

Now it is possible to link to this enum from any document class. You
can do this by selecting `Enum Property` under the `AddProperty`
selector.
