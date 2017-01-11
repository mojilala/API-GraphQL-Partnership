# [WIP] MojiLaLa Partnership GraphQL API Documentation

12,000 original stickers by 300+ artists all over the world.

<p align="center">
<img align="center" src="graphiql.gif" width="100%" alt="MojiLaLa API"/>
</p>

## Access and API Keys

`api_key` param is required.

#### Public Key for sandbox:

* The public key for sandbox:"fCwSnMW0cR9BqTdrgWODZ1SdqWSmzAxA4NVu3Uho”

#### Request a production API Key

* Please send a message https://mojilala.com/partnership/

#### Endpoint

* The endpoint is http://api-partnerships.mojilala.net/v1/graphql

## Overview

GraphQL natively supports performing an introspection query. As our GraphQL schema matures, you will automatically receive new data types as we release updates to the platform. <a target="_blank" href="http://graphql.org/">More about GraphQL</a> 

### Using GraphiQL App
We recommend downloading and installing the GraphiQL App. This is the same editor that the GraphQL Explorer uses.

* Launch GraphiQL.
* Enter http://api-partnerships.mojilala.net/v1/graphql?api_key=fCwSnMW0cR9BqTdrgWODZ1SdqWSmzAxA4NVu3Uho to GraphQL Endpoint box and select `GET` method.


### GraphQL Explorer

* Visit http://api-partnerships.mojilala.net/v1/explorer.

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


