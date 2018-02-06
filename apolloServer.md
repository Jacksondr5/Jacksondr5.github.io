#### [Apollo Server](https://www.apollographql.com/docs/apollo-server/) and [graphql-tools](https://www.apollographql.com/docs/graphql-tools/)

| Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
| ------- | ---- | ---------------------- | --------------- | ---------------- |
| 5       | 3    | 4                      | 2               | 4                |

\*: These ratings assume you've already decided to use GraphQL

Apollo Server and graphql-tools are what we use to build the GraphQL API. Apollo Server configures the server to have a GraphQL endpoint while graphql-tools is what connects the GraphQL layer to our business logic. Most of the code is in the business logic that we define ourselves. We will use graphql-tools to teach the server how to resolve a query, how to get a Loan object when it has a User object, etc. Below are some pictures of code from the NEAT that show how we use these tools.

![Picutre of a graphql-tools query definition](https://jacksondr5.github.io/imgs/graphqlQueryDefinition.JPG)
_Here, we define some of the queries that clients can use. This gives the server the ability to validate queries **before** it tries to process them. We don't have to worry about the arguments our API is given, graphql-tools will check them for us._

![Picture of a graphql-tools resolver definition](https://jacksondr5.github.io/imgs/graphqlQueryResolvers.JPG)
_Here, we tell the server what functions to call when it recieves a query. These functions are completely seperate from GraphQL and 100% written by the developers._

![Picture of a resolver for the User type](https://jacksondr5.github.io/imgs/graphqlResolvingUserType.JPG)
_Here, we tell the server what functions should be called with it has a User and wants to get the User type's complex children._
