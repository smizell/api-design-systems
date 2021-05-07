# Standard Identifiers

These are identifiers to use to match conditions on `when` and refer to as a `subject`. See the [specification](specification.md) on how and where to use these identifiers.

A Standard Identifier is an array of strings that reference a standard or part of a standard.

## HTTP

* `[http, transaction]` - generally refers to a transaction where there is a request and a response

### Request

Used for defining requirements around HTTP responses.

* `[http, request, method]` - generally refers to HTTP methods
* `[http, request, method, METHOD_NAME]` - refers to specific HTTP methods

    **Variables**

    * `METHOD_NAME` - valid HTTP method

* `[http, request, header]` - generally refers to HTTP request headers
* `[http, request, header, HEADER_NAME]` - refers to specific HTTP request headers

    **Variables**

    * `HEADER_NAME` - valid HTTP header

* `[http, request, body]` - generally refers to the HTTP response body

### Response

Used for defining requirements around HTTP responses.

* `[http, response, header, HEADER_NAME]` - refers to a specific HTTP response header

    **Variables**

    * `HEADER_NAME` - valid HTTP header

* `[http, response, status_code]` - generally refers to the HTTP status code
* `[http, response, status_code, STATUS_CODE]` - refers to a specific HTTP status code

    **Variables**

    * `STATUS_CODE`

        **Values**

        * `success` - any 2xx HTTP status code
        * `redirect` - any 3xx HTTP status code
        * `client_error` - any 4xx HTTP status code
        * `server_error` - any 5xx HTTP status code
        * Valid HTTP status code - refer to HTTP specification for valid HTTP status codes

* `[http, response, body]` - generally refers to the HTTP response body

### Message

A `message` is a way to reference either a request or response. Instead of writing two different requirements around a request or response header, you can use this to write one.

* `[http, message, header, HEADER_NAME]` - refers to a specific HTTP message header
* `[http, message, body]`