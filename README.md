### New E-Commerce Admin Tool Technology Overview and Setup Guide

Here, I'll be going over the libraries and packages I'm currently using in the New E-Commerce Admin Tool (NEAT). I'm going to give a brief description of each, provide some links to resources so you can learn more, and tell you how to set up an environment to play around.

One thing I want to mention is that you’re going to see a large number of dependencies here. This might look like a lot of technical debt, but these tools are different than frameworks like .NET, Xamarin, or Angular. They’re usually pretty small. While .NET and Angular try to be frameworks that can do everything you could ever need to do, all of the dependencies here focus on doing one particular thing. In fact, the some of the developers that make these tools have stated that they intentionally limit the scope of their projects to keep things simple. This lets us carefully pick the stuff we need.

This is going to be a long web page, so for each dependency, I've included a summary table that rates the dependency on benefit, risk, prevalence in our code, effort to learn, and effort to remove. Here's a reference for that table.

| Rating | Benefit                                                                                                 | Risk                                                                                                                    | Prevalence in our Code                                                                                        | Effort to Learn                                            | Effort to Remove                                     |
| ------ | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------- |
| 1      | We honestly could do without this. It’s a nicety                                                        | This is stable code with a large community and great backers                                                            | Occurs in very few places / Is completely separate from production code and tests                             | Almost no effort                                           | We can delete this on a whim, at any point in time   |
| 2      | There are tangible benefits, but it’s not completely necessary                                          | This is a well-maintained project that is unlikely to cause us problems in the future                                   | While this dependency doesn't appear in a lot of places, it is related to an important piece of functionality | An hour or two is enough to master                         | Minimal code change to remove                        |
| 3      | This is pretty useful. It gives the user / developer something useful, and we should really consider it | This is a well-maintained project, but it is still growing and might require some effort if we need to upgrade versions | We use this dependency in quite a few places                                                                  | After writing a few components, you'll have the hang of it | This could take a sprint or two to remove            |
| 4      | This gives us a lot of benefits. I highly recommend it                                                  | This project will probably introduce breaking changes in the future                                                     | This dependency is a core part of a large portion of the app                                                  | This will take some time to master                         | Removing this is a large effort                      |
| 5      | This is essentially necessary                                                                           | There is a real chance this could be a problem in a couple of years                                                     | This thing is everywhere                                                                                      | You'll be using the documentation a lot                    | If you remove this you might as well rewrite the app |

### Tech Stack

## [React](https://reactjs.org/)

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

## [material-ui](https://material-ui-next.com/)

| Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
| ------- | ---- | ---------------------- | --------------- | ---------------- |
| 4-5\*   | 3    | 4                      | 4\*\*           | 4                |

*\*:Having a UI library is necessary, in my opinion. However, there are a lot of them, and Material-UI doesn’t have to be that one.*
_\*:Some parts of M-UI can be difficult to grasp, but the high effort mostly comes from how many components there are. You'll be referencing the docs a lot, but it's not particularly hard most of the time._

This is a UI component library we would use to make our app beautiful. There are tons of components that we can use, all of which follow Google’s Material Design philosophy. These UI elements are the building blocks of our view.

**Benefits**

* For the User:
  * A beautiful and consistent experience. All we have to do to give them a pretty button with a snazzy click animation is write `<Button raised />`.
  * Familiarity. Material Design is used on pretty much every Google product, and many other websites. By following those conventions, users can feel more at home in our app.
  * There’s a lot of functionality built in. Tables, collapsible UI, a flexbox implementation, selection tools, and much more.
