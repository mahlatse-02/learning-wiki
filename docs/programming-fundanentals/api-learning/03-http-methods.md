# 1. GET — Retrieving Resources

The GET method is an HTTP method used by a client to request information from a server.

It allows applications to retrieve resources without intending to modify the server's resource state.

## 1.1 Retrieving a Collection of Resources

A GET request can retrieve an entire collection of resources.

Example:

    GET /api/students

This request asks the server to return the collection of student records.

## 1.2 Retrieving a Specific Resource

GET can also retrieve one specific resource using its unique identifier.

Example:

    GET /api/students/2

This request asks the server to return the student whose ID is 2.

**Important distinction:**

- `/api/students` retrieves a collection of students.
- `/api/students/2` retrieves one specific student.

## 1.3 GET and Query Parameters

Query parameters provide additional instructions that help the server filter, sort or limit the resources being retrieved.

They are added to the endpoint using a question mark (`?`).

Example:

    GET /api/students?course=software-development&limit=10

Breaking down the request:

- `course` is a query parameter.
- `software-development` is its value.
- `limit` is another query parameter.
- `10` is its value.

The request asks the server to retrieve students enrolled in Software Development and return a maximum of 10 results.

The ampersand (`&`) separates multiple query parameters.

**Important distinction:**

- Path parameters identify a particular resource, such as `/api/students/25`.
- Query parameters provide additional instructions for retrieving resources, such as `?course=software-development`.

## 1.4 GET, Safety and Idempotency

GET is both a safe and an idempotent HTTP method.

### Safe Method

A safe method is intended to retrieve information without modifying the server's resource state.

For example:

    GET /api/students/25

This request retrieves student information without changing the student's record.

### Idempotent Method

An idempotent method produces the same intended effect when repeated multiple times as when performed once.

For example, sending:

    GET /api/students/25

five times does not create five student records or introduce additional changes.

**Important distinction:**

- Safe means the request is not intended to modify server resources.
- Idempotent means repeating the request has the same intended effect as performing it once.

GET is both safe and idempotent.