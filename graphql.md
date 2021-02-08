# GraphQL

- [A new approach to mocking GraphQL data](https://www.freecodecamp.org/news/a-new-approach-to-mocking-graphql-data-1ef49de3d491/)
- https://blog.apollographql.com/explaining-graphql-connections-c48b7c3d6976
- [Batching Client GraphQL Queries](https://www.apollographql.com/blog/batching-client-graphql-queries-a685f5bcd41b/)

### Compiling(Preprocessing) Queries

The need for compilation comes to [avoid runtime overhead](https://www.apollographql.com/docs/react/recipes/babel/) caused by colocating the queries in js files. This is not an issue when the files are kept in separate `.graphql` or `.gql` files, but keep in mind that you still need to preprocess them either by using:

- webpack `graphql-tag` [loader](https://github.com/apollographql/graphql-tag#webpack-preprocessing-with-graphql-tagloader)
- babel plugin [babel-plugin-graphql-tag](https://github.com/gajus/babel-plugin-graphql-tag), which uses `graphql-tag` under the hood.

In case you're colocating the queries in js files, then you need to use either bable plugin or macro to do the compilation. The plugin is [babel-plugin-graphql-tag](https://github.com/gajus/babel-plugin-graphql-tag) and there are two macros:

- [graphql-tag.macro](https://github.com/leoasis/graphql-tag.macro) as documented in apollo recipe.
- [graphql.macro](https://github.com/evenchange4/graphql.macro) as documented in cra [guide](https://facebook.github.io/create-react-app/docs/loading-graphql-files).

Using a macro is prefered because it requires less configuration and is more explicit as explained [here](https://www.apollographql.com/docs/react/recipes/babel/#using-graphql-tagmacro).

## Tools

- [Public GraphQL APIs](http://apis.guru/graphql-apis/)
- [apollographql/graphql-tag](https://github.com/apollographql/graphql-tag)
- [prisma/get-graphql-schema](https://github.com/prisma/get-graphql-schema)
- [graphql-compose/graphql-compose](https://github.com/graphql-compose/graphql-compose)
- [TypeGraphQL](https://typegraphql.ml/)
- [zalando-incubator/graphql-jit](https://github.com/zalando-incubator/graphql-jit)
- [GraphQL Field Finder](https://gist.github.com/stubailo/7a2071c4e568a185726c583073695bc0)
- [apollographql/graphql-tools](https://github.com/apollographql/graphql-tools)
- [APIs-guru/graphql-faker](https://github.com/APIs-guru/graphql-faker)
- [GraphQL Network chrome extension](https://chrome.google.com/webstore/detail/graphql-network/igbmhmnkobkjalekgiehijefpkdemocm/related?hl=en-GB)
- https://github.com/stylesuxx/graphql-custom-types
- [graphql-inspector](https://chrome.google.com/webstore/detail/graphql-inspector/jdkgbhpcefadmffbaamaipfhpecbedao) chrome extension

### Engines

- [prisma/prisma](https://github.com/prisma/prisma)
- [Hasura](https://hasura.io/)


## Resources

- [graphql/graphql-spec](https://github.com/graphql/graphql-spec)
- [Principled GraphQL](https://principledgraphql.com/)
- [GraphQL Foundation](https://gql.foundation/)
- [GraphQL Mastery](https://medium.com/graphql-mastery)
- [GraphQL cheatsheet](https://devhints.io/graphql#schema)
- [How to GraphQL](https://www.howtographql.com/)
- [chentsulin/awesome-graphql](https://github.com/chentsulin/awesome-graphql)

# Apollo GraphQL

## Use Cases

- [How to invalidate cached data in Apollo and handle updating paginated queries](https://medium.com/@martinseanhunt/how-to-invalidate-cached-data-in-apollo-and-handle-updating-paginated-queries-379e4b9e4698)
- [👩🏻‍🍳 Render Props, Apollo and Formik: build and compose forms in React with ease 🏄🏾‍](https://techblog.commercetools.com/render-props-apollo-and-formik-build-and-compose-forms-in-react-with-ease-f79a594be239)

SDL First:

- [apollo-server](https://www.apollographql.com/docs/apollo-server/)

Code First:

- [prisma/nexus](https://github.com/prisma/nexus)
