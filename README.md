###New E-Commerce Admin Tool Technology Overview and Setup Guide
Here, I'll be going over the libraries and packages I'm currently using in the New E-Commerce Admin Tool (NEAT). I'm going to give a brief description of each, provide some links to resources so you can learn more, and tell you how to set up an environment to play around.

One thing I want to mention is that you’re going to see a large number of dependencies here. This might look like a lot of technical debt, but these tools are different than frameworks like .NET, Xamarin, or Angular. They’re usually pretty small. While .NET and Angular try to be frameworks that can do everything you could ever need to do, all of the dependencies here focus on doing one particular thing. In fact, the some of the developers that make these tools have stated that they intentionally limit the scope of their projects to keep things simple. This lets us carefully pick the stuff we need.

This is going to be a long web page, so for each dependency, I've included a summary table that rates the dependency on benefit, risk, prevalence in our code, effort to learn, and effort to remove. Here's a reference for that table.

| Rating | Benefit                                                                                                 | Risk                                                                                                                    | Prevalence in our Code                                                                                        | Effort to Learn                                              | Effort to Remove                                     |
| ------ | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ | ---------------------------------------------------- |
| 1      | We honestly could do without this. It’s a nicety                                                        | This is stable code with a large community and great backers                                                            | Occurs in very few places / Is completely separate from production code and tests                             | Almost no effort                                             | We can delete this on a whim, at any point in time   |
| 2      | There are tangible benefits, but it’s not completely necessary                                          | This is a well-maintained project that is unlikely to cause us problems in the future                                   | While this dependency doesn't appear in a lot of places, it is related to an important piece of functionality | An hour or two is enough to master                           | Minimal code change to remove                        |
| 3      | This is pretty useful. It gives the user / developer something useful, and we should really consider it | This is a well-maintained project, but it is still growing and might require some effort if we need to upgrade versions | We use this dependency in quite a few places                                                                  | After writing a few components, you'll have the hang of it   | This could take a sprint or two to remove            |
| 4      | This gives us a lot of benefits.                                                                        | I highly recommend it                                                                                                   | This project will probably introduce breaking changes in the future                                           | This dependency is a core part of a large portion of the app | This will take some time to master                   | Removing this is a large effort |
| 5      | This is essentially necessary                                                                           | There is a real chance this could be a problem in a couple of years                                                     | This thing is everywhere                                                                                      | You'll be using the documentation a lot                      | If you remove this you might as well rewrite the app |

###Tech Stack

##[React](https://reactjs.org/)
Rating | Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
------ | ------- | ---- | ---------------------- | --------------- | ---------------- |
5 | 2 | 4 | 3-4 | 4-5\*
_\*:Depending on what we replace React with, we may or may not have to do an entire rewrite._

React is the basis for our view layer. It allows us to code our apps in a declarative way, break our code down into components, and opens us up to pretty much every other dependency on the list. #**Benefits**

* For the user:
  * A consistent experience. By reusing components, we can ensure a consistent style throughout the app, making it easier to use.
  * More advanced features. By using React, we have the ability to easily pull in 3rd party components that have features that would ordinarily be time-consuming for us to make ourselves.
* For the Dev:
  * Components enable us to reuse code much easier than we could when our HTML was spread out in various HTML pages and JQuery calls. We can organize our project to better enable testing. Our files can be smaller and organized by purpose, instead of by language or MV\* pattern.
  * Access to an incredibly vibrant ecosystem of libraries, letting us easily bring in the advanced features shown in this document, and more.

#**Risk**: React is developed and maintained by Facebook. Facebook has said at their React Conference that they use thousands of components and have decided to not introduce breaking changes in future releases. There have been around 5.5 million downloads of React in the past month, showing how large the community around this project is.

#**Effort To Adopt**: This is a pretty big change from JQuery and WebForms, although I can’t speak to what it would be like for a developer coming from Angular/Knockout/Kentico. The React documentation is very good, however, and there’s a lot of it currently in our code. Out of the other big dependencies in this document (React, Redux, Apollo/GraphQL, Material-UI, Jest/Enzyme) I think this is the easiest to learn. Once it clicks, this becomes a really easy way to write web code.
