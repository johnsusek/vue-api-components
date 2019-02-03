# Specification

## \<api>

### Props
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
    <td align="center">*</td>
    <td></td>
    <td>The URL to request.</td>
  </tr>
  <tr>
    <td><code>name</code></td>
    <td><code>String</code></td>
    <td></td>
    <td></td>
    <td>Make request using this named api-config.</td>
  </tr>
  <tr>
    <td><code>method</code></td>
    <td><code>String</code></td>
    <td></td>
    <td><code>GET</code></td>
    <td>HTTP method to use for request.</td>
  </tr>
  <tr>
    <td><code>data</code></td>
    <td><code>Object</code></td>
    <td></td>
    <td></td>
    <td>Send this data as JSON in POST body.</td>
  </tr>
  <tr>
    <td><code>params</code></td>
    <td><code>Object</code></td>
    <td></td>
    <td></td>
    <td>Send this data as URL params in GET request.</td>
  </tr>
  <tr>
    <td><code>filter</code></td>
    <td><code>String</code></td>
    <td></td>
    <td></td>
    <td>Apply this <a href="http://jsonata.org/">JSONata</a> expression to the response data before returning it.</td>
  </tr>
  <tr>
    <td><code>mutation</code></td>
    <td><code>String</code></td>
    <td></td>
    <td></td>
    <td>Commit this vuex mutation with the response data as the payload.</td>
  </tr>
</table>

### Events
| Event      | Handler arguments | Details                                                                                                                            |
| ---------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| `@start`   |                   | The request has started.                                                                                                           |
| `@end`     |                   | The request has ended.                                                                                                             |
| `@success` | _`responseBody`_  | The request has succeeded. First argument of handler will be body of response.                                                     |
| `@error`   | _`response`_      | The request has failed. First argument of handler will be [axios response object](https://github.com/axios/axios#response-schema). |


<br>

## \<api-config>

### Props
| Prop      | Type     | Details                                                         |
| --------- | -------- | --------------------------------------------------------------- |
| `name`    | `String` | Specify a name for this API config. Used with \<api> name prop. |
| `baseUrl` | `String` | The base url to prepend to all request URLs.                    |
| `headers` | `Object` | Add these headers to all requests.                              |