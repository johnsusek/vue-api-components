## `<api>`

### Props
| Prop     | Type     | Required | Default | Details                                      |
| -------- | -------- | -------- | ------- | -------------------------------------------- |
| `url`    | `String` | `true`   |         | The URL to request                           |
| `name`   | `String` |          |         | Make request using this named api-config.    |
| `method` | `String` |          | `GET`   | HTTP method to use for request.              |
| `data`   | `Object` |          |         | Send this data as JSON in POST body.         |
| `params` | `Object` |          |         | Send this data as URL params in GET request. |

### Events
| Event      | Handler arguments | Details                                                                                                                            |
| ---------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `@start`   |                   | The request has started.                                                                                                           |
| `@end`     |                   | The request has ended.                                                                                                             |
| `@success` | _`responseBody`_  | The request has succeeded. First argument of handler will be body of response.                                                     |
| `@error`   | _`response`_      | The request has failed. First argument of handler will be [axios response object](https://github.com/axios/axios#response-schema). |


<br>

## `<api-config>`

| Prop    | Type   | Details                                                         |
| ------- | ------ | --------------------------------------------------------------- |
| `name`    | `String` | Specify a name for this API config. Used with \<api> name prop. |
| `baseUrl` | `String` | The base url to prepend to all request URLs.                    |
| `headers` | `Object` | Add these headers to all requests.                              |