* For the Dev:
  * Developers don’t have to spend time writing UI specific code. Most CSS is taken care of by the library, although it still lets us hook in and change stuff if we want to. There’s a lot of flexibility with design.
  * Lots of components. [Buttons](https://material-ui-next.com/demos/buttons/), [cards](https://material-ui-next.com/demos/cards/), [pickers](https://material-ui-next.com/demos/pickers/), several [progress indicators](https://material-ui-next.com/demos/progress/), [snackbars](https://material-ui-next.com/demos/snackbars/), [inputs](https://material-ui-next.com/demos/text-fields/), [menus](https://material-ui-next.com/demos/menus/), [modal dialogs](https://material-ui-next.com/demos/modals/), etc, etc. Check [the website](https://material-ui-next.com/getting-started/supported-components/) for a full list. (Note: Forcepoint seems to be blocking this at random. Opening the pages in Chrome Incognito helped, but I found this out after the site was unblocked for me only, so I can’t be sure if it will work for you.)

**Risk**: The project is still under active development, and they do introduce breaking changes in major versions. The community around it seems very vibrant, though, so I doubt it will die off anytime soon. There are a couple of corporate backers, and the main devs have been working for around 2 years now. This is one of our largest dependencies, it would take a great amount of effort to replace if we had to.

**Effort to Adopt**: The documentation site is pretty good, but still under development. The examples are extremely useful, though. They provide a lot of them, so you’ll be able to see a few different ways to use each component. The hardest parts for me to learn were the theme and grid elements, but for the most part, those aren’t something developers will work on much going forward. Once you set them up, they don’t require too much attention.

**Tightly Coupled Dependencies**

* [material-ui-icons](https://www.npmjs.com/package/material-ui-icons): This is a set of SVG icons in material style. They’re very convenient, but should be easy to replace if we have to.
* [mdi-material-ui](https://www.npmjs.com/package/mdi-material-ui): A 3rd party set of material-ui icons.
* [typeface-roboto](https://www.npmjs.com/package/typeface-roboto): A font.

## [prop-types](https://www.npmjs.com/package/prop-types)

| Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
| ------- | ---- | ---------------------- | --------------- | ---------------- |
| 4       | 1    | 1                      | 1               | 1                |

PropTypes checks the data types of any properties passed into a component. If the property is of the wrong type, shape, or missing altogether, an error will be thrown. This is **only active in development**.

**Benefits**

* For the Dev:
  * o PropTypes will immediately alert you if a component is rendered with incorrect/missing properties, making some bugs extremely obvious.
  * Since the PropTypes are spelled out in the source code, it acts as a sort of documentation. We can easily see what we can/should pass into a component. Below is an example.
    ![Image of ptop-types in NEAT Code](https://github.com/Jacksondr5/Jacksondr5.github.io/blob/master/imgs/propTypes.png)

**Risk**: The PropTypes code only runs in development, and is completely independent of any other code. We can delete this at any time.

**Effort to Adopt**: The syntax is a little funky, but there are few concepts to learn.

## [Redux](https://redux.js.org/)

| Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
| ------- | ---- | ---------------------- | --------------- | ---------------- |
| 4       | 2    | 4                      | 5               | 4                |

The goal of using this is to provide a single source of truth for the data on the client (not the server or DB) while also decoupling the view code from the logical code. There are more benefits to developers than to users, although a faster time to market is certainly a benefit to users. This dependency is more of a methodology than a library. There are very few APIs, and we write most of the code ourselves.

**Benefits**

* For the Dev:
  * State management is one of the most difficult parts of modern web development. The MVC model works well until you have a lot of interconnected data, and then handling how that data flows can become a problem. Redux helps solve this problem by providing a single store (basically a model) for your data. All the important data lives in this store and views subscribe to this store to get their data.
  * Redux also enforces a specific way of updating this data, through plain objects that describe the change. This way, all of the changes to the data are serializable and replay-able. We can use hot reloading to speed up development. If you’re working on a feature that’s behind several clicks and a search, the app will automatically navigate right back to where you were whenever it detects a change in the code files.
  * Lots of errors/bugs are caused by data being wrong or undefined. Before using Redux, I found myself using console.log() to track down pretty much every problem. I would have to trace the data through the app to figure out where it went wrong. Redux lets us use the Redux DevTools, which gives the developer an interactive tree of all the data. I have found it much easier to locate problems in my code when I can see all the data like this:
    ![Image of examining data in Redux DevTools](https://static.pexels.com/photos/20787/pexels-photo.jpg)
  * Both the single source of truth and explicit state changes make it possible for us to get a complete picture of what a user did when they used our app. We can build a bug reporting system in the app that sends us the user’s state history. With this, we don’t have to work with the user to try and reproduce the problem; we just replay the state history to find the problem. This can be automatic on error detection, or the user can send us a bug report with the history included.
  * The logic to update the source of truth is implemented in pure functions, which are very easy to test.
* For the User:
  * A single source of truth means we can save the state (minus sensitive information) to the browser’s local storage. This way, the user can reload the app exactly where they left off. Implementing this with Redux takes very little effort.
  * Certain actions can be “undone” very easily since we have a complete history of everything the user did. We can provide the user with a list of their actions, and let them select which ones they want to undo.

**Risk**: Redux is maintained by the React team, and it is very small (660 lines, many of those are comments). Because of its size and lack of heavy development over the past 1.5 years, I think that this library has matured and we won’t have to deal with many changes in the future. The ecosystem around Redux does continue to change and so any Redux-based dependencies can still change. The Redux-based code is how we would manage around 90% of the data in the client (not on the server or DB). If we suddenly had to abandon Redux this would be a large effort. However, the Redux code is loosely coupled with any other code (view code, data fetching code) so the work shouldn’t spread very far from the data processing code.

**Effort to Adopt**: Coding in a Redux way is different from the way most other web development is done. You have to learn to think about mutating data differently. This can take a little time. The hardest part for me was taking that theory and implementing it in real code. However, the NAT already has a lot of this real code in it, so I think it will take others less time to pick it up. Redux doesn’t have many APIs to learn, the effort is mostly in learning the process.

**Tightly Coupled Dependencies**

* [react-redux](https://www.npmjs.com/package/react-redux): This is a helper library that makes Redux work with React. Very lightweight.
* [redux-thunk](https://www.npmjs.com/package/redux-thunk): Makes it possible to do async work in the Redux workflow.
