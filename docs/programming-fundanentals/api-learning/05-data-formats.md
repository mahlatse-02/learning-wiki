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

GET /api/students

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