+ [Featured Sticker Packages](#featured-sticker-packages)
+ [Featured Sticker Packages by FeaturedGroup id](#featured-sticker-packages-by-featuredgroup-id)
+ [Search Stickers](#search-stickers)
+ [Sticker by id](#sticker-by-id)
+ [Search Sticker Packages](#search-sticker-packages)
+ [Package by id](#package-by-id)
+ [Get stickers of Package](#get-stickers-of-package)
+ [Pagination](#pagination)



### Featured Sticker Packages

Example GraphQL Queries:


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
<a target="_blank" href="http://api-partnerships.mojilala.net/v1/explorer?query=%7B%0A%20%20featured%7B%0A%20%20%20%20edges%7B%0A%20%20%20%20%20%20node%7B%0A%20%20%20%20%20%20%20%20name%0A%20%20%20%20%20%20%20%20packages%7B%0A%20%20%20%20%20%20%20%20%20%20edges%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20node%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20name%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20defaultSticker%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20id%20%20%20%20%20%20%20%20%20%20%20%20%20%20%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20fileUrl%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D">See in Explorer</a>

Sample Response:
      
```json
{
  "data": {
    "featured": {
      "edges": [
        {
          "node": {
            "id": "RmVhdHVyZWRHcm91cC0z",
            "name": "Popular",
            "packages": {
              "edges": [
                {
                  "node": {
                    "name": "Miawsy",
                    "defaultSticker": {
                      "id": "U3RpY2tlci0xMDk5MQ==",
                      "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUc3/bVeAiynXfh59ENFa423TK8XlOjQK0buO5vXMheSE=.png"
                    }
                  }
                },
                {
                  "node": {
                    "name": "Smiley Upgrade",
                    "defaultSticker": {
                      "id": "U3RpY2tlci0xNjMxMw==",
                      "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUE2KPdFPWOWiZjzUK7hZf8hgYP8n9bVQ0uVyXgYhmyKU=.png"
                    }
                  }
                }                
              ]
            }
          }
        },        
        {
          "node": {
            "id": "RmVhdHVyZWRHcm91cC00Nw==",
            "name": "Animated Stickers",
            "packages": {
              "edges": [
                {
                  "node": {
                    "name": "Cute Little Wizard Stickers (Animated)",
                    "defaultSticker": {
                      "id": "U3RpY2tlci0xMTM3MA==",
                      "fileUrl": "https://cdn-stickers.mojilala.com/cld/3B2OheFn7op0r8JGS0RAG61el9LYUBQi03Dtzf5+YAES70YZ7CrWvAOFHkh19romKoetcYoQRp9BmgA1Rj0/AYAAZkyLf1PpoTbtQuOiJz1DaIhXchObK+h4RcR7vFDFQu6DLyOWn7YDvk0CznyFxsodxcv5LNvlukRa/6qOiwr76PBjpiMliu7juh2KTYBys36VDaup2U1GC2NebfLhwJRPp63iwDXMSQhvgTYvW+J0dAJadrgfBBR8k3zmHx1tDBxIH1j8pFa3NFchQh/EwREFxLEB+2gRMXQaJDMMwjxS/cXLn0XWd2p+w1qnA+2gs7+3l1xMZMKSzU2KIDkMOn4ScydnDpEW13tisLHCo4Ubyy7F5WWkCv7IMdHMZ9PzzhJgYhCiJlIdqwgCwwuDkpaU6FsIAhPNuRsAQPrLBaOTpqp7S6G1HPC/3qBcrvRLkMzJg1dcTE8wjhGkyYgrFaucFShqL2y9JnT3KM2pQqc=.png"
                    }
                  }
                },
                {
                  "node": {
                    "name": "NERDY BUNNY (Animated)",
                    "defaultSticker": {
                      "id": "U3RpY2tlci05NTQ1",
                      "fileUrl": "https://cdn-stickers.mojilala.com/cld/3B2OheFn7op0r8JGS0RAG61el9LYUBQi03Dtzf5+YAES70YZ7CrWvAOFHkh19romesb1rdMBNgLjzI3a66Z8wB4jmP/HgqY53CDINsU0QSgDZwxSf8h7UBqKwoo1q4e6ADmk2FplCDd4YSLEdPE8wc6htNMhXvJ5c4PBSxPmvxc+oahjwTEH/4UmAjVDVmuiKkq36zMzWaE5a+ZBsOVGmCaAFf4nwqIa5+R2b8/JPpc4EXJosnn/sY8s5+fyR6D40LCswdwG1pZ7iu2l70tzSvUYm3xTWH0/0k1jkXFE12hYXJDzw2A7dcUvuYm/M81l4P7gXdBYro+8DFz1xqszh6emqfT88LGJTHke0YL4AC6erinQ2qPtBQPwSS13Bg49RomhtmVa7+OnurwVjeTgVVo1+ju0Qg8gLzFTtByVaUE51G9NrwKFi68Oym+F8u+Cmh4dfS8zL0QQooI+pa4VeB8uMi3DG1LNe7git/5m6RQ=.png"
                    }
                  }
                }                
              ]
            }
          }
        },
        {
          "node": {
            "id": "RmVhdHVyZWRHcm91cC02NQ==",
            "name": "Holidays",
            "packages": {
              "edges": [
                {
                  "node": {
                    "name": "New Year's",
                    "defaultSticker": {
                      "id": "U3RpY2tlci0xOTIyMg==",
                      "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUv1ntnDI6IFbKl2/CJNkMs8ESVZTkx+Ycablgbgb31EA=.png"
                    }
                  }
                },
                {
                  "node": {
                    "name": "Chinese New Year",
                    "defaultSticker": {
                      "id": "U3RpY2tlci0xOTg2Ng==",
                      "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCU47IzZ0ARvBRuTYN+/KvOS45xPGyMmKsW5f3N+bKsZOk=.png"
                    }
                  }
                }
              ]
            }
          }
        }
      ]
    }
  }
}
```

### Featured Sticker Packages by FeaturedGroup id

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
      <p></p><p>id of FeaturedGroup</p> </td>
    <td>Yes</td>
  </tr>
  
  </tbody>
</table>

Example GraphQL Query:

```
{
  featuredGroup(id: "RmVhdHVyZWRHcm91cC0z") {
    id
    name
    packages(first: 2){
      edges{
        node{
          id
          name
          description
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
<a target="_blank" href="http://api-partnerships.mojilala.net/v1/explorer?query=%7B%0A%20%20featuredGroup(id%3A%20%22RmVhdHVyZWRHcm91cC0z%22)%20%7B%0A%20%20%20%20id%0A%20%20%20%20name%0A%20%20%20%20packages(first%3A%202)%20%7B%0A%20%20%20%20%20%20edges%20%7B%0A%20%20%20%20%20%20%20%20node%20%7B%0A%20%20%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20%20%20name%0A%20%20%20%20%20%20%20%20%20%20description%0A%20%20%20%20%20%20%20%20%20%20defaultSticker%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20%20%20%20%20fileUrl%0A%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A">See in Explorer</a>

Sample Response:

```json
{
  "data": {
    "featuredGroup": {
      "id": "RmVhdHVyZWRHcm91cC0z",
      "name": "Popular",
      "packages": {
        "edges": [
          {
            "node": {
              "id": "UGFja2FnZS03MTU=",
              "name": "Miawsy",
              "description": "Hi... I'm Miawsy! Let's join and share its daily life!",
              "defaultSticker": {
                "id": "U3RpY2tlci0xMDk5MQ==",
                "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUc3/bVeAiynXfh59ENFa423TK8XlOjQK0buO5vXMheSE=.png"
              }
            }
          },
          {
            "node": {
              "id": "UGFja2FnZS0xMDE5",
              "name": "Smiley Upgrade",
              "description": "Smileys on steroids, expressing themselves like never before.",
              "defaultSticker": {
                "id": "U3RpY2tlci0xNjMxMw==",
                "fileUrl": "https://cdn-stickers.mojilala.com/cld/j7S+d19qAItZjWLqxI2kNbu2BfjhZbcl8rJI5z+ux6S90/4sfEmHnpphl9ITlYY6mqxdsCYD7OsbgIAtpv9yk2luHNR4H28G3h5UaqDtxMaFwDIJpl898S4t8IBKls+BWD15U6wDFktK3IXoR37ORdCfi/XeByYonQKzxKSVJnNMm/7D7fJNeaYgJZRxuXCUE2KPdFPWOWiZjzUK7hZf8hgYP8n9bVQ0uVyXgYhmyKU=.png"
              }
            }
          }
        ]
      }
    }
  }
}
```


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
<a target="_blank" href="http://api-partnerships.mojilala.net/v1/explorer?query=%7B%0A%20%20stickers(query%3A%20%22Hello%22%2C%20language_code%3A%20%22en%22)%20%7B%0A%20%20%20%20edges%20%7B%0A%20%20%20%20%20%20node%20%7B%0A%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20fileUrl%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A">See in Explorer</a>


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
<a target="_blank" href="http://api-partnerships.mojilala.net/v1/explorer?query=%7B%0A%20%20stickers(query%3A%20%22Hello%22%2C%20isAnimated%3A%20true%2C%20language_code%3A%20%22en%22)%20%7B%0A%20%20%20%20edges%20%7B%0A%20%20%20%20%20%20node%20%7B%0A%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20fileUrl%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A">See in Explorer</a>


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
      <p></p><p>id of Sticker</p> </td>
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
<a target="_blank" href="http://api-partnerships.mojilala.net/v1/explorer?query=%7B%0A%20%20sticker(id%3A%20%22U3RpY2tlci0xNTU4Mw%3D%3D%22)%20%7B%0A%20%20%20%20id%0A%20%20%20%20fileUrl%0A%20%20%7D%0A%7D%0A">See in Explorer</a>

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

<a target="_blank" href="http://api-partnerships.mojilala.net/v1/explorer?query=%7B%0A%20%20packages(query%3A%20%22Hello%22%2C%20language_code%3A%20%22en%22)%20%7B%0A%20%20%20%20edges%20%7B%0A%20%20%20%20%20%20node%20%7B%0A%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20defaultSticker%20%7B%0A%20%20%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20%20%20fileUrl%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A">See in Explorer</a>

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
<a target="_blank" href="http://api-partnerships.mojilala.net/v1/explorer?query=%7B%0A%20%20packages(query%3A%20%22Hello%22%2C%20isAnimated%3A%20true%2C%20language_code%3A%20%22en%22)%20%7B%0A%20%20%20%20edges%20%7B%0A%20%20%20%20%20%20node%20%7B%0A%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20defaultSticker%20%7B%0A%20%20%20%20%20%20%20%20%20%20id%0A%20%20%20%20%20%20%20%20%20%20fileUrl%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A">See in Explorer</a>

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
      <p></p><p>id of Package</p> </td>
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

<a target="_blank" href="http://api-partnerships.mojilala.net/v1/explorer?query=%7B%0A%20%20package(id%3A%20%22UGFja2FnZS0xMjg3%22)%20%7B%0A%20%20%20%20id%0A%20%20%20%20name%0A%20%20%20%20description%0A%20%20%20%20defaultSticker%7B%0A%20%20%20%20%20%20id%0A%20%20%20%20%20%20fileUrl%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D">See in Explorer</a>
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

You can get pagination info with `pageInfo` field in connections (stickers, packages, featured).

Example GraphQL Query:

[See in Explorer](http://api-partnerships.mojilala.net/v1/explorer?query=%7B%0A%20%20stickers(query%3A%20%22Hello%22%2C%20first%3A%2010)%20%7B%0A%20%20%20%20pageInfo%7B%0A%20%20%20%20%20%20hasNextPage%0A%20%20%20%20%20%20hasPreviousPage%0A%20%20%20%20%20%20startCursor%0A%20%20%20%20%20%20endCursor%0A%20%20%20%20%7D%0A%20%20%20%20edges%20%7B%20%20%20%20%0A%20%20%20%20%20%20node%20%7B%0A%20%20%20%20%20%20%20%20fileUrl%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)
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

[See in Explorer](http://api-partnerships.mojilala.net/v1/explorer?query=%7B%0A%20%20stickers(query%3A%20%22Hello%22%2C%20first%3A%2010)%20%7B%0A%20%20%20%20totalCount%0A%20%20%20%20pageInfo%7B%0A%20%20%20%20%20%20hasNextPage%0A%20%20%20%20%20%20hasPreviousPage%0A%20%20%20%20%20%20startCursor%0A%20%20%20%20%20%20endCursor%0A%20%20%20%20%7D%0A%20%20%20%20edges%20%7B%20%20%20%20%0A%20%20%20%20%20%20node%20%7B%0A%20%20%20%20%20%20%20%20fileUrl%0A%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D)
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