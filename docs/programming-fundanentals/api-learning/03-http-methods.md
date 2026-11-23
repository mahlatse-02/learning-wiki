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

# 2. POST — Creating Resources

The POST method is used to submit data to a server. It is commonly used to create new resources or perform operations that require submitted information.

For example, a student management application can use POST to register a new student.

## 2.1 Creating a Resource

Example:

    POST /api/students
    Content-Type: application/json

    {
      "name": "Precious",
      "course": "Software Development"
    }

The request asks the server to create a new student resource.

The API receives the request, validates the submitted information and creates the student record if the request is valid.

## 2.2 Understanding the 201 Created Response

When a new resource is successfully created, the server commonly returns the HTTP status code `201 Created`.

Example:

    HTTP/1.1 201 Created
    Content-Type: application/json

    {
      "studentId": 104,
      "name": "Precious",
      "course": "Software Development"
    }

The response confirms that a new student resource was created.

The server may assign a unique identifier to the resource so that it can be retrieved or managed in future requests.

## 2.3 POST and Idempotency

POST is generally not an idempotent HTTP method.

Idempotency means that repeating the same request produces the same intended effect as performing it once.

POST is generally not idempotent because repeating the same request can create additional resources or trigger additional operations.

For example, sending the same student registration request multiple times may create duplicate student records.

**Important:**

- GET is safe and idempotent.
- POST is generally not safe or idempotent.
- An API can implement safeguards, such as idempotency keys, to prevent duplicate operations.

## 2.4 POST and Request Bodies

POST commonly uses a request body to submit structured information to the server.

Example:

    POST /api/products
    Content-Type: application/json

    {
      "name": "Laptop",
      "price": 15000,
      "category": "Electronics",
      "inStock": true
    }

The request body contains the information that the API needs to process the request and potentially create the new product.

**Why use a request body?**

- It is suitable for submitting structured information.
- It can contain larger amounts of data than is practical to include in a URL.
- It supports data formats such as JSON.

Unlike query parameters, which are commonly used for filtering and controlling resource retrieval, request bodies are commonly used to submit resource data.

**Important:** Request bodies are not unlimited. Servers can impose request-size limits.

## 2.5 When to Use POST

POST is commonly used when a client needs to:

- Create a new resource, such as registering a student.
- Submit information for processing.
- Place an order in an online shopping application.
- Submit information that triggers an operation, such as a login request.

POST is not exclusively used for creating resources. Its exact behaviour depends on how the API endpoint is designed.

**Key Takeaway:**

POST allows a client to submit information to a server for processing. The server validates the information, performs the requested operation and returns an appropriate HTTP response.

# 3. PUT — Replacing Resources

The PUT method is used to create or replace the state of a resource at a specific URL.

It is commonly used to replace an existing resource with a new representation.

## 3.1 Replacing an Existing Resource

Example:

    PUT /api/students/25
    Content-Type: application/json

    {
      "name": "Thabo",
      "course": "Software Development",
      "email": "thabo.new@example.com"
    }

The request asks the server to replace the existing representation of the student identified by ID 25.

The request body generally contains the complete representation that the client wants the resource to have.

## 3.2 PUT and Idempotency

PUT is an idempotent HTTP method.

Idempotency means that repeating the same request produces the same intended effect as performing it once.

For example, sending the same PUT request multiple times with identical information will leave the resource in the same intended state.

**Important:**

Idempotency concerns the intended effect on the resource, not whether every response from the server is identical.

## 3.3 PUT vs POST

| POST | PUT |
|---|---|
| Commonly used to create resources. | Commonly used to replace resources. |
| Often targets a collection endpoint. | Often targets a specific resource endpoint. |
| Generally not idempotent. | Idempotent. |
| Repeating may create additional resources. | Repeating the same request produces the same intended resource state. |

Example:

    POST /api/students

Creates a new student in the students collection.

    PUT /api/students/10

Replaces the representation of the student identified by ID 10.

## 3.4 When to Use PUT

Use PUT when:

- You want to replace an existing resource.
- You can provide the complete representation of the resource.
- You want repeated identical requests to produce the same intended result.
- You want to create a resource at a specific URL, if the API supports that behaviour.

**Important distinction:**

- PUT replaces a resource's representation.
- PATCH partially modifies a resource.

**Key Takeaway:**

PUT allows a client to request the replacement of a resource's representation. It is idempotent because repeating the same request produces the same intended resource state.

# 4. PATCH — Partially Updating Resources

The PATCH method is used to apply partial modifications to an existing resource.

Unlike PUT, which generally sends the complete representation of a resource, PATCH allows the client to submit only the information that needs to change.

## 4.1 Understanding Partial Updates

Example:

    PATCH /api/students/10
    Content-Type: application/json

    {
      "email": "precious.new@example.com"
    }

The request asks the server to update only the email address of the student identified by ID 10.

The other student information, such as the name and course, remains unchanged.

## 4.2 PUT vs PATCH

