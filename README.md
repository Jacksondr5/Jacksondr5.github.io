#### New E-Commerce Admin Tool Technology Overview and Setup Guide

&nbsp;&nbsp;&nbsp;&nbsp;Here I'll be going over the libraries and packages I'm currently using in the New E-Commerce Admin Tool (NEAT). I'm going to give a brief description of each, provide some links to resources so you can learn more, and tell you how to set up an environment to play around.

&nbsp;&nbsp;&nbsp;&nbsp;One thing I want to mention is that you’re going to see a large number of dependencies here. This might look like a lot of technical debt, but these tools are different than frameworks like .NET, Xamarin, or Angular. They’re usually pretty small. While .NET and Angular try to be frameworks that can do everything you could ever need to do, all of the dependencies here focus on doing one particular thing. In fact, the some of the developers that make these tools have stated that they intentionally limit the scope of their projects to keep things simple. This lets us carefully pick the stuff we need.

&nbsp;&nbsp;&nbsp;&nbsp;This is going to be a long discussion, so for each dependency, I've included a summary table that rates the dependency on benefit, risk, prevalence in our code, effort to learn, and effort to remove. Here's a reference for that table.

| Rating | Benefit                                                                                                 | Risk                                                                                                                    | Prevalence in our Code                                                                                        | Effort to Learn                                            | Effort to Remove                                     |
| ------ | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------- |
| 1      | We honestly could do without this. It’s a nicety                                                        | This is stable code with a large community and great backers                                                            | Occurs in very few places / Is completely separate from production code and tests                             | Almost no effort                                           | We can delete this on a whim, at any point in time   |
| 2      | There are tangible benefits, but it’s not completely necessary                                          | This is a well-maintained project that is unlikely to cause us problems in the future                                   | While this dependency doesn't appear in a lot of places, it is related to an important piece of functionality | An hour or two is enough to master                         | Minimal code change to remove                        |
| 3      | This is pretty useful. It gives the user / developer something useful, and we should really consider it | This is a well-maintained project, but it is still growing and might require some effort if we need to upgrade versions | We use this dependency in quite a few places                                                                  | After writing a few components, you'll have the hang of it | This could take a sprint or two to remove            |
| 4      | This gives us a lot of benefits. I highly recommend it                                                  | This project will probably introduce breaking changes in the future                                                     | This dependency is a core part of a large portion of the app                                                  | This will take some time to master                         | Removing this is a large effort                      |
| 5      | This is essentially necessary                                                                           | There is a real chance this could be a problem in a couple of years                                                     | This thing is everywhere                                                                                      | You'll be using the documentation a lot                    | If you remove this you might as well rewrite the app |

#### Tech Stack

&nbsp;&nbsp;&nbsp;&nbsp;I've split up the technology I'm using into groups based on the part of the app they're in. Each link will take you to a short write up I've done on the tool.

### Front End

[React](https://jacksondr5.github.io/react)

[material-ui](https://jacksondr5.github.io/material)

[Redux](https://jacksondr5.github.io/redux)

[Smaller Tools](https://jacksondr5.github.io/viewSmall)

### Back End

[Node and Express](https://jacksondr5.github.io/nodeExpress)

[GraphQL](https://jacksondr5.github.io/graphql)

[Apollo Server](https://jacksondr5.github.io/apolloServer)

[Apollo Client](https://jacksondr5.github.io/apolloClient)

### Testing

[Jest and Enzyme](https://jacksondr5.github.io/testing)

# Setting Up an Environment (under development)
