# 1. Introduction to HTTP Status Codes

An HTTP status code is a three-digit number returned by a server as part of an HTTP response. It communicates the result or current status of the client's request.

For example:

    HTTP/1.1 200 OK

In this response:

- `200` is the HTTP status code.
- `OK` is the descriptive phrase.
- It communicates that the request was successful.

Status codes help clients understand how the server handled their requests.

# 2. The Five Categories of HTTP Status Codes

HTTP status codes are divided into five categories. Each category is identified by the first digit of the status code.

## 2.1 1xx — Informational Responses

Informational responses indicate that the server has received the request and is continuing to process it.

## 2.2 2xx — Successful Responses

Successful responses indicate that the client's request was successfully received, understood and processed.

Example:

    HTTP/1.1 200 OK

## 2.3 3xx — Redirection Responses

Redirection responses indicate that further action is needed to complete the request, commonly by following a different URL.

## 2.4 4xx — Client Error Responses

Client error responses indicate that there is a problem with the request made by the client.

The server cannot process the request as intended because of an issue such as invalid information, missing authentication or insufficient permissions.

Examples:

- `400 Bad Request` — The request contains invalid information.
- `401 Unauthorized` — Authentication is required or has failed.
- `403 Forbidden` — The client does not have permission to access the resource.
- `404 Not Found` — The requested resource cannot be found.

## 2.5 5xx — Server Error Responses

Server error responses indicate that the server has failed to fulfil an otherwise valid request.

The request may be valid, but the server is experiencing a problem while processing it.

Examples:

- `500 Internal Server Error` — The server encountered an unexpected internal problem.
- `503 Service Unavailable` — The server is temporarily unable to handle the request.

**Important distinction:**

- 4xx indicates a problem with the client's request.
- 5xx indicates a problem preventing the server from fulfilling the request.

**Key Takeaway:**

The first digit of an HTTP status code identifies its category and helps the client understand the general outcome of its request.

# 3. 200 OK

`200 OK` is a successful HTTP status code that indicates that the server successfully processed the request.

The exact meaning of `200 OK` depends on the HTTP method used.

## 3.1 200 OK with GET

Example:

    GET /api/products/25

Response:

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
      "productId": 25,
      "name": "Laptop",
      "price": 15000
    }

The `200 OK` status code communicates that the request was successfully processed.

The response body contains the information retrieved by the server and returned to the client.

## 3.2 200 OK with PUT

Example:

    PUT /api/students/10
    Content-Type: application/json

    {
      "name": "Precious",
      "course": "Cybersecurity"
    }

Response:

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
      "studentId": 10,
      "name": "Precious",
      "course": "Cybersecurity"
    }

The `200 OK` status code communicates that the update was successfully processed.

The response body may contain the updated representation of the resource.

**Important:**

- `200 OK` indicates successful processing.
- The response body may contain information returned by the server.
- The meaning of `200 OK` depends on the operation performed.

# 4. 201 Created

`201 Created` is a successful HTTP status code that indicates that a request successfully resulted in the creation of a new resource.

It is commonly returned when a client uses the POST method to create a resource.

## 4.1 201 Created with POST

Example:

    POST /api/students
    Content-Type: application/json

    {
      "name": "Lerato",
      "course": "Software Development"
    }

Response:

    HTTP/1.1 201 Created
    Content-Type: application/json

    {
      "studentId": 101,
      "name": "Lerato",
      "course": "Software Development"
    }

The `201 Created` status code communicates that the server successfully created a new student resource.

The response body may contain information about the newly created resource, including the unique identifier assigned by the server.

## 4.2 The Location Header

A server may include a `Location` header in a `201 Created` response.

Example:

    HTTP/1.1 201 Created
    Location: /api/students/101
    Content-Type: application/json

    {
      "studentId": 101,
      "name": "Lerato",
      "course": "Software Development"
    }

The `Location` header identifies the URL of the newly created resource.

**Important:**

- `201 Created` indicates that a new resource was successfully created.
- The server may return the newly created resource in the response body.
- The `Location` header may identify where the new resource can be accessed.

# 5. 204 No Content

`204 No Content` is a successful HTTP status code that indicates that the server successfully processed the request but has no response content to return.

It is commonly used when an operation is successful and the client does not need additional information in the response body.

## 5.1 204 No Content with DELETE

Example:

    DELETE /api/students/25

Response:

    HTTP/1.1 204 No Content

The response communicates that the deletion request was successfully processed.

The server does not return a response body because no additional content is being provided.

## 5.2 204 No Content with PUT

A server can also return `204 No Content` after successfully updating a resource.

Example:

    PUT /api/students/10
    Content-Type: application/json

    {
      "name": "Precious",
      "course": "Cybersecurity"
    }

Response:

    HTTP/1.1 204 No Content

The response communicates that the update was successful without returning the updated resource representation.

## 5.3 200 OK vs 204 No Content

