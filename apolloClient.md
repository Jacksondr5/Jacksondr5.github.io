#### [Apollo Client](https://www.apollographql.com/client/)

| Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
| ------- | ---- | ---------------------- | --------------- | ---------------- |
| 3       | 3    | 1-2                    | 1               | 3-4              |

\*: These ratings assume you've already decided to use GraphQL

_Apollo Client is a client side library that handles interacting with the GraphQL server for us. It makes cachnig, pagination, and websockets easier for us to use._

Apollo client lives as a thin layer in our app. It interfaces with the GraphQL server for us, handling caching, errors, server events, and more. The footprint in our code is small. It basically replaces AJAX calls.
