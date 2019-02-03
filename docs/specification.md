## Specification

### `<api>`

#### Props
| Prop       | Type     | Required | Default | Details                                                                                        |
| ---------- | -------- | -------- | ------- | ---------------------------------------------------------------------------------------------- |
|       |  | `true`   |         | The URL to request                                                                             |
| `name`     | `String` |          |         | Make request using this named api-config.                                                      |
| `method`   | `String` |          | `GET`   | HTTP method to use for request.                                                                |
| `data`     | `Object` |          |         | Send this data as JSON in POST body.                                                           |
| `params`   | `Object` |          |         | Send this data as URL params in GET request.                                                   |
| `filter`   | `String` |          |         | Apply this [JSONata](http://jsonata.org/) expression to the response data before returning it. |
| `mutation` | `String` |          |         | Commit this vuex mutation with the response data as the payload.                               |

<table>
  <tr>
    <td>Prop</td>
    <td>Type</td>
    <td>Required</td>
    <td>Default</td>
    <td>Details</td>
  </tr>
  <tr>
    <td><code>url</code></td>
    <td><code>String</code></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>

#### Events
| Event      | Handler arguments | Details                                                                                                                            |
| ---------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `@start`   |                   | The request has started.                                                                                                           |
| `@end`     |                   | The request has ended.                                                                                                             |
| `@success` | _`responseBody`_  | The request has succeeded. First argument of handler will be body of response.                                                     |
| `@error`   | _`response`_      | The request has failed. First argument of handler will be [axios response object](https://github.com/axios/axios#response-schema). |


<br>

### `<api-config>`

#### Props
| Prop      | Type     | Details                                                         |
| --------- | -------- | --------------------------------------------------------------- |
| `name`    | `String` | Specify a name for this API config. Used with \<api> name prop. |
| `baseUrl` | `String` | The base url to prepend to all request URLs.                    |
| `headers` | `Object` | Add these headers to all requests.                              |