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

Headers are useful for several reasons from design to security, but most often headers are used for [metadata](https://en.wikipedia.org/wiki/Metadata) _about_ the request or response itself. For example, let's say we wanted to ask for a specific project from the Jello server. We need to send that project's ID to the server so it knows which project to send back the information for. That ID _is my request_, it's not information _about my request_. However, we might include headers in that request to pass along extra information - like _who_ is making the request.

[Authentication](https://auth0.com/intro-to-iam/what-is-authentication/) is a common use case for headers. If I ask Jello to complete a project, I need to provide authentication information that I'm logged in, but that auth info isn't the request itself, it's just _additional information_ about the request.

# Methods