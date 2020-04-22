**How to avoid hoisting when requiring a module**

It's not hoisting but caching, and this is a feature of Node.js that cannot be avoided. It's not even related to import/export or babel.

```js
// file.js
console.log("I am being imported");

// factory.js
module.exports = () => {
  require("./file");
};

// index.js
const factory = require("./factory");

factory();
factory();

// result: 1 single log instead of 2
I am being imported
```

> Caching
>
>Modules are cached after the first time they are loaded. This means (among other things) that every call to require('foo') will get exactly the same object returned, if it would resolve to the same file.
>
>Provided require.cache is not modified, multiple calls to require('foo') will not cause the module code to be executed multiple times. This is an important feature. With it, "partially done" objects can be returned, thus allowing transitive dependencies to be loaded even when they would cause cycles.
>
>To have a module execute code multiple times, export a function, and call that function.

As mentioned, the solution is to export a function and call it.

```js
// file.js
module.exports = () => { console.log("I am being imported"); }

// factory.js
module.exports = () => {
  require("./file")();
};

// index.js
const factory = require("./factory");

factory();
factory();

// result: 2 logs
I am being imported
I am being imported
```

Resources:

- https://nodejs.org/api/modules.html#modules_caching

**Terminal**

- https://github.com/SamVerschueren/listr

**Tools**

- [remy/nodemon](https://github.com/remy/nodemon)
- [isaacs/rimraf](https://github.com/isaacs/rimraf)
- [node-inspector/node-inspector](https://github.com/node-inspector/node-inspector)
- [npm/node-semver](https://github.com/npm/node-semver)
- [paulmillr/chokidar](https://github.com/paulmillr/chokidar)
- [senchalabs/connect](https://github.com/senchalabs/connect)
- [chimurai/http-proxy-middleware](https://github.com/chimurai/http-proxy-middleware)
- [nodejitsu/node-http-proxy](https://github.com/nodejitsu/node-http-proxy)
- [kentcdodds/cross-env](https://github.com/kentcdodds/cross-env)
- [sass/node-sass](https://github.com/sass/node-sass)
- [socketio/socket.io](https://github.com/socketio/socket.io/)
- [senecajs/seneca](https://github.com/senecajs/seneca)
- [LoopBack](https://loopback.io/)
- [jasongin/nvs](https://github.com/jasongin/nvs)
- [anodynos/upath](https://github.com/anodynos/upath)
- [Automattic/mongoose](https://github.com/Automattic/mongoose)
- [zeit/pkg](https://github.com/zeit/pkg)
- [jakutis/require-text](https://github.com/jakutis/require-text)
- [sindresorhus/meow](https://github.com/sindresorhus/meow)
- [nodemailer/nodemailer](https://github.com/nodemailer/nodemailer)
- [jprichardson/node-fs-extra](https://github.com/jprichardson/node-fs-extra)
- [isaacs/node-graceful-fs](https://github.com/isaacs/node-graceful-fs)
- https://github.com/mikeal/watch

Version manager

- https://github.com/nvm-sh/nvm/blob/master/README.md
- https://github.com/tj/n
- https://github.com/Schniz/fnm
