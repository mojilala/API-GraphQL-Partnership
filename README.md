# [WIP] MojiLaLa Partnership GraphQL API Documentation

12,000 original stickers by 300+ artists all over the world.

## Access and API Keys

`api_key` param is required.

#### Public Key for sandbox:

* The public key for sandbox:"fCwSnMW0cR9BqTdrgWODZ1SdqWSmzAxA4NVu3Uho”

#### Request a production API Key

* Please send a message https://mojilala.com/partnership/

#### Endpoint

* The endpoint is https://api-partnerships.mojilala.net/v1/graphql

## Overview

GraphQL natively supports performing an introspection query. As our GraphQL schema matures, you will automatically receive new data types as we release updates to the platform. The documentation on this repo will also be updated.

### Using GraphiQL
We recommend downloading and installing the GraphiQL App. This is the same editor that the GraphQL Explorer uses.

* Launch GraphiQL.
* Enter https://api-partnerships.mojilala.net/v1/graphql?api_key=fCwSnMW0cR9BqTdrgWODZ1SdqWSmzAxA4NVu3Uho to GraphQL Endpoint box and select `GET` method.

### Using curl or HTTP-speaking library
    
You can make a GraphQL query by issuing a `GET` request with a `query` and `variables` params. Params must be url encoded. For example:

GraphQL Query:
```
query { viewer { id }}
```

    
Request:

```
curl -X GET https://api-partnerships.mojilala.net/v1/graphql?query=query%20%7B%20viewer%20%7B%20id%20%7D%7D&api_key=fCwSnMW0cR9BqTdrgWODZ1SdqWSmzAxA4NVu3Uho
```



## Queries

Every GraphQL schema has a root type for both queries and mutations.

The root type defines how GraphQL operations begin. It is the entry point to constructing GraphQL queries.

For more information, see the [GraphQL spec](https://facebook.github.io/graphql/#sec-Type-System).


+ [Search Stickers](#search-stickers)
+ [Sticker by id](#sticker-by-id)
+ [Search Sticker Packages](#search-sticker-packages)
+ [Package by id](#package-by-id)
+ [Featured Sticker Packages](#featured-sticker-packages)
+ [Pagination](#pagination)


### Search Stickers

Arguments

<table class="arguments" markdown="1">
  <thead>
    <tr>
      <th>Argument</th>
      <th>Type</th>
      <th>Description</th>
      <th>Required</th>  
    </tr>
  </thead>
  <tbody>
  
  <tr>
    <td><code>query</code></td>
    <td><code>String</code></td>
    <td>
      <p></p><p>Search query term or phrase.</p> </td>
    <td>Yes</td>
  </tr>
  
  <tr>
      <td><code>isAnimated</code></td>
      <td><code>Boolean</code></td>
      <td>
        <p></p><p>Filter animated stickers.</p> </td>
      <td>Yes</td>
    </tr>
  
  <tr>
    <td><code>language_code</code></td>
    <td><code>String</code> </td>
    <td>
      <p></p> <p>For better search result.</p></td>
    <td>No</td>
  </tr>  
  </tbody>
</table>

Example GraphQL Queries:

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

Sample Response:
      
```json
{
  "data": {
    "stickers": {
      "edges": [
        {
          "node": {
            "id": "U3RpY2tlci0xNTU4Mw==",
            "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUzuxRovN4w+dB8SrqxyvTJGLmL+anEqAhyVJaWBfsQNk=.png"
          }
        },
        {
          "node": {
            "id": "U3RpY2tlci0xNTcyNw==",
            "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUY6WpWPLHkXT+O8SDzaIgF2cw6D62z7gNAGgd7PRICZg=.png"
          }
        }        
      ]
    }
  }
}
```


### Sticker by id

Arguments

<table class="arguments" markdown="1">
  <thead>
    <tr>
      <th>Argument</th>
      <th>Type</th>
      <th>Description</th>
      <th>Required</th>  
    </tr>
  </thead>
  <tbody>
  
  <tr>
    <td><code>id</code></td>
    <td><code>ID</code></td>
    <td>
      <p></p><p>id of sticker</p> </td>
    <td>Yes</td>
  </tr>
  
  </tbody>
</table>

Example GraphQL Query:

```
{
  sticker(id: "U3RpY2tlci0xNTU4Mw==") {
    id
    fileUrl
  }
}
```

Sample Response:

```json
{
  "data": {
    "sticker": {
      "id": "U3RpY2tlci0xNTU4Mw==",
      "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUzuxRovN4w+dB8SrqxyvTJGLmL+anEqAhyVJaWBfsQNk=.png"
    }
  }
}
```


### Search Sticker Packages

Arguments

<table class="arguments" markdown="1">
  <thead>
    <tr>
      <th>Argument</th>
      <th>Type</th>
      <th>Description</th>
      <th>Required</th>  
    </tr>
  </thead>
  <tbody>
  
  <tr>
    <td><code>query</code></td>
    <td><code>String</code></td>
    <td>
      <p></p><p>Search query term or phrase.</p> </td>
    <td>Yes</td>
  </tr>
  
  <tr>
      <td><code>isAnimated</code></td>
      <td><code>Boolean</code></td>
      <td>
        <p></p><p>Filter animated sticker packages.</p> </td>
      <td>Yes</td>
    </tr>
  
  <tr>
    <td><code>language_code</code></td>
    <td><code>String</code> </td>
    <td>
      <p></p> <p>For better search result.</p></td>
    <td>No</td>
  </tr>  
  </tbody>
</table>

Example GraphQL Queries:

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

Sample Response:
      
```json
{
  "data": {
    "packages": {
      "edges": [
        {
          "node": {
            "id": "UGFja2FnZS0xMjg3",
            "defaultSticker": {
              "id": "U3RpY2tlci0yMDY5OQ==",
              "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUFPnOAOGky+SUvKyFd3Jca/5RlZb/vLdPlVBj0XDiNB4=.png"
            }
          }
        },
        {
          "node": {
            "id": "UGFja2FnZS04NTQ=",
            "defaultSticker": {
              "id": "U3RpY2tlci0xMzc3OQ==",
              "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUCRfep9RoiQaeT6xWZPxwquUDg68KjiCv3b0TjqiIHD0=.png"
            }
          }
        }
      ]
    }
  }
}
```


### Package by id

Arguments

<table class="arguments" markdown="1">
  <thead>
    <tr>
      <th>Argument</th>
      <th>Type</th>
      <th>Description</th>
      <th>Required</th>  
    </tr>
  </thead>
  <tbody>
  
  <tr>
    <td><code>id</code></td>
    <td><code>ID</code></td>
    <td>
      <p></p><p>id of package</p> </td>
    <td>Yes</td>
  </tr>
  
  </tbody>
</table>

Example GraphQL Query:

```
{
  package(id: "UGFja2FnZS0xMjg3") {
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

Sample Response:

```json
{
  "data": {
    "package": {
      "id": "UGFja2FnZS0xMjg3",
      "name": "President Obama 2",
      "description": "アメリカへ行ってみたくて、オバマさんに会えるなら、本当にいいことですね。＾＾",
      "defaultSticker": {
        "id": "U3RpY2tlci0yMDY5OQ==",
        "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUFPnOAOGky+SUvKyFd3Jca/5RlZb/vLdPlVBj0XDiNB4=.png"
      }
    }
  }
}
```


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