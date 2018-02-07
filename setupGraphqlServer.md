#### Setting up a GraphQL Server

_Be sure you've [set up Node and Yarn](https://jacksondr5.github.io/nodeYarn) first!_

_If you just want to play around with a small GraphQL instance, check out the [Playgrounds](https://jacksondr5.github.io/playgrounds) page first._

I recommend using [this starter project](https://github.com/Jacksondr5/starter-graphql-project) that I made. The documentation on Apollo's sites still needs some work, and it took me a while to get a setup that I liked. This should give you a good starting base for your project. Be sure to run `yarn` in the project directory to get all the dependencies. Once you tweak the code to your liking, run `yarn start` to start the server.

A few notes:

* This doesn't actually work. Since I'm hosting this on a public site, I removed anything that can relate to AgF systems. The purpose of this project is to give you a file structure that you can expand upon to make an app. If you're just trying to experiment with GraphQL, I recommend making your resolvers return constant data you define in the project instead of trying to connect to a DB/API.
* I recommend defining new types and their resolvers in their own file (like the `src/schema/User.js` file). This is not necessary at all, but it keeps your project clean. None of the sample projects I saw on the internet did this. I think this is one of those times where there's just a gap between tutorials and real code.
* Run `yarn start` to start the server. I've installed a package called [nodemon](https://www.npmjs.com/package/nodemon) that will watch your source code files for changes and restart the server when you save.
* Use [graphiql](https://github.com/graphql/graphiql) to test your API. `graphiql` is an IDE for your API. Load it up and you can test queries out in it. With my project, you can find it by going to localhost:8080/graphiql after you set up the server.

You are now set up to user GraphQL. From here, reference the [server](https://www.apollographql.com/docs/apollo-server/example.html) and [graphql-tool](https://www.apollographql.com/docs/graphql-tools/) docs. The `graqphql-tools` ones are the ones you'll use the most. They're a little hard to follow at times, so I'm working on cleaning up my source code and sharing it as a reference for what a real server looks like.
