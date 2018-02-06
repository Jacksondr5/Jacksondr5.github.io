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
    ![Image of examining data in Redux DevTools](https://github.com/Jacksondr5/Jacksondr5.github.io/blob/master/imgs/reduxDevTools.jpg)
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

## [immutability-helper](https://www.npmjs.com/package/immutability-helper)

| Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
| ------- | ---- | ---------------------- | --------------- | ---------------- |
| 4       | 2    | 4                      | 3               | 4                |

Redux requires that all of our data be in a single object. While this brings a lot of conveniences from a single source of truth, this makes updating that data difficult. Splitting the reducers to handle various parts is one strategy, but immutability-helper helps us where splitting can be hard to do. This utility exports a function `update(oldState, commands) => newState`, which we can use to make safe state mutations.

**Benefits**

* For the Dev:
  * Here is an example of some data from the NEAT state. It is a complex object with nested objects and arrays:
  * ![Picture of an example state](https://github.com/Jacksondr5/Jacksondr5.github.io/blob/master/imgs/immutHelperExampleState.jpg)
    With regular JS, if we wanted to flip one of the settings(customer options), we would use this code to do it safely:

    ![Picture of mutating the state with regular JS](https://github.com/Jacksondr5/Jacksondr5.github.io/blob/master/imgs/immutHelperPlainUpdate.jpg)
    Here is the code with immutability-helper. It can parse the object we give it to find commands (denoted by $) to figure out what and how to update.

    ![Picture of mutating the state with immutability-helper](https://github.com/Jacksondr5/Jacksondr5.github.io/blob/master/imgs/immutHelperImmutUpdate.jpg)

**Risk**: This utility function helps us update the data in the app, which is a core piece of functionality. If we did have to remove this, it would be a large task. However, the source code for this dependency is only 260 lines. It is very simple, unlikely to change soon, and is a highly recommended way to manage immutability.

**Effort to Adopt**: The syntax is a bit strange, and the documentation is lacking some depth. It will take a little time to get used to.
