# [WIP] MojiLaLa Partnership GraphQL API Documentation

12,000 original stickers by 300+ artists all over the world.

## Access and API Keys

`x-api-key` header is required.

#### Public Key for sandbox:

* The public key for sandbox:"fCwSnMW0cR9BqTdrgWODZ1SdqWSmzAxA4NVu3Uho”
* The endpoint is https://api-partnerships.mojilala.net/v1_sandbox/graphql

#### Request a production API Key

* Please send a message https://mojilala.com/partnership/
* The production endpoint is https://api-partnerships.mojilala.net/v1/graphql

## Overview

GraphQL natively supports performing an introspection query. As our GraphQL schema matures, you will automatically receive new data types as we release updates to the platform. The documentation on this repo will also be updated.

### Using GraphiQL
We recommend downloading and installing the GraphiQL App. This is the same editor that the GraphQL Explorer uses.

* Launch GraphiQL.
* Click Edit HTTP Headers.
* Add `x-api-key` header with `fCwSnMW0cR9BqTdrgWODZ1SdqWSmzAxA4NVu3Uho` value.
* Enter https://api-partnerships.mojilala.net/v1_sandbox/graphql to GraphQL Endpoint box and select `GET` method.

### Using curl or HTTP-speaking library
    
You can make a GraphQL query by issuing a `GET` request with a `query` and `variables` params. Params must be url encoded. For example:

GraphQL Query:
```
query { viewer { id }}
```

    
Request:

```
curl -X GET https://api-partnerships.mojilala.net/v1_sandbox/graphql?query=query%20%7B%20viewer%20%7B%20id%20%7D%7D -H "x-api-key: fCwSnMW0cR9BqTdrgWODZ1SdqWSmzAxA4NVu3Uho"
```



## Queries

Every GraphQL schema has a root type for both queries and mutations.

The root type defines how GraphQL operations begin. It is the entry point to constructing GraphQL queries.

For more information, see the [GraphQL spec](https://facebook.github.io/graphql/#sec-Type-System).

### Connections

#### stickers

A sticker.

##### Search stickers

Example GraphQL Query:
```
{
  stickers(query: "Hello", language_code: "en"){
    edges{
      node{
        id
        fileUrl
      }
    }
  }
}
```

##### Search animated stickers

Example GraphQL Query:
```
{
  stickers(query: "Hello", isAnimated: true, language_code: "en"){
    edges{
      node{
        id
        fileUrl
      }
    }
  }
}
```

#### packages

Collection of related stickers.

##### Search sticker packages

Example GraphQL Query:
```
{
  packages(query: "Hello", language_code: "en"){
    edges{
      node{
        id
        defaultSticker{
          id
          fileUrl
        }
      }
    }
  }
}
```

##### Search animated sticker packages

Example GraphQL Query:
```
{
  packages(query: "Hello", isAnimated: true, language_code: "en"){
    edges{
      node{
        id
        defaultSticker{
          id
          fileUrl
        }
      }
    }
  }
}
```

#### featured

Featured sticker packages as grouped.

Example GraphQL Query:
```
{
  featured{
    edges{
      node{
        name
        packages{
          edges{
            node{
              name
              defaultSticker{
                id              
                fileUrl
              }
            }
          }
        }
      }
    }
  }
}
```

### Fields

#### node
Fetches an object given its ID.

Example GraphQL Query:
```
{
  node(id: "UGFja2FnZS0zMTg=") {
    id
    __typename
    
  }
}
```

#### package

Example GraphQL Query:
```
{
  package(id: "UGFja2FnZS0zMTg=") {
    id
    name
    description
    defaultSticker{
      id
      fileUrl
    }    
  }
}
```

#### sticker

Example GraphQL Query:
```
{
  sticker(id: "U3RpY2tlci04ODQx") {
    id
    fileUrl
  }
}
```

#### featuredGroup

Example GraphQL Query:

```
{
  featuredGroup(id: "RmVhdHVyZWRHcm91cC0z") {
    id
    name
    packages{
      edges{
        node{
          defaultSticker{
            id
            fileUrl
          }
        }
      }
    }
  }
}
```


#### viewer
Unassociated viewer object queries.


## Pagination

You can paginate the connections.

### Pagination arguments


<table class="arguments" markdown="1">
  <thead>
    <tr>
      <th>Argument</th>
      <th>Type</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
  
  <tr>
    <td><code>first<code></code></code></td>
    <td><code>Int</code></td>
    <td>
      <p></p><p>Returns the first <em>n</em> elements from the list. Maximum 50.</p> </td>
  </tr>
  
  <tr>
    <td><code>after<code></code></code></td>
    <td><code>String</code> </td>
    <td>
      <p></p> <p>Returns the elements in the list that come after the specified global ID.</p></td>
  </tr>
  
  <tr>
    <td><code>last<code></code></code></td>
    <td><code>Int</code> </td>
    <td>
      <p></p><p>Returns the last <em>n</em> elements from the list. Maximum 50.</p></td>
  </tr>
  
  <tr>
    <td><code>before<code></code></code></td>
    <td> <code>String</code> </td>
    <td>
      <p></p>
<p>Returns the elements in the list that come before the specified global ID.</p> </td>
  </tr>
   
  
  </tbody>
</table>

### Pagination Info

You can get pagination info with `pageInfo` field in connections.

Example GraphQL Query:
```
{
  stickers(query: "Hello", first: 10) {
    pageInfo{
      hasNextPage
      hasPreviousPage
      startCursor
      endCursor
    }
    edges {    
      node {
        fileUrl
      }
    }
  }
}
```

If you do not provide `first` or `last` arguments `hasNextPage` and `hasPreviousPage` returns `false` all the time. It means if you want to use pagination you must provide `first` or `last` arguments.

### Total Count

You can get total nodes count of your query with `totalCount` field in connection. `totalCount` type is `Int`

Example GraphQL Query:
```
{
  stickers(query: "Hello", first: 10) {
    totalCount
    pageInfo{
      hasNextPage
      hasPreviousPage
      startCursor
      endCursor
    }
    edges {    
      node {
        fileUrl
      }
    }
  }
}
```