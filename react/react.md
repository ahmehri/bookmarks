- [React Components, Elements, and Instances](https://medium.com/@dan_abramov/react-components-elements-and-instances-90800811f8ca)
- [Typeching with PropTypes](https://reactjs.org/docs/typechecking-with-proptypes.html)
- [How to use Webpack’s new “magic comment” feature with React Universal Component + SSR](https://medium.com/faceyspacey/how-to-use-webpacks-new-magic-comment-feature-with-react-universal-component-ssr-a38fd3e296a)
- [Behind the Scenes: Improving the Repository Infrastructure](https://reactjs.org/blog/2017/12/15/improving-the-repository-infrastructure.html)
- [Controlled and uncontrolled form inputs in React don't have to be complicated](https://goshakkk.name/controlled-vs-uncontrolled-inputs-react/)
- https://github.com/acdlite/react-fiber-architecture
- https://github.com/typescript-cheatsheets/react-typescript-cheatsheet?utm_campaign=React%2BNewsletter&utm_medium=web&utm_source=React_Newsletter_216


**Performance**

- https://reactjs.org/docs/optimizing-performance.html
- https://calibreapp.com/blog/react-performance-profiling-optimization

**(Committing Changes) Warning: Lifecycle hook scheduled a cascading update**

What it means.

>It means what it says: you scheduled a cascading update. "Cascading" means an update inside an update. React first reconciles the tree by calling render, then commits DOM changes, then calls lifecycle hooks. If you call setState in componentDidMount, you are causing React to repeat the cycle: reconcile the tree, commit DOM changes, and call the hooks. This is wasteful.

Resources

- https://github.com/reduxjs/react-redux/issues/834

---

**Lifecycle**

- [Lifecycle diagram](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)

**Props Vs State**

- [Guide](https://github.com/uberVU/react-guide/blob/master/props-vs-state.md)
- https://lucybain.com/blog/2016/react-state-vs-pros/
- [Component state](https://reactjs.org/docs/faq-state.html#what-does-setstate-do)
- [React Anti-Patterns: Props in Initial State](https://medium.com/@justintulk/react-anti-patterns-props-in-initial-state-28687846cc2e)
- [Common pitfall in initialising state based on props in React JS](https://hackernoon.com/common-pitfall-in-initialising-state-based-on-props-in-react-js-d56795a944aa)

**Concurrent React**

- [sw-yx/fresh-concurrent-react](https://github.com/sw-yx/fresh-concurrent-react)

**List items keys**

- [Why you need keys for collections in React](https://paulgray.net/keys-in-react/)
- [Index as a key is an anti-pattern](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318)

**setState**

- [RFClarification: why is `setState` asynchronous?](https://github.com/facebook/react/issues/11527)
- [Does React keep the order for state updates?](https://stackoverflow.com/questions/48563650/does-react-keep-the-order-for-state-updates/48610973)
- [Using a function in `setState` instead of an object](https://medium.com/@wisecobbler/using-a-function-in-setstate-instead-of-an-object-1f5cfd6e55d1)
- https://twitter.com/kentcdodds/status/939245496056422401

**Style**

- [Why are underscore prefixes for internal methods of a React component considered bad?](https://github.com/airbnb/javascript/issues/1024)
- [Underscore prefixes for "private" properties](https://github.com/airbnb/javascript/issues/490)

**Tools**

- [teambit/bit](https://github.com/teambit/bit)
- Creating CLIs using React: https://github.com/vadimdemedes/ink
- [facebook/react-devtools](https://github.com/facebook/react-devtools)
