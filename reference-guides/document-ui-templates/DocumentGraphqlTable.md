## Documents UI - GraphQL Table

The `DocumentsGraphqlTable` element allows you to visualize document classes using iteractive cards.

## Installation

Install the dependencies from npm

```
npm install @terminusdb/terminusdb-documents-ui
npm install @terminusdb/terminusdb-react-table
npm install @terminusdb/terminusdb-documents-ui-templates
```

## Properties
| Properties |Description  |
|--|--|
|type| The document type
|gqlQuery|The GraphQL query|
|apolloClient| An apollo client instance - [documentation](https://www.apollographql.com/docs/react/)|
|tableConfig| An object with the table configuration|
|onRowClick|A function that acts as a callback when the table row is clicked|
|onViewButtonClick|A function that acts as a callback when the table row view button is clicked|
|onEditButtonClick|A function that acts as a callback when the table row edit button is clicked|
|onDeleteButtonClick|A function that acts as a callback when the table row delete button is clicked|
|showGraphqlTab|A boolean property to enable the GraphQL query view tab|

## Example
```js
import React,{useEffect} from "react"
import {DocumentsGraphqlTable,useTDBDocuments} from "@terminusdb/terminusdb-documents-ui-template"
import {gql} from "@apollo/client"
/**
 * 
 * @param {*} setSelected function to get selected document link by user 
 * @param {*} doctype document type selected
 * @returns 
 */
export const DocumentSearchComponent = ({setSelected, doctype,apolloClient,tdbClient}) => {
    const {documentTablesConfig,getGraphqlTablesConfig} = useTDBDocuments(tdbClient)

    useEffect(() => {
        if(doctype){       
            getGraphqlTablesConfig()         
        }
     },[doctype]);

    const querystr  = documentTablesConfig && documentTablesConfig.objQuery ? documentTablesConfig.objQuery[doctype].query : null
    const gqlQuery = querystr ? gql`${querystr}` : null
    if(!gqlQuery) return <div/>

    return  <DocumentsGraphqlTable tableConfig={documentTablesConfig} 
                type={doctype} 
                gqlQuery={gqlQuery}
                apolloClient={apolloClient}
                onRowClick={setSelected} 
                showGraphqlTab={false} />

}
```

you can see this code integrated inside a dashboard here
[DocumentSearchComponent full example code]()
[DocumentsGraphqlTable code]()
[View the complete example in Sandbox]()


