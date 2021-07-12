# Misc

- https://1loc.dev/
- JS operator lookup: https://joshwcomeau.com/operator-lookup/
- [WTFJS](https://github.com/denysdovhan/wtfjs)
- [JS is weird](https://jsisweird.com/)
- [How to monitor function creation](https://nikgrozev.com/2019/04/07/reacts-usecallback-and-usememo-hooks-by-example/)

# Shadowing

I was wrong, shadowing doesn't have to do with whether we're using `var` or `const`/`let`. Shadowing will occur in both cases and it will result in [two problems](https://eslint.org/docs/rules/no-shadow#top)

> This can cause confusion while reading the code and it's impossible to access the global variable.

It's bad to make the global variable inaccessible, but it's not a big deal. In the end, if we will need to access the global variable (which is very rare but who knows), we will just have to rename the local variable.

And again, it's not as bad as causing confusion while reading the code. The fact that the reader will ask the question, "Is this the local variable being referenced here, or is it the global one?" is a mental burden that we can avoid by ensuring variable names uniqueness. This means that the following is the way to go, in addition to not have to add `/* eslint-disable no-shadow */` anymore.

```js
  const [key, setKey] = useState(0);
  useEffect(() => {
    setKey(k => k + 1);
  }, [dataLocale]);
```

# Purist

- http://blog.cleancoder.com/uncle-bob/2016/05/01/TypeWars.html

# Functional JS

- http://2ality.com/2017/11/currying-in-js.html
- https://github.com/getify/Functional-Light-JS
- https://medium.com/making-internets/why-using-chain-is-a-mistake-9bc1f80d51ba

# Numbers Encoding

- http://2ality.com/2012/04/number-encoding.html
- http://0.30000000000000004.com/
- https://docs.google.com/presentation/d/1apPbAiv_-mJF35P31IjaII8UA6TwSynCA_zhfDEmgOE/edit#slide=id.p
- https://en.wikipedia.org/wiki/IEEE_754

# Tools

Fake data generators

- https://github.com/rosiejs/rosie
- https://github.com/marak/Faker.js/
- https://github.com/boo1ean/casual
- https://github.com/chancejs/chancejs
- https://github.com/json-schema-faker/json-schema-faker
