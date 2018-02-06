####[Jest](https://facebook.github.io/jest/) and [Enzyme](http://airbnb.io/enzyme/)

_**Important:** I'm still working on learning and implementing this into the NEAT, so some of the content on this page may change with time. As I learn more about how to test various parts of the application, the role of Jest and Enzyme can change._

| Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
| ------- | ---- | ---------------------- | --------------- | ---------------- |
| 5       | 3    | 4                      | 3-4\*           | 4                |

\*:I'm still learning this myself, so right now, I'm not exactly sure

**Benefits**

* For the Dev and BA:
  * Jest is an automated testing framework that lets us make automated tests for React apps. Using Jest, we can write unit, integration, and ui tests which can run on the developer's box as they work, in Release Management as a build step, or on demand as the BAs want.
  * Jest comes with a tool for building code coverage reports which can help us track down places where our code is not being tested. This is not going to find every test case for us, but can really help us out.
    ![Picure of code coverage report](https://github.com/Jacksondr5/Jacksondr5.github.io/blob/master/imgs/jestCodeCoverage.jpg)
  * Jest gives us the ability to create [snapshot tests](https://facebook.github.io/jest/docs/en/snapshot-testing.html) which can serialize our UI and save it to ensure that when we make changes we can see how the UI is rendered differently. Snapshot testing can be used on any serializable value, meaning it can be used in nearly every unit test. I'm still exploring the uses of snapshot testing, and determining where we should use this. The downside of snapshot tests are that it makes TDD harder, and there is room for tests that generate false positives. It's important that we use these carefully.
  * Enzyme gives us ways to shallow render our UI tests, traverse the node tree, and simulate certain user events. I'm still in the early stages of exploring this, but the features sound extremely useful.

**Risk:** The project is still under active development and we can probably expect some breaking changes on major version upgrades. Facebook says they’re using it heavily in their development process, so I think that the risk of the project dying off is low.

**Effort to Adopt:** Snapshot tests are very simple to learn, and the code overall is very easy to understand. I’m still working on it myself, but it doesn’t seem very hard so far.
