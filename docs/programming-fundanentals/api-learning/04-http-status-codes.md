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