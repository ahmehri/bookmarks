# Styling in React

Styling in React can be done using one of the following approaches.
* CSS methodologies.
* CSS processors.
* React based approaches.
* CSS Modules.

The first 2 approaches are for styling in general. When it's about React, other approaches, in addition to the first 2 approaches can be used too.
One important use case related to our code is how to avoid CSS naming conflicts between our microfrontends. We will answer this question in the following.

# CSS Methodologies and CSS Processors
Traditional CSS is not scalable and is error prone. New methodologies emerged;
* [BEM](http://getbem.com/).
* [OOCSS](http://oocss.org/).
* [SMACSS](https://smacss.com/).

For the moment, only BEM [has](https://github.com/marcohamersma/react-bem-helper) [integrations](https://github.com/morlay/react-bem-render) with React.

```
|                   | Pros                                              | Cons        |
|-------------------|---------------------------------------------------|-------------|
| CSS Methodologies | bring structure to project. help with maintenance | Complicated |
| CSS Processors    | Improve productivity. Parameterize styling.       |             |
```

CSS methodologies can be complicated, once adopted, you are stuck with it. They don't solve the issues but rather provide patches around them. CSS processors go deeper and solve the fundamental issues.
**It's not an either-or proposition**, you still can use both of them.

CSS spec is evloving and we can start using it today even though browsers are not compliant with it. In other words, we can start using tomorrow's CSS syntax, today thanks to [cssnext](http://cssnext.io/).

# React Based Approaches: Inline styles (CSS in JS)
All the approaches share the same principle, push styles to the component level. Which means putting the styles in the component.
![CSS classes written in React](https://gist.github.com/ahmehri/c814c5526256e66030288b45726d392a/raw/1d9b05b41ebb9b1912547ad1ec191d81f7738e9d/css-in-js.png)

Because styles live now in the JS world, all the following issues that we've been stuck with for so long in the CSS world disappeared:
![CSS issues solved](https://gist.github.com/ahmehri/c814c5526256e66030288b45726d392a/raw/729895a9ec4b94ec6c7187dcfcdfc45ffb134d7c/css-issues-solved.png)

For tools, there is a [lot](http://michelebertoli.github.io/css-in-js/).
**Recommendation**: [Radium](https://github.com/FormidableLabs/radium)

This is how React handles styling, and if we want to adopt this approach, we will need to do an important amount of refactoring (inline all styles and get rid of CSS files). A mindset shift is needed too because we're not used to write CSS in JS.

# CSS Modules
Why using [CSS Modules](https://github.com/css-modules/css-modules)? Modular and reusable CSS.
* No more conflicts.
* Explicit dependencies.
* No global scope.

A CSS Module is a CSS file in which all class names and animation names are scoped locally by default. When importing the CSS Module from a JS Module, it exports an object with all mappings from local names to global names. This is possible because CSS Modules compile to a low-level interchange format called ICSS or [Interoperable CSS](https://github.com/css-modules/icss), but are written like normal CSS files. This format is designed for loader implementers not end-users.

Webpack's [css-loader](https://github.com/webpack/css-loader) in module mode is an implementation of CSS Module. An example of this implementation can be found [here](https://github.com/css-modules/webpack-demo).

:thumbsup: CSS Processors such as Sass can still be used in front of CSS Modules to obtain more functionalities.

## react-css-modules
[react-css-modules](https://github.com/gajus/react-css-modules) is a helper for CSS Modules in React. It has the following pros:
![react-css-modules pros](https://gist.github.com/ahmehri/c814c5526256e66030288b45726d392a#file-react-css-modules-pros-png)

But the main con is that we should decorate all of our classes (decorators everywhere) which is kind of ugly:
```
import React from 'react';
import CSSModules from 'react-css-modules';
import styles from './table.css';

class Table extends React.Component {
    render () {
        return <div styleName='table'>
            <div styleName='row'>
                <div styleName='cell'>A0</div>
                <div styleName='cell'>B0</div>
            </div>
        </div>;
    }
}

export default CSSModules(Table, styles);
```

# Summary
CSS Modules is the way to go if we want to avoid CSS conflicts between microfrontends without the need to do an important refactoring, such as if we want to adopt CSS in JS approach.

# References
* https://survivejs.com/react/advanced-techniques/styling-react/
* CSS in JS
    * https://speakerdeck.com/vjeux/react-css-in-js
    * https://github.com/MicheleBertoli/css-in-js
    * https://speakerdeck.com/vjeux/react-css-in-js
* https://github.com/css-modules/css-modules
