#### [React](https://reactjs.org/)

| Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
| ------- | ---- | ---------------------- | --------------- | ---------------- |
| 5       | 2    | 4                      | 3-4             | 4-5\*            |

_\*:Depending on what we replace React with, we may or may not have to do an entire rewrite._

React is the basis for our view layer. It allows us to code our apps in a declarative way, break our code down into components, and opens us up to pretty much every other dependency on the list.

**Benefits**

* For the User:
  * A consistent experience. By reusing components, we can ensure a consistent style throughout the app, making it easier to use.
  * More advanced features. By using React, we have the ability to easily pull in 3rd party components that have features that would ordinarily be time-consuming for us to make ourselves.
* For the Dev:
  * Components enable us to reuse code much easier than we could when our HTML was spread out in various HTML pages and JQuery calls. We can organize our project to better enable testing. Our files can be smaller and organized by purpose, instead of by language or MV\* pattern.
  * Access to an incredibly vibrant ecosystem of libraries, letting us easily bring in the advanced features shown in this document, and more.

**Risk**: React is developed and maintained by Facebook. Facebook has said at their React Conference that they use thousands of components and have decided to not introduce breaking changes in future releases. There have been around 5.5 million downloads of React in the past month, showing how large the community around this project is.

**Effort To Adopt**: This is a pretty big change from JQuery and WebForms, although I can’t speak to what it would be like for a developer coming from Angular/Knockout/Kentico. The React documentation is very good, however, and there’s a lot of it currently in our code. Out of the other big dependencies in this document (React, Redux, Apollo/GraphQL, Material-UI, Jest/Enzyme) I think this is the easiest to learn. Once it clicks, this becomes a really easy way to write web code.
