# Introduction to Express.js

## 2. The Relationship Between JavaScript, Node.js and Express.js

These three technologies work together when building an API.

### JavaScript

JavaScript is the programming language used to write the application logic of an API.

### Node.js

Node.js is a JavaScript runtime environment that allows JavaScript to execute outside a web browser. It enables developers to use JavaScript to build server-side applications.

### Express.js

Express.js is a web framework that runs on Node.js. It provides tools and features that simplify the process of building web servers and APIs.

### How They Work Together

- JavaScript is the language used to write the code.
- Node.js provides the environment in which the JavaScript code runs.
- Express.js provides additional tools for building and managing servers and API functionality.

Express.js depends on Node.js to run. It does not replace Node.js but builds on the capabilities that Node.js provides.

## 3. Why Use Express.js Instead of Node.js Alone?

Node.js provides built-in modules that allow developers to create servers and handle HTTP requests. However, developers must manually manage many aspects of request handling and routing when using Node.js alone.

Express.js simplifies these processes by providing tools and features that make building APIs easier.

### Advantages of Express.js

- **Simplified request handling:** Express.js makes it easier to handle incoming HTTP requests.
- **Easier routing:** Developers can define routes using HTTP methods and URL paths without manually inspecting every request.
- **Simplified response handling:** Express.js provides convenient methods for sending responses to clients.
- **Middleware support:** Developers can use middleware to perform tasks such as processing incoming data, authentication and logging.

Express.js reduces the amount of repetitive code developers need to write, making server-side development more manageable.

## 4. Understanding an Express Server

An Express server is an application built using Express.js that receives HTTP requests from clients, processes them and sends HTTP responses.

Express.js helps developers implement the request-response cycle.

### Example

A client sends the following request:

```http
GET /api/students
```

The Express server:

1. Receives the HTTP request.
2. Identifies the requested endpoint and HTTP method.
3. Processes the request.
4. Sends an HTTP response back to the client.

This allows the client and server to communicate through HTTP using the request-response cycle.

## 5. Understanding Routes in Express.js

A route in Express.js determines how the server responds to a particular HTTP method and URL path.

Routes allow the server to identify which application logic should be executed when a client sends a request.

### Components of a Route

A route consists of:

- **HTTP method:** Identifies the operation the client wants to perform, such as GET or POST.
- **URL path:** Identifies the resource or endpoint the client wants to access.

### Examples

| HTTP method | URL path | Purpose |
|---|---|---|
| GET | `/api/students` | Retrieve students |
| POST | `/api/students` | Create a student |
| GET | `/api/students/5` | Retrieve a student with ID 5 |

### Important

Two requests can use the same URL path but different HTTP methods.

Express.js uses both the HTTP method and URL path to determine which route should handle the incoming request.

## 6. Understanding Route Handlers

A route handler is a function that contains the application logic executed when an incoming HTTP request matches a defined route.

The route identifies the HTTP method and URL path, while the route handler determines what the server should do when that route is accessed.

### Example

```javascript
app.get("/api/students", (req, res) => {
    res.send("List of students");
});
```

In this example:

- `app.get()` defines a GET route.
- `"/api/students"` identifies the URL path.
- `(req, res) => { ... }` is the route handler.
- `res.send()` sends a response to the client.

### The Request and Response Objects

A route handler commonly receives two objects:

- **`req` (Request):** Contains information about the incoming HTTP request.
- **`res` (Response):** Provides methods for sending an HTTP response back to the client.

The route handler uses these objects to process requests and return responses.

## 7. Understanding the Request (`req`) Object

The `req` object represents the incoming HTTP request received by the Express server.

It contains information about the request that the client sent, allowing the route handler to access and process that information.

The `req` object can provide information such as:

- HTTP method.
- URL path.
- Route parameters.
- Query parameters.
- Request body.
- Request headers.

The route handler uses the `req` object to access information needed to process the client's request.

## 8. Route Parameters

Route parameters are dynamic values included in a URL path. They allow an API to identify specific resources without defining a separate route for every resource ID.

In Express.js, route parameters are defined using a colon (`:`) followed by the parameter name.

### Example

```javascript
app.get("/api/students/:id", (req, res) => {
    console.log(req.params.id);
});
```

In this example:

- `:id` defines a dynamic route parameter.
- `req.params.id` accesses the value of the route parameter.
- If the client requests `/api/students/5`, the value of `req.params.id` will be `"5"`.

### Examples of Requests

| Request URL | `req.params.id` |
|---|---|
| `/api/students/5` | `"5"` |
| `/api/students/12` | `"12"` |
| `/api/students/101` | `"101"` |

Route parameters allow a single route to handle requests for different resources based on their identifiers.

## 9. Query Parameters

Query parameters are values included in a URL that allow a client to provide additional instructions or criteria for retrieving data from an API.

They are commonly used to filter, sort, search or limit the data returned by an API.

Query parameters appear after a question mark (`?`) in the URL. Multiple query parameters are separated by an ampersand (`&`).

### Example

```http
GET /api/students?course=IT&limit=10
```

In this example:

