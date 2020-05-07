**cache-and-network fetch policy**

This is an [important policy](https://www.apollographql.com/docs/react/api/react-hoc/#optionsfetchpolicy) that allows to retrieve the data from the cache first, and then issue a request to ensure that the cached data remains in sync with the server data. This is better than network-only policy, which doesn't use the cache at all.

In order to be able to use cache-and-network policy effeciently, the following pattern should be used instead.

```diff
const { loading, data } = useQuery();

-if(loading) {
+if(loading && !data) {
  return 'loading';
}

return <MyComponent/>;
```

This means that the loading indicator won't be displayed when there already cached data. The component will be rendered with the cached data first, then the request will be issued, in **background** and the new server data will be received, and the component will rerender with the new up to date data.
