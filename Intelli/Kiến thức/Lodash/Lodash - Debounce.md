Tags: #lodash #debounce

[Link document](https://lodash.com/docs/4.17.15#debounce)

# Introduce
<p>Creates a debounced function that delays invoking `func` until after `wait` milliseconds have elapsed since the last time the debounced function was invoked.</p>

# Example
JS:
```js
// Avoid costly calculations while the window size is in flux.

jQuery(window).on('resize', _.debounce(calculateLayout, 150));

// Invoke `sendMail` when clicked, debouncing subsequent calls.

jQuery(element).on('click', _.debounce(sendMail, 300, {

  'leading': true,

  'trailing': false

}));

// Ensure `batchLog` is invoked once after 1 second of debounced calls.

var debounced = _.debounce(batchLog, 250, { 'maxWait': 1000 });

var source = new EventSource('/stream');

jQuery(source).on('message', debounced);

// Cancel the trailing debounced invocation.

jQuery(window).on('popstate', debounced.cancel);
```

In Typescript: [Example](https://github.com/HarryWarre/Todo-Redux-Intelli/blob/master/src/components/form/filter-task.tsx)
```typescript
 const handleSearch = (event: React.ChangeEvent<HTMLInputElement>) => {
    dispatch(searchTerm(event.target.value));
  };

  const debounceSearch = _.debounce(handleSearch, 1000, { maxWait: 2000 });

  return (
    <Box display={"flex"} sx={{ my: 3 }}>
      <TextField
        onChange={debounceSearch}
        variant='outlined'
        placeholder='Search...'
        size='medium'
        style={{ marginRight: 1, width: "570px" }}
      />
    </Box>
  );
```

