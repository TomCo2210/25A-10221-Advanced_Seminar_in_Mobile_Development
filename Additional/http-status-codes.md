# HTTP response status codes

HTTP response status codes indicate whether a specific HTTP request has been successfully completed. Responses are grouped in five classes:

- Informational responses (100–199)
- Successful responses (200–299)
- Redirects (300–399)
- Client errors (400–499)
- and Server errors (500–599)

The below list is a summary of the most common HTTP status codes:

- 200 OK
  - The request succeeded. The result and meaning  of "success" depends on the HTTP method:
    - GET: The resource has been fetched and transmitted in the message body.
    - PUT or POST: The resource describing the result of the action is transmitted in the message body.
- 201 Created
  - The request has been fulfilled, resulting in the creation of a new resource.
- 204 No Content
  - The server successfully processed the request and is not returning any content.
- 400 Bad Request
  - The server cannot or will not process the request due to an apparent client error.
- 401 Unauthorized
  - Similar to 403 Forbidden, but specifically for use when authentication is required and has failed or has not yet been provided.
- 403 Forbidden
  - The request was valid, but the server is refusing action. The user might not have the necessary permissions for a resource.
- 404 Not Found
  - The requested resource could not be found but may be available in the future.
- 405 Method Not Allowed
  - A request method is not supported for the requested resource.
- 500 Internal Server Error
  - A generic error message, given when an unexpected condition was encountered and no more specific message is suitable.
- 501 Not Implemented
  - The server either does not recognize the request method or it lacks the ability to fulfill the request.
- 503 Service Unavailable
  - The server is not ready to handle the request. Common causes are a server that is down for maintenance or that is overloaded.

For a complete list of HTTP status codes, please refer to the [Mozilla Developer Network](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status).

---

[🏠 Back to 25A-10221 Advanced Seminar in Mobile Development](../README.md)

© 2025 Afeka - Tel Aviv's College of Engineering