| PUT | PATCH |
|---|---|
| Generally replaces the complete resource representation. | Applies partial modifications to a resource. |
| Generally requires the complete representation. | Sends only the information that needs to change. |
| Idempotent. | Can be idempotent or non-idempotent. |

Example of PUT:

    PUT /api/students/15

    {
      "name": "Tom",
      "course": "Cybersecurity",
      "email": "tom@example.com"
    }

Example of PATCH:

    PATCH /api/students/15

    {
      "course": "Cybersecurity"
    }

## 4.3 PATCH and Idempotency

PATCH is not guaranteed to be idempotent.

Whether a PATCH operation is idempotent depends on the operation being performed and how the API implements it.

An idempotent PATCH operation:

    PATCH /api/students/15

    {
      "course": "Cybersecurity"
    }

Repeating this request produces the same intended resource state because the course remains Cybersecurity.

A non-idempotent PATCH operation could increment a student's reward points by 10 every time the request is executed.

Repeating that operation would continue increasing the points.

**Important:**

- PUT is defined as idempotent.
- PATCH can be idempotent or non-idempotent.
- Idempotency concerns the intended effect of repeating a request.

## 4.4 When to Use PATCH

Use PATCH when:

- You want to update selected fields of an existing resource.
- You do not need to submit the complete resource representation.
- You want to avoid sending unnecessary information.
- You want to modify a resource without replacing its entire representation.

**Key Takeaway:**

PATCH allows a client to partially modify an existing resource by submitting only the information that needs to change.

# 5. DELETE — Removing Resources

The DELETE method is used when a client requests the removal of a resource from the server.

For example:

    DELETE /api/students/15

This request asks the server to delete the student identified by ID 15.

## 5.1 DELETE Responses

A successful DELETE request can return different HTTP status codes depending on how the server handles the deletion.

| Status Code | Meaning |
|---|---|
| `200 OK` | The resource was deleted, and the server returned a response. |
| `202 Accepted` | The deletion request was accepted but has not yet been completed. |
| `204 No Content` | The resource was deleted successfully, and there is no response body. |

## 5.2 DELETE and Idempotency

DELETE is an idempotent HTTP method.

Idempotency means that repeating the same request produces the same intended effect as performing it once.

For example:

    DELETE /api/students/25

The first request deletes the student resource.

Repeating the same request does not delete additional student resources or cause the student to be removed multiple times.

The intended result remains the same: the student resource no longer exists.

The server may return different status codes when the request is repeated. For example, it may return `204 No Content` initially and `404 Not Found` on a subsequent request if the resource is already gone.

This does not necessarily make DELETE non-idempotent because idempotency concerns the intended effect on the resource, not identical response codes.

## 5.3 When to Use DELETE

Use DELETE when:

- You want to remove a specific resource.
- You want to delete a record, such as a student or product.
- You want to request the removal of a resource identified by an endpoint.

Example:

    DELETE /api/products/10

This request asks the server to delete the product identified by ID 10.

**Key Takeaway:**

DELETE allows a client to request the removal of a resource from a server. It is idempotent because repeating the same request has the same intended effect on the resource.

# 6. Comparing the Five HTTP Methods

HTTP methods communicate the type of operation a client wants the server to perform on a resource.

Each method has a specific purpose.

| HTTP Method | Purpose | Idempotent? |
|---|---|---|
| GET | Retrieve information from the server. | Yes |
| POST | Submit information or create a resource. | Generally no |
| PUT | Replace the representation of a resource. | Yes |
| PATCH | Partially modify an existing resource. | Depends on the operation |
| DELETE | Request the removal of a resource. | Yes |

## 6.1 Understanding the Differences

### GET
Used when a client wants to retrieve information without intending to modify the server's resource state.

Example:

    GET /api/students/10

### POST
Used when a client wants to submit information to the server, commonly to create a new resource.

Example:

    POST /api/students

### PUT
Used when a client wants to replace the complete representation of an existing resource.

Example:

    PUT /api/students/10

### PATCH
Used when a client wants to modify only selected fields of an existing resource.

Example:

    PATCH /api/students/10

### DELETE
Used when a client wants to request the removal of a resource.

Example:

    DELETE /api/students/10

## 6.2 HTTP Methods and Resource-Oriented Endpoints

An API can use the same endpoint with different HTTP methods to perform different operations on the same resource.

For example:

    GET /api/students/10
    PUT /api/students/10
    PATCH /api/students/10
    DELETE /api/students/10

The endpoint identifies the resource, while the HTTP method communicates the operation the client wants to perform.

This approach makes API design more consistent and predictable.

## 6.3 Why Choosing the Correct HTTP Method Matters

Choosing the correct HTTP method is important because:

- It communicates the intended operation to the server.
- It helps maintain data integrity.
- It ensures requests are processed according to their purpose.
- It makes API behaviour more predictable.
- It helps prevent unintended resource modifications.

**Key Takeaway:**

HTTP methods define how clients interact with resources on a server. Choosing the correct method ensures that resources are retrieved, created, replaced, modified or removed appropriately.