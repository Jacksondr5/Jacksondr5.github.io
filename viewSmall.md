#### Smaller Front End Tools

## [prop-types](https://www.npmjs.com/package/prop-types)

| Benefit | Risk | Prevalence in our Code | Effort to Learn | Effort to Remove |
| ------- | ---- | ---------------------- | --------------- | ---------------- |
| 4       | 1    | 1                      | 1               | 1                |

PropTypes checks the data types of any properties passed into a component. If the property is of the wrong type, shape, or missing altogether, an error will be thrown. This is **only active in development**.

**Benefits**

* For the Dev:

  * PropTypes will immediately alert you if a component is rendered with incorrect/missing properties, making some bugs extremely obvious.
  * Since the PropTypes are spelled out in the source code, it acts as a sort of documentation. We can easily see what we can/should pass into a component. Below is an example.

    ![Image of ptop-types in NEAT Code](https://jacksondr5.github.io/imgs/propTypes.jpg)

**Risk**: The PropTypes code only runs in development, and is completely independent of any other code. We can delete this at any time.

**Effort to Adopt**: The syntax is a little funky, but there are few concepts to learn.
