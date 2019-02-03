## Usage

## Getting data

### On creation

The simplest invocation will just GET the URL provided when the component is created.

```vue
<api url="http://api.example.com/users" />
```

### On interaction

This example loads the endpoint only once the button is clicked.

```vue
<api url="/users">
  <button slot-scope="api" @click="api.action">
</api>
```



<br>

Add a `@success` handler to access the data that was retrieved.

```vue
<api url="http://api.example.com/users" @success="x => users = x" />
Data from API is: {% raw %}{{ users }}{% endraw %}
```

<br>

Add an `@error` handler to access the error response.

```vue
<api url="http://api.example.com/users" @error="x => response = x" />
Error from API is: {% raw %}{{ response }}{% endraw %}
```

You don't want to specify the full url for each request, so you can configure VAC first.

```vue
<api-config base-url="https://api.example.com" />
<api url="/users" />
```

<br>

Often API communication will need a token passed in the headers to authenticate.

```vue
<api-config :headers="{ 'X-API-TOKEN': 'mySecretToken' }" />
<api url="http://api.example.com/users" />
```

<br>

### Sending data

To send data to an endpoint, add `method` and `data` props.

```vue
<api url="/users" method="post" :data="{ username: 'JaneDoe' }">
  <button slot-scope="api" @click="api.action">
</api>
```
