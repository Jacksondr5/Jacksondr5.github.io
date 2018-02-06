####[Node](https://nodejs.org/en/) and [Express](http://expressjs.com/)

| Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
| ------- | ---- | ---------------------- | --------------- | ---------------- |
| 5       | 2    | 4                      | 2\*             | 4                |

\*:For our purposes there is not much to learn. Node and Express do have a lot of features, though.

Node is the event driven JavaScript runtime that we're using for our back end server. Our GraphQL API will run off of it. Node is the basis of the largest open source ecosystem in the world, and the Node team works with TC39, the working group that defines the ECMAScript spec. Millions of developers depend on Node, and it is a very stable and mature organization. I've rated them a 2 because Node is updated every year. However, only even numbered versions are given active and maintainence support, which extends for 2 years. We would only have to update every 2 years, and since the node runtime is based on the Chrome V8 engine, it is extremely unlikely that we will have any breaking changes.

Express is a framework for Node that provides a very simple web server. We only use it as a way to direct HTTP calls to the GraphQL server. It can do a lot more for us, but we don't need it to. It is one of the most widely used node packages (17 mil downloads last month), and is very stable.

These are the basis for our back end, but we do very little code with them.