- `course=IT` filters students according to their course.
- `limit=10` limits the number of students returned.
- `?` indicates the beginning of the query string.
- `&` separates multiple query parameters.

### Accessing Query Parameters in Express.js

Express allows route handlers to access query parameter values through `req.query`.

Example:

```javascript
app.get("/api/students", (req, res) => {
    console.log(req.query.course);
    console.log(req.query.limit);
});
```

If the client sends:

```http
GET /api/students?course=IT&limit=10
```

The values can be accessed through:

- `req.query.course` → `"IT"`
- `req.query.limit` → `"10"`

### Route Parameters vs Query Parameters

- **Route parameters** identify specific resources, such as a student with ID 5.
- **Query parameters** provide additional criteria or instructions, such as filtering students by course or limiting results.

Both are used to provide information to the API through the URL.

## 10. Understanding the Response (`res`) Object

The `res` object represents the HTTP response that the Express server sends back to the client.

Express provides methods through the `res` object that allow developers to return information and communicate the outcome of a request.

Common response methods include:

- `res.send()` – Sends a response to the client.
- `res.json()` – Sends a JSON response to the client.
- `res.status()` – Sets the HTTP status code of the response.

### Example

```javascript
app.get("/api/students", (req, res) => {
    const students = ["Precious", "Tom", "Lilly"];
    res.send(students);
});
```

In this example:

- The route handler defines an array of student names.
- `res.send()` sends the array back to the client.
- The client receives the response from the server.

The information returned by `res` depends on the data and response logic defined by the developer. Express does not automatically retrieve data unless the application is programmed to do so.

## 11. Sending JSON Responses with `res.json()`

JSON (JavaScript Object Notation) is a lightweight, language-independent data-interchange format commonly used by APIs to exchange information between clients and servers.

Express provides the `res.json()` method to send JSON responses to clients.

### Example

```javascript
app.get("/api/students", (req, res) => {
    const students = [
        { id: 1, name: "Precious" },
        { id: 2, name: "Tom" },
        { id: 3, name: "Lilly" }
    ];

    res.json(students);
});
```

When a client sends a GET request to `/api/students`, the server returns the student information as JSON.

### Example Response

```json
[
    { "id": 1, "name": "Precious" },
    { "id": 2, "name": "Tom" },
    { "id": 3, "name": "Lilly" }
]
```

### Why Use `res.json()`?

- It allows the server to return structured data.
- JSON is supported by many programming languages.
- It makes exchanging information between different applications easier.
- Express automatically sets the response Content-Type to `application/json`.

### Difference Between `res.send()` and `res.json()`

- `res.send()` sends a response and supports different types of content.
- `res.json()` specifically sends a JSON response.

Both can send JavaScript objects, but `res.json()` explicitly communicates that the response is JSON.

## 12. Setting HTTP Status Codes with `res.status()`

Express provides the `res.status()` method to set the HTTP status code of a response.

The status code communicates the outcome of the client's request, while the response body provides additional information or data.

### Example

```javascript
app.get("/api/students", (req, res) => {
    res.status(200).json({
        message: "Students retrieved successfully"
    });
});

### Understanding the Difference Between 200 OK and 201 Created

Although both status codes indicate success, they communicate different outcomes.

- **200 OK:** Indicates that the request was successfully processed.
- **201 Created:** Indicates that the request was successful and a new resource was created.

For example:

- A GET request that successfully retrieves students can return `200 OK`.
- A POST request that successfully creates a new student can return `201 Created`.

Choosing the appropriate status code allows the API to communicate the outcome of an operation accurately.

### Understanding the Code

- `req.params.id` retrieves the student ID from the URL.
- `Number()` converts the ID from a string into a number.
- `.find()` searches the students array for a student with a matching ID.
- `if (!student)` checks whether the student was not found.
- `res.status(404).json()` returns a 404 status code and a JSON error message.
- `res.status(200).json()` returns the student information when the student exists.

The `return` statement prevents the route handler from continuing after sending the 404 response.

## 15. Understanding the Request Body (`req.body`)

The request body contains data that a client sends to the server as part of an HTTP request.

It is commonly used when creating or updating resources through methods such as POST, PUT and PATCH.

### Example

A client sends the following JSON data when registering a student:

```json
{
    "name": "Precious",
    "course": "Information Technology",
    "email": "precious@example.com"
}
```

### Why Must Middleware Be Registered Before the Route Handler?

Middleware is executed in the order in which it is registered.

When `express.json()` is registered before a route handler:

1. The client sends a request containing JSON data.
2. `express.json()` parses the incoming JSON data.
3. The parsed data becomes accessible through `req.body`.
4. The route handler processes the request using the parsed data.

Registering middleware before the route handler ensures that the request body is parsed before the route attempts to access it.

### Difference Between `req.body` and `req.params`

- `req.body` accesses data submitted inside the HTTP request body. It is commonly used when creating or updating resources.
- `req.params` accesses dynamic values included in the URL path. It is commonly used to identify specific resources.

For example:

- `req.body.name` retrieves the student's name from the request body.
- `req.params.id` retrieves a student's ID from the URL path.

The two properties allow Express route handlers to access information from different parts of an HTTP request.