| 200 OK | 204 No Content |
|---|---|
| Indicates successful processing. | Indicates successful processing. |
| May include a response body. | Does not include a response body. |
| Commonly returns requested or updated information. | Used when no response content needs to be returned. |

**Important:**

- `204 No Content` indicates a successful operation.
- It does not mean the server has no information.
- A 204 response must not contain response content.

# 6. 202 Accepted

The `202 Accepted` status code indicates that the server has accepted a request for processing, but the processing has not necessarily been completed.

It is commonly used for long-running operations that may take time to finish.

For example, when a client requests a large financial report, the server may accept the request and place it in a processing queue.

**Example response:**

    HTTP/1.1 202 Accepted
    Content-Type: application/json

    {
      "message": "Report generation has started.",
      "status": "Processing"
    }

The client may need to check the status of the operation later to determine whether it has completed successfully.

**Difference between 200 OK and 202 Accepted:**

- `200 OK`: The request has been successfully processed.
- `202 Accepted`: The request has been accepted for processing, but processing may still be incomplete.

**Important:** A `202 Accepted` response does not guarantee that the operation will eventually succeed. It only confirms that the server accepted the request for processing.

# 7. 3xx — Redirection Responses

The `3xx` category represents HTTP redirection responses. These status codes indicate that the client needs to take additional action to complete its request.

Redirection commonly occurs when a resource has moved to another URL.

For example, imagine a website changes the location of a page from:

    https://example.com/old-page

to:

    https://example.com/new-page

When the client requests the old URL, the server can return a redirection response containing the new URL.

**Example response:**

    HTTP/1.1 301 Moved Permanently
    Location: https://example.com/new-page

The `Location` header tells the client where the resource can now be found.

The client can then follow the new URL to access the resource.

**Important:** A redirection response does not necessarily mean that the request failed. It means the client needs to take another action, such as following a new URL.

# 8. 301 Moved Permanently

The `301 Moved Permanently` status code indicates that a resource has permanently moved to a new URL.

When a client requests the old URL, the server responds with a `301` status code and provides the new URL through the `Location` response header.

**Example:**

    GET /api/students/registration

**Server response:**

    HTTP/1.1 301 Moved Permanently
    Location: /api/registration/students

The client can then follow the new URL to access the resource.

**Important:** A `301` response indicates that the resource has permanently moved. Clients should use the new URL instead of continuing to rely on the old one.

# 9. 302 Found

The `302 Found` status code indicates that a resource is temporarily available at a different URL.

Unlike `301 Moved Permanently`, the original URL is still considered the resource's permanent location. The client is temporarily redirected to another URL.

**Example:**

A university temporarily moves its registration page while performing maintenance.

    GET /api/students/registration

**Server response:**

    HTTP/1.1 302 Found
    Location: /api/temporary-registration

The client can follow the new URL to access the temporary registration page.

Once maintenance is complete, the university can restore the original endpoint.

**Difference between 301 and 302:**

- `301 Moved Permanently`: The resource has permanently moved to another URL.
- `302 Found`: The resource is temporarily available at another URL.

**Important:** A `302` response does not mean that the original URL has been permanently replaced.

# 10. 4xx — Client Error Responses

The `4xx` category represents HTTP client error responses. These status codes indicate that there is a problem with the request sent by the client, which prevents the server from fulfilling it.

Client errors may occur when:

- The client sends invalid or incomplete information.
- The client provides incorrect authentication credentials.
- The client requests a resource that does not exist.
- The client does not have permission to access a resource.

**Example:**

A client requests a student record using an invalid student ID.

    GET /api/students/abc

The server expects a numeric student ID but receives `abc`.

**Server response:**

    HTTP/1.1 400 Bad Request
    Content-Type: application/json

    {
      "error": "Invalid student ID."
    }

The `400 Bad Request` status code indicates that the request contains invalid information.

**Important distinction:**

- `4xx`: The problem is related to the client's request or access.
- `5xx`: The server encounters a problem while trying to fulfil a request.

# 11. 400 Bad Request

The `400 Bad Request` status code indicates that the server cannot process a request because it contains invalid information or is incorrectly formatted.

This can happen when:

- Required information is missing.
- The client sends data in an invalid format.
- The request contains incorrect parameter values.
- The request body contains invalid JSON.

**Example:**

A client wants to register a new student but sends an invalid email address.

    POST /api/students
    Content-Type: application/json

    {
      "name": "Precious",
      "email": "precious-email"
    }

The server expects a properly formatted email address.

**Server response:**

    HTTP/1.1 400 Bad Request
    Content-Type: application/json

    {
      "error": "Invalid email address."
    }

The client must correct the information and submit the request again.

**Important:** A `400 Bad Request` indicates a problem with the request itself, not necessarily a problem with the server.

# 12. 401 Unauthorized

The `401 Unauthorized` status code indicates that the client's request does not contain valid authentication credentials.

Authentication is the process of verifying the identity of a user or application.

This error commonly occurs when:

- The client provides an incorrect password.
- The client does not provide authentication credentials.
- An authentication token is invalid or has expired.

