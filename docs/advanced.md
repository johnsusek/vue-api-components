## Advanced usage

### Sequencing

Let's say you have a scenario where need to request data from two endpoints before you can call a third endpoint. Since the last endpoint requires data from the first two, you cannot call it right away. Here is how you would handle that with VAC.

```vue
<api url="/todos" @success="x => todos = x" />
<api url="/users" @success="x => users = x" />

<api
  v-if="users && todos"
  url="/thirdEndpoint"
  :params="{ user: users[1].id, todo: todos[3].id }" />
```

Now, `/thirdEndpoint` won't be called until `todos` and `users` is populated with data.

### Vuex

Add the propery `mutation` to `<api>` to commit the specified mutation with the response data as the payload.

```vue
<api url="/users" mutation="SET_USERS" />
```

Now, the mutation `SET_USERS` will be called on the store with the data returned from the API.