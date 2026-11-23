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