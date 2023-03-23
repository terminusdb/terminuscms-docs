# Diff

*How-to use the JS WOQLClient to diff a specific object or a database branch data version*

## Diff a specific object

Return the diff from two objects

```js
const diffObjects = async () => {
   const before = { "@id" : "Person/Jane", "@type" : "Person", "name" : "Jane"}
   const after = { "@id" : "Person/Jane", "@type" : "Person", "name" : "Janine"}
   const options = {keep:{ "@id" : true, "name" : true }}
   
   //in options you can list the properties that you would like to see in the diff result in any case.
   const diffResult = await client.getJSONDiff = function (before, after, options) {

   console.log("the diff result ", JSON.stringify(diffResult,null,4))
}

```
Here an example of objects diff result

```json
{
   "name":{
      "@op":"ValueSwap",
      "@before":"Jane",
      "@after":"Janine"
   },
   "@id":"Person/Jane"
}
```


## Get the patch of difference between branches or commits.

```js
const diffDocsVersion = async () => {
   const beforeVersion = "a73ssscfx0kke7z76083cgswszdxy6l"
   const afterVersion =  "73rqpooz65kbsheuno5dsayh71x7wf4"
   const options = {keep:{ "@id" : true, "name" : true }}
   
   const diffResult = await client.getVersionDiff = function (beforeVersion, afterVersion, null, options) {

   console.log("the diff result ", JSON.stringify(diffResult,null,4))
}

```

here a result example

```json
[
   {
      "@id":"Person/Jane",
      "@type":"Person",
      "name" : "Jane"
      "age":{
         "@after":23,
         "@before":22,
         "@op":"SwapValue"
      }
   },
   {
      "@id":"Person/Tom",
      "@type":"Person",
      "name" : "Tom"
      "age":{
         "@after":10,
         "@before":null,
         "@op":"SwapValue"
      }
   }
]
```



## Get the patch of difference between a documents and an object.

```js
const diffDocToObject = async () => {
   const jsonObject = { "@id" : "Person/Jane", "@type" : "Person", "name" : "Jannet"}
   const options = {keep:{ "@id" : true, "name" : true }}
   
   //in options you can list the properties that you would like to see in the diff result in any case.
   const diffResult = await client.getVersionObjectDiff = function ("main", jsonObject, "Person/Jane", options) {

   console.log("the diff result ", JSON.stringify(diffResult,null,4))
}

```


