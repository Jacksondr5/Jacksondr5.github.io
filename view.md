#### View

_Here we will go over the technoligies I've used to make the view._

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
