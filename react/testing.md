- https://kentcdodds.com/blog/write-fewer-longer-tests

# Tools:
- [testing-library/react-testing-library](https://github.com/testing-library/react-testing-library)
- [testing-library/jest-dom](https://github.com/testing-library/jest-dom)
- [kentcdodds/react-testing-library-course](https://github.com/kentcdodds/react-testing-library-course)

---

(OUTDATED, TODO: update)

It's important to use all the tools marked in yellow in the following slide:
![](https://gist.github.com/ahmehri/3ee739bdb1bc17a8f16b732d1bc04b5a/raw/3cd237eac34f4ab46ce8d7b7b86a6261202ef460/test-pyramid.png)

# Sanpshot Testing
- Some interesting usages:
  - Test against breaking legacy code when doing refactoring (see https://twitter.com/nicoespeon/status/919602559966466048).
  - >[can](https://blog.progressly.com/what-makes-a-good-test-dff3df6058a2) act as a red flag if updating one component causes snapshots in other areas to fail.
- Snapshot testing is not TDD?
- Is snapshot testing bad and useless? No, but we should use it [correctly](https://blog.kentcdodds.com/effective-snapshot-testing-e0d1a2c28eca).
- Sanpshot test shallow rather than deep rendered content (using enzyme and enzyme-to-json). This will avoid having huge snapshots (one of the things to avoid when using snapshot testing).

# DOM Testing
- Use enzyme traversal utilities.

# Sanpshot VS DOM Testing
||Snapshot Testing|DOM Testing|
|---|---|---|
|Assertions|General|Specific|
|Affected by implementation details|Yes|No|

# Testing React with Enzyme
* Shallow rendering: unit tests.
* Full rendering: integration tests.

# Use Test Markers
> [Rule](https://blog.progressly.com/what-makes-a-good-test-dff3df6058a2) of thumb for assertions:

> Don’t couple the test to the implementation — use test markers (such as data-test="xyz") instead of targeting DOM nodes or CSS classes. The test shouldn't fail when someone adds a wrapper element or tweaks the class name. Note: If you don’t want to ship unused data-attributes to production, there are Babel plugins to remove properties from React components.

At the beginning, I wasn't convinced about this practice because I found that it adds complexity in addition to add code that is only used by the tests. I got convinced after reading this [article](https://blog.kentcdodds.com/making-your-ui-tests-resilient-to-change-d37a6ee37269). Those are useful even for E2E tests, it makes tests resilient to change and not brittle.

## Does Shipping Those Special Attributes To Production A Problem?
No, from the article:
> However, some folks have expressed to me concern about shipping these attributes to production. If that’s you, please really consider whether it’s actually a problem for you (because honestly it’s probably not as big a deal as you think it is). If you really want to, you can transpile those attributes away with babel-plugin-react-remove-properties.

# Async Code Testing
Use `expect.assertions(count)` to ensure that assertions have been called (it's so trivial that this doesn't happend in async code). Also returning a promise that resolves when testing errors will mark the test as succeeded when in reality [it's not](https://blog.progressly.com/what-makes-a-good-test-dff3df6058a2):
> If you are testing error handling behavior it is extra important to add the assertion count so that returning a resolved Promise does not make the test pass without running the .catch code and its assertions.

# What's Worth Testing
> [Here](https://medium.freecodecamp.org/the-right-way-to-test-react-components-548a4736ab22) are three rules of thumb I use to determine that something is not worth testing:

>1/ Will the test have to duplicate exactly the application code? This will make it brittle.

>2/ Will making assertions in the test duplicate any behavior that is already covered by (and the responsibility of) library code?

>3/ From an outsider’s perspective, is this detail important, or is it only an internal concern? Can the effect of this internal detail be described using only the component’s public API?

PropTypes are already covered by prop-types package -> don't test PropTypes

# How to Enforce Good Testing Practices?
By using [eslint-plugin-jest](https://github.com/jest-community/eslint-plugin-jest).

The [no-hooks](https://github.com/jest-community/eslint-plugin-jest/blob/master/docs/rules/no-hooks.md) rule is particularly interesting and convinced me that it's always better to avoid nesting when writing tests and to have a flat structure by avoiding setup and teardown hooks. Check [Further Reading](https://github.com/jest-community/eslint-plugin-jest/blob/master/docs/rules/no-hooks.md#further-reading) section for more details.

# Resources
- [Kent C. Dodds – Write tests. Not too many. Mostly integration.](https://www.youtube.com/watch?list=PLV5CVI1eNcJgNqzNwcs4UKrlJdhfDjshf&v=Fha2bVoC8SE)
