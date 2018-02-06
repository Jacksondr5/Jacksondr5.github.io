#### Setting up a GraphQL Server

_Be sure you've [set up Node and Yarn](https://jacksondr5.github.io/nodeYarn) first!_

_If you just want to play around with a small GraphQL instance, check out the [Playgrounds](https://jacksondr5.github.io/playgrounds) page first._

1. Create a project using `yarn init` in the directory where you want your project. It will ask you some questions, the only important one is the name, you can just hit enter for the other ones. Yarn will generate a `project.json` which holds information about your project.
2. Run `yarn add apollo-server-express graphql-tools grapql`
3. Place the following code into your index.js file

```javascript
const express = require('express');

// This package automatically parses JSON requests.
const bodyParser = require('body-parser');

//This package deals with CORS
const cors = require('cors');

// This package will handle GraphQL server requests and responses
// for you, based on your schema.
const { graphqlExpress, graphiqlExpress } = require('apollo-server-express');

//Your schame should be defined in this file
const schema = require('./schema.js');

// This package lets us make requests to SQL databases
const sql = require('mssql');

const config = {
  user: 'someUserName',
  password: 'theCorrectPassword',
  server: 'yourDBServer',
  database: 'yourDB',
};

// Connects mssql to the database
sql.connect(config);

var app = express();
app.use(cors());
app.use('/graphql', bodyParser.json(), graphqlExpress({ schema }));
// Optional, configures the Graphiql IDE at localhost:[port]/graphiql
app.use(
  '/graphiql',
  graphiqlExpress({
    endpointURL: '/graphql',
  }),
);

const PORT = 8080;
app.listen(PORT, () => {
  console.log(`GraphQL server running on port ${PORT}.`);
});
```

4. Define a schema in `\[yourProjectDir]/schema/index.js`

You are now set up to user GraphQL. From here, reference the [server](https://www.apollographql.com/docs/apollo-server/example.html) and [graphql-tool](https://www.apollographql.com/docs/graphql-tools/) docs. The `graqphql-tools` ones are the ones you'll use the most. They're a little hard to follow at times, so I'm working on cleaning up my source code and sharing it as a reference for what a real server looks like.
