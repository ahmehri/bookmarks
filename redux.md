- [Using redux devtools in Production](https://medium.com/@zalmoxis/using-redux-devtools-in-production-4c5b56c5600f).

# Action Creators, Reducers, Selectors
https://gist.github.com/ahmehri/d24952f13e99c63a6f3dfc39b48c73a5

# Don't Reduxify Everything
* [Move UI State Into The Component](https://dev.bleacherreport.com/3-things-i-learned-about-working-with-data-in-redux-5fa0d5f89c8b).
* https://github.com/reactjs/redux/issues/1287.
* https://redux.js.org/faq/organizing-state#organizing-state-only-redux-state.
* https://medium.com/@dan_abramov/you-might-not-need-redux-be46360cf367.
* https://medium.com/@adamrackis/finding-state-s-place-with-react-and-redux-e9a586630172.
* https://medium.com/@zackargyle/a-case-for-setstate-1f1c47cd3f73
* https://medium.com/react-ecosystem/how-to-handle-state-in-react-6f2d3cd73a0c.
* https://medium.freecodecamp.org/where-do-i-belong-a-guide-to-saving-react-component-data-in-state-store-static-and-this-c49b335e2a00
* http://jamesknelson.com/5-types-react-application-state/
* https://redux.js.org/faq/organizing-state#organizing-state-only-redux-state

## Forms
* https://github.com/jaredpalmer/formik#why-not-redux-form

# Normalization
* > [But](https://github.com/reactjs/redux/issues/1171#issuecomment-186580710) in redux the best practice is to build a fully normalized state and derieve your views' data through selectors.
* https://redux.js.org/faq/organizing-state#how-do-i-organize-nested-or-duplicate-data-in-my-state
* https://github.com/gaearon/flux-react-router-example#how-i-classify-stores

# Action Creators / Reducer Pairing
[ducks](https://github.com/erikras/ducks-modular-redux) is a pattern that advocates the pairing. It's not recommended by Dan Abramov:
> There's no such thing as reducer / action creator pairing in Redux. That's purely a Ducks thing. Some people like it but it obscures the fundamental strengths of Redux/Flux model: state mutations are decoupled from each other and from the code causing them.

> One part of the app might want to react to another part's actions because of complex product requirements, and we think this is fine. The coupling is minimal: all you depend on is a string and the action object shape. The benefit is it's easy to introduce new derivations of the actions in different parts of the app without creating tons of wiring with action creators. Your components stay ignorant of what exactly happens when an action is dispatched—this is decided on the reducer end.

## Pattern
> our official recommendation is that you should first try to have different reducers respond to the same actions. If it gets awkward, then sure, make separate action creators. But don't start with this approach.

> [By](https://github.com/reactjs/redux/issues/1171#issuecomment-167715393) the way message box is a good example of where I'd prefer to have a separate action creator for showing. Mostly because I'll want to pass a time when it was created so it can be dismissed automatically (and action creator is where you call impure Date.now()), because I want to set up a timer to dismiss it, I want to debounce that timer, etc. So I'd consider a message box the case where its "action flow" is important enough to warrant its personal actions. That said perhaps what I described can be solved more elegantly by https://github.com/yelouafi/redux-saga.

# Actions
> [I would](https://github.com/reactjs/redux/issues/1171#issuecomment-197044922) say that there is no semantic notion of Action Creators in Redux at all. There is a semantic notion of Actions (which describe what happened and are roughly equivalent to events but not quite—e.g. see discussion in #351). Action creators are just a pattern for organizing the code. It’s convenient to have factories for actions because you want to make sure that actions of the same type have consistent structure, have the same side effect before they are dispatched, etc. But from Redux point of view, action creators don’t exist—Redux only sees actions.

## Styles
**Best Practice**: Reactive style.
> Perhaps, it boils down to whether you program in imperative style or reactive style. Using ducks can cause actions and reducers to become highly-coupled, which encourages more imperative actions.
>* In imperative style, the store is given “what to do,” e.g. SHOW_MESSAGE_BOX or SHOW_ERROR
>* In reactive style, the store is given “a fact of what happened,” e.g. DATA_FETCHING_FAILED or USER_ENTERED_INVALID_THING_ID. The store reacts accordingly.

# Selectors
> We do recommend using selectors—in fact, we recommend exporting keeping functions that read from the state ("selectors") alongside reducers, and always using them in mapStateToProps instead of hardcoding state structure in the component. This way it's easy to change the internal state shape. You can (but don't have to) use reselect for performance, but you can also implement selectors naïvely like in the shopping-cart [example](https://github.com/rackt/redux/blob/891a97cd3e9a6c8ecea88087bfa3bec878f2ae0a/examples/shopping-cart/reducers/products.js#L52-L58).

# mapStateToProps / mapDispatchToProps
> [I recently](https://github.com/reactjs/redux/issues/1171#issuecomment-201047513) ran into an issue where nested objects were lost when Redux merges mapStateToProps and mapDispatchToProps (see reactjs/react-redux#324). Although @gaearon provides a solution that allows me to use nested objects, he goes on to say that this is an anti-pattern:

# Where to put state updating logic, in action creators or reducers?
Non-deterministic part in action creators and deterministic part in reducers.

> [I'm not](https://github.com/reactjs/redux/issues/1171#issuecomment-205756731) so sure putting most of your logic in action creators is a good idea. If all your reducers are just trivial functions accepting ADD_X-like actions, then they're unlikely to have errors - great! But then all your errors have been pushed to your action creators and you lose the great debugging experience that @dtinth alludes to.
But also like @tommikaikkonen mentioned, it's not so simple writing complex reducers. My gut feeling is that is where you would want to push if you wanted to reap the benefits of Redux though - otherwise instead of pushing side effects to the edge, you're pushing your pure functions to handle only the most trivial tasks, leaving most of your app in state-ridden hell. :)

> [@lumiasaki The advice](https://github.com/reactjs/redux/issues/1171#issuecomment-205865840) to keep your reducers simple while keeping complex logic in action creators goes against the recommended way to use Redux. Redux's recommended pattern is the opposite: keep action creators simple while keeping complex logic in reducers. Of course, you are free to put all your logic in action creators anyways, but in doing so you aren't followed the Redux paradigm, even if you are using Redux.

> [Expanding](https://github.com/reactjs/redux/issues/1171#issuecomment-205888533) on the previous points regarding business logic, I think you can separate your business logic into two parts:
non-deterministic part and deserministic part.
...
I try to put as much code into this deterministic land as possible, while keeping in mind that the reducer’s sole responsibility is to keep the application state consistent, given the incoming actions. Nothing more. Anything besides that, I would do it outside of Redux, because Redux is just a state container.

> [About](https://github.com/reactjs/redux/issues/1171#issuecomment-206043117) the only hard-and-fast rule I'd agree with is "non-determinism in action creators, pure determinism in reducers". That's a given.

# Side Effects
[redux-saga](https://github.com/redux-saga/redux-saga), Dan Abramov is a Backer.

> [@dtinth @denis-sokolov I agree](https://github.com/reactjs/redux/issues/1171#issuecomment-167585575) with you too on that. Btw when I was referencing the redux-saga project I maybe not made it clear that I'm against the idea of making the actionCreators grow and be more and more complex over time.

# References
* [This](https://github.com/reactjs/redux/issues/1171) discussion.
* [Dan Abramov and the react/redux team Recommendations](https://github.com/reactjs/redux/issues/1171#issuecomment-167704896).
* [Redux Styles](https://github.com/reactjs/redux/issues/1171).

# Tools

- [redux-devtools](https://github.com/reduxjs/redux-devtools).
- [redux-devtools-extension](https://github.com/zalmoxisus/redux-devtools-extension).
