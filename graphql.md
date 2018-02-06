### [GraphQL](http://graphql.org/)

_Here we will go over how the NEAT will handle getting and modifying data._

GraphQL is a new spec for building APIs, it tries to solve some of the problems REST and other APIs have with flexability and scalability. What I go over here will seem like overkill for the admin tool, but I think that most of the benefits from GraphQL are really worthwhile when we look beyond this one simple app. Instead, think of the GrqphQL back end I'm building as a service that can be comsumed by every other app in the Online Banking portfolio, as well as by other apps and services within the bank. I believe that's where the strengths of GraphQL become much more worthwhile.

On this page, I'll talk about GraphQL as a spec. For information on the actual libraries I'm using to implement GraphQL, check out the Apollo Client and Apollo Server pages.

GraphQL has 2 main benefits:

* A type system that describes the data the service can give and consume
* A single endpoint that accepts queries

##Typed API

Defining types in our API gives us the ability to be explicit about what data clients can consume. Clients can know exacty what data they're getting, and what format it will be in. Clients don't have to worry about null or type checking data after we send it. Below is an example definition for the User type in the NEAT API. We spell out exactly what data a User has, what type each piece of data is, and whether or not it can be null (denoted by !).
![Picture of User type definition](https://github.com/Jacksondr5/Jacksondr5.github.io/blob/master/imgs/graphqlUserSchemaDef.jpg)
It also allows our clients to tell us exactly what data they need. Often we have times where different clients will need different data. The admin tool needs a user's history, but AccountAccess doesn't. Normal APIs don't have a built in way to manage this, but GraphQL types open up this possibility. In some cases, with a normal API, we might have to build out 2 endpoints to deal with this problem, leading to more code duplication, making it harder to make big changes in the future.

##Queries on a Single Endpoint

Normal APIs deal with requests. A client hits an endpoint, provides some parameters, and the client returns a response. That response isn't guarenteed to have all the information that the client wants. The client may have to go back to other endpoints to request more data. This makes programming the client more difficult, as developers have to deal with resolving multiple requests and more networking errors.
![Picture of multiple User requests]()
Once all the requests come in, the client has many loosely coupled pieces of data it needs to piece together, and it probably has more data than it needs. This is more of a problem on mobile connections, where loading speed and data plans become much more important factors we need to consider.

GraphQL servers have one endpoint that you can send a query to. Clients can reference the data's types to ask the server for related data in a single request:
![Picture of graphiql request]()
The above request would have taken multiple round trips to the server to fulfill on a normal REST API.

##Implemting GraphQL
![Picture of GraphQL system](https://github.com/Jacksondr5/Jacksondr5.github.io/blob/master/imgs/graphqlSystemDiagram.JPG)
Above is a picture of some wonderful PowerPoint art that shows what our system will look like with GraphQL implemented. As you can hopefully see, GraphQL exists as a thin layer on the server and (optionally) the client. All of the code related to fetching data from databases and other places is contained in the business logic, which we write **100%** of. GraphQL gives us a way to draw relations between our data, but it doesn't handle how to actually get that data. This makes GraphQL a much smaller dependency than it might seem to be.

#One Final Note
It's important to mention that while this is a JavaScript technology, and there are a few client side implementations of GraphQL, you don't actually need any dependency on the client side. GraphQL endpoints accept query strings and return JSON data, so any client that can format and send a string can query a GraphQL API. This makes it easy for other services in the bank to consume our API. If they don't need to make extensive use of the API, or have mostly static queries, thay don't need a fancy library to use it.