**Example:**

A student wants to access their university results but provides an incorrect password.

**Server response:**

    HTTP/1.1 401 Unauthorized
    Content-Type: application/json

    {
      "error": "Invalid username or password."
    }

The client must provide valid authentication credentials before the server can authenticate the user.

**Important:** A `401 Unauthorized` response relates to authentication, not permission.

**Difference between 401 and 403:**

- `401 Unauthorized`: The client has not successfully authenticated.
- `403 Forbidden`: The client is authenticated but does not have permission to access the requested resource.

# 13. 403 Forbidden

The `403 Forbidden` status code indicates that the server understands the client's request but refuses to fulfil it because the client does not have the required permissions.

This commonly happens when:

- A student tries to access administrator-only features.
- An ordinary user tries to access restricted information.
- An authenticated user attempts an operation they are not allowed to perform.

**Example:**

A student successfully signs in to a university system but tries to access the administrator dashboard.

    GET /api/admin/dashboard
    Authorization: Bearer valid_student_token

**Server response:**

    HTTP/1.1 403 Forbidden
    Content-Type: application/json

    {
      "error": "You do not have permission to access this resource."
    }

The server recognises the student but refuses access because the student does not have administrator privileges.

**Important:** A `403 Forbidden` response does not necessarily mean that the client has failed to authenticate. The client may be successfully authenticated but lack the required authorization.

# 14. 404 Not Found

The `404 Not Found` status code indicates that the server cannot find the specific resource requested by the client.

This commonly happens when:

- The client requests a resource using an incorrect ID.
- The requested resource does not exist.
- The client uses an incorrect endpoint or URL.
- A resource has been deleted.

**Example:**

A client wants to retrieve information about a student with ID `150`, but no student with that ID exists.

    GET /api/students/150

**Server response:**

    HTTP/1.1 404 Not Found
    Content-Type: application/json

    {
      "error": "Student not found."
    }

The server cannot return the requested student information because the resource cannot be found.

**Important:** A `404 Not Found` response does not necessarily mean that the entire API or server is unavailable. It means the specific resource requested could not be found.

# 15. 405 Method Not Allowed

The `405 Method Not Allowed` status code indicates that the server recognises the requested resource, but the HTTP method used is not allowed for that resource.

For example:

- An API allows `GET` to retrieve product information.
- The API does not allow `PATCH` on that endpoint.
- A client sends a `PATCH` request to that endpoint.

**Example request:**

    PATCH /api/products/25

**Server response:**

    HTTP/1.1 405 Method Not Allowed
    Allow: GET
    Content-Type: application/json

    {
      "error": "PATCH method is not allowed for this resource."
    }

The `Allow` response header tells the client which HTTP methods are supported by the resource.

**Difference between 404 and 405:**

- `404 Not Found`: The requested resource cannot be found.
- `405 Method Not Allowed`: The resource exists, but the HTTP method used is not supported for it.

**Important:** The problem is the HTTP method used, not the existence of the resource.

# 16. 409 Conflict

The `409 Conflict` status code indicates that the client's request conflicts with the current state of a resource on the server.

This commonly happens when:

- A client tries to register an email address that is already in use.
- A client tries to create a resource that already exists.
- An update conflicts with a change made by another user.

**Example:**

A student tries to register an account using an email address that already belongs to another student.

    POST /api/students
    Content-Type: application/json

    {
      "name": "Precious",
      "email": "precious@example.com"
    }

**Server response:**

    HTTP/1.1 409 Conflict
    Content-Type: application/json

    {
      "error": "An account with this email address already exists."
    }

The server refuses to create the account because doing so would conflict with an existing resource.

**Difference between 400 and 409:**

- `400 Bad Request`: The request contains invalid or malformed information.
- `409 Conflict`: The request may be valid, but it conflicts with the current state of a resource.

**Important:** A `409 Conflict` response means the client may need to resolve the conflict before retrying the request.

## 17. 422 Unprocessable Content

The 422 Unprocessable Content status code indicates that the server understands the request and its format, but cannot process the instructions because the provided information fails validation or business rules.

For example, an API may require students to be at least 17 years old. If a client sends an age of 12, the request may be rejected with a 422 status code.

### Example

A valid JSON request:

{
    "age": 12
}

The value is an integer, but it does not satisfy the API's age requirement.

### Difference Between 400 and 422

- 400 Bad Request: The request contains invalid or malformed information, such as an incorrect data type.
- 422 Unprocessable Content: The request is correctly formatted, but its content violates a validation rule or business requirement.

## 18. 429 Too Many Requests

The 429 Too Many Requests status code indicates that a client has sent too many requests within a specified period.

APIs use rate limiting to control how frequently clients can make requests and to prevent excessive traffic from affecting server performance.

### Example

An API allows a user to make 100 requests per minute.

If the user sends 150 requests within one minute, the API may reject additional requests and return a 429 status code.

The response may include a `Retry-After` header indicating how long the client should wait before trying again.