# HTTP Methods

HTTP methods indicate the desired action to be performed on the identified resource. The below list is a summary of the most common HTTP methods:

- `GET`: Requests data from a specified resource.
  - The query string (name/value pairs) is sent in the URL of a GET request.
- `POST`: Submits data to be processed to a specified resource.
  - The query string (name/value pairs) is sent in the HTTP message body of a POST request.
- `PUT`: Updates a specified resource.
  - The query string (name/value pairs) is sent in the HTTP message body of a PUT request.
- `DELETE`: Deletes a specified resource.
  - The query string (name/value pairs) is sent in the URL of a DELETE request.

## Other HTTP Methods, mostly less in use

- `PATCH`: Applies partial modifications to a resource.
- `HEAD`: Asks for a response identical to that of a GET request but without the response body.
- `OPTIONS`: Represents a request for information about the communication options available on the request/response chain identified by the Request-URI.
- `CONNECT`: Establishes a tunnel to the server identified by the target resource.
- `TRACE`: Performs a message loop-back test along the path to the target resource.

For a complete list of HTTP methods, please refer to the [W3Schools](https://www.w3schools.com/tags/ref_httpmethods.asp).

## Data Transfer in HTTP Methods

- `GET`: Data is sent in the URL. (Path Variables, Query Parameters)
- `POST`: Data is sent in the body. (Request Body)
- `PUT`: Data is sent in the body. (Request Body)
- `DELETE`: Data is sent in the URL. (Path Variables, Query Parameters)

## Notes

- Body data is sent in JSON format.
- The body data is sent in the request body as a JSON object.

---

[🏠 Back to 25A-10221 Advanced Seminar in Mobile Development](../README.md)

© 2025 Afeka - Tel Aviv's College of Engineering