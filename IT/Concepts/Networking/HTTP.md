# Request

# Response

# Using URLs in HTTP
The `http://` at the beginning of a website URL specifies that the `http` protocol will be used for communication.

# Headers
An [HTTP header](https://developer.mozilla.org/en-US/docs/Glossary/HTTP_header) allows clients and servers to pass _additional_ information with each request or response. Headers are just case-insensitive [key-value pairs](https://en.wikipedia.org/wiki/Name%E2%80%93value_pair) that pass additional [metadata](https://en.wikipedia.org/wiki/Metadata) about the request or response.
HTTP requests from a web browser automatically carry with them many headers, including but not limited to:
- The type of client (e.g. Google Chrome)
- The Operating system (e.g. Windows)
- The preferred language (e.g. US English)
As developers, we can also define custom headers in each request.
## Why Are Headers Useful?

Headers are useful for several reasons from design to security, but most often headers are used for [metadata](https://en.wikipedia.org/wiki/Metadata) _about_ the request or response itself. 
For example, let's say we wanted to ask for a specific project from the Jello server. We need to send that project's ID to the server so it knows which project to send back the information for. That ID _is my request_, it's not information _about my request_. However, we might include headers in that request to pass along extra information - like _who_ is making the request.

[Authentication](https://auth0.com/intro-to-iam/what-is-authentication/) is a common use case for headers. If I ask Jello to complete a project, I need to provide authentication information that I'm logged in, but that auth info isn't the request itself, it's just _additional information_ about the request.

# Methods
HTTP defines a set of [methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods). We must choose one to use each time we make an HTTP request. The most common ones include:
- `GET`
- `POST`
- `PUT`
- `DELETE`
## Get
The [GET method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/GET) is used to "get" a _representation_ of a specified resource. It doesn't _take_ (remove) the data from the server but rather _gets_ a representation, or copy, of the resource in its current state. A GET request is considered a [_safe_](https://developer.mozilla.org/en-US/docs/Glossary/Safe/HTTP) method to call multiple times because it shouldn't alter the state of the server.
## Post
An [HTTP POST request](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/POST) _sends_ data to a server, typically to _create_ a new resource.
### Adding a Body
The `body` of the request is the _payload_ sent to the server. The special `Content-Type` header is used to tell the server the format of the body: `application/json` for JSON data in our case. `POST` requests are generally _not_ safe methods to call multiple times because that would create duplicate records. For example, you wouldn't want to accidentally send a tweet twice.

## Put
The HTTP [`PUT`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/PUT) method creates _or more commonly, updates_ the target resource with the contents of the request's `body`.
### POST vs. PUT
While `POST` and `PUT` are both used for creating resources, `PUT` is more common for updates and is [idempotent](https://developer.mozilla.org/en-US/docs/Glossary/Idempotent), meaning it's safe to make the same request multiple times without changing the server state more than once. For example:
```
POST /users/bob (create bob user)
POST /users/bob (create duplicate bob user)
POST /users/bob (create duplicate bob user)
```

```
PUT /users/bob (create bob user if it doesn't exist)
PUT /users/bob (update bob user with the same data)
PUT /users/bob (update bob user with the same data)
```
# Status Codes
The `Status Code` of an HTTP _response_ tells the client whether or not the server was able to fulfill the request. Status codes are 3-digit numbers that are grouped into categories:

- `100-199`: Informational responses. These are very rare.
- `200-299`: Successful responses. Hopefully, most responses are 200's!
- `300-399`: Redirection messages. These are typically invisible because the browser or HTTP client will automatically do the redirect.
- `400-499`: Client errors. You'll see these often, especially when trying to debug a client application
- `500-599`: Server errors. You'll see these sometimes, usually only if there is a bug on the server.

Here are some of the most common status codes, but there is also a [full list here](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) if you're interested.

- `200` - OK. This is by far the most common code, it just means that everything worked as expected.
- `201` - Created. This means that a resource was created successfully. Typically in response to a `POST` request.
- `301` - Moved permanently. This means the resource was moved to a new place, and the response will include where that new place is. Websites often use `301` redirects when they change their domain name, for example.
- `400` - Bad request. A general error indicating the client made a mistake in their request.
- `401` - Unauthorized. This means the client doesn't have the correct permissions. Maybe they didn't include a required authorization header, for example.
- `404` - Not found. You'll see this on websites quite often. It just means the resource doesn't exist.
- `500` - Internal server error. This means something went wrong on the server, likely a bug on their end.
