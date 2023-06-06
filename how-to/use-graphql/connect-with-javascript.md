# Connect with javascript

> :note:
> This tutorial gets you up and running with TerminusDB graphql and [Apollo Client](https://www.apollographql.com/docs/react/get-started/).

1. Install dependencies 

```bash 
    npm install @apollo/client graphql
```

2. Initialize ApolloClient and Connect with TerminusDB
Import the dependencies that we need

```js
import { ApolloClient, InMemoryCache, ApolloProvider, gql,HttpLink,ApolloLink } from '@apollo/client';

```

Initialize ApolloClient, passing its constructor a configuration object with the TerminusDB server endpoint, user's credentials
and cache fields:
> :note 
> you'll find extra information about apollo client cache in apollo client web site

## Connect with terminusDB local

```js
const orgName = "myOrganizationName"
const dbName = "myDBname"
const myBranch = "main"

const user = "admin"
const password = "mypass"
const userPassEnc = btoa(`${user}:${password}`)

const terminusdbURL = `http://127.0.0.1:6363/api/graphql/${orgName}/${dbName}/local/branch/${myBranch}/`

const httpLink = new HttpLink({ uri: terminusdbURL });
const authMiddleware = new ApolloLink((operation, forward) => {
    // add the authorization to the headers
    operation.setContext(({ headers = {} }) => ({
    headers: {
        ...headers,
        authorization: `Basic ${userPassEnc}`}
    }));
    return forward(operation);
})
    
const cache = new InMemoryCache({
    addTypename: false
});

const value = concat(authMiddleware, httpLink)

const apolloClient = new ApolloClient({
    cache:cache,
    link: value,       
});

3. Query your database

apolloClient
  .query({
    query: gql`
     query{
        Person{
        _id
        name
        }
    }
    `,
  })
  .then((result) => console.log(result));
```

## Connect with terminusCMS 
> :note:
> How get your [api token](link to api token page) to connect with terminusCMS

```js
const orgName = "myOrganizationName"
const dbName = "myDBname"
const myBranch = "main"

const user = "admin"
const password = "mypass"
const userPassEnc = btoa(`${user}:${password}`)

const terminusdbURL = `https://cloud.terminusdb.com/${orgName}/api/graphql/${orgName}/${dbName}/local/branch/${myBranch}/`
const myAPIToken = 'replaceYourToken'

const httpLink = new HttpLink({ uri: terminusdbURL });
const authMiddleware = new ApolloLink((operation, forward) => {
    // add the authorization to the headers
    operation.setContext(({ headers = {} }) => ({
    headers: {
        ...headers,
        authorization: `Token ${myAPIToken}`}
    }));
    return forward(operation);
})
    
const cache = new InMemoryCache({
    addTypename: false
});

const value = concat(authMiddleware, httpLink)

const apolloClient = new ApolloClient({
    cache:cache,
    link: value,       
});

3. Query your database

apolloClient
  .query({
    query: gql`
     query{
        Person{
        _id
        name
        }
    }
    `,
  })
  .then((result) => console.log(result));



