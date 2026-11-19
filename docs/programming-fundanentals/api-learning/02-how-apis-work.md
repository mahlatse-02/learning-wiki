# 02 - How APIs Work

## Learning Objectives

By the end of this section, I should be able to:

1. Explain how communication between a client and server works.
2. Understand the request response cycle.
3. Identify the main components of an HTTP request.
4. Identify  the main components of an HTTP response.
5. Explain how an API processes a request and returns a response.

## 1. Introduction

APIs enable communication between different software applications through a client-server architecture.

In this architecture, one application actsa as a client that identifies a request, while another application acts as a server that receives and processes the request before sending a response

The client and server communicate using agreed protocols and data formats, alloeing these to exchange information regardless of the programming language used to develop them.

### 1.1 Understanding the Client and the Server

**Client**

A client is an application or device that initialises communication by sending a request to the server.

Examples include:
    - A web browser requesting a webpage.
    - A mobile application reporting information
    - A Python program requesting data from an API

**Server**

A server is a computer or application that receives requests from clients, processes them, and sends responses back.

For example, a weather API server can receive a request for the current weather, retrieve relevant information, and return it to the requesting application.

**Example: Weather AApplication**

1. The weather application on the phone acts as a client.
2. The client sends the request to the weather API.
3. The server receives and processes the request.
4. The server sends a response containing the weather data.
5. The client receives the response and displays the information to the user.

### 1.2 The Requeest-Response Cycle

The request-response cycle describes the process through which a client and server communicate whenn using an API.

It consists of the following stages:

1. **Request:** The client sends a request to the server, asking for information or requesting an action.

2. **Processing:** The server receives and processes the request according to thte API's logic.

3. **Response:** The server sends a response containing the result of the request and an appropriate HTTP status code.

4. **Reception:** The client receives the response and interpretes the retirned information.

**Example: Retrieving a User Profile**

1. The client sends a request to retrieve a user's profile.
2. The server receives and processes the request.
3. The server checks whether the requested user exists.
4. If the user cannot be found, the server returns an error
   response with the HTTP status code `404 Not Found`.
5. The response may contain a message such as
   `"User profile not found"`.
6. The client receives the response and can display an
   appropriate message to the user.

**Important:**

A server does not always return the requested information.
It can also return an error response when a request cannot
be completed successfully.

## 2. Understanding HTTP Requests

An HTTP request is a message ssent by a client to a server to request information or ask the server to perform an action.

For example, a registration form sends an HTTP request containing the information needed to create a new user.

### 2.1 The Four Main Components of an HTTP Request

An HTTP request consists of four main components:

1. **HTTP Method:** Specifies the action the client wants
   the server to perform.

2. **URL (Endpoint):** Identifies the resource or functionality
   that the client wants to access.

3. **Headers:** Provide additional information about the
   request, such as the content type or authentication details.

4. **Body:** Contains data sent from the client to the server.
   It is commonly used when creating or updating resources.


**Example: User Registration**

A registration request body might contain:

- Email address
- Password
- First name
- Last name


The server processes this information and validates it before creating a new user.

**Important**

The request bosy carries the submitted information, but the server is responsible for validating it. For example, the server shoud check whether an email address is already registered before creating a new account.

### 2.2 HTTP Methods

An HTTP method specifies the action that a client wants the server to perform on a particular resource.

Common HTTP methods include:

| Method | Purpose | Example |
|---|---|---|
| GET | Retrieve information | Retrieve a user's profile |
| POST | Submit information or create a resource | Register a new user |
| PUT | Replace an existing resource | Replace a user's profile |
| PATCH | Partially update a resource | Change only a user's email |
| DELETE | Remove a resource | Delete a user's account |

**PUT vs PATCH**

- PUT replaces the existing resource with the supplied representation.
- PATCH modifies only specific parts of an existing resiurce

### 2.3 Understanding resource Endpoints

An endpoint identifies the resource or functionality that a client wants to access through an API.

For example:

   GET /api/products

This endpoint accesses the products collected and typically returns a list of products.

   GET /api/products/25

This endpoint accesses a specific product identified by the ID 25.

**Important distinction**

- '/api/products' refers to a collection of products
- '/api/products/25' refers to one specific product

The HTTP method determines the action to perform while the endpoint identifies the resource involved

### 2.4 HTTP Request Headers

HTTP headers provide additional information (metadata) about an HTTP request. They help the server understand how to interpret the request and handle the information being sent.

Common HTTP request headers include:

**1. Host**

Identifies the server's domain name.

Example:
'Host: example.com'

**2. Content-Type**

Specifies the format of the data being sent in the request body.

Example:
'Content-Type: application/json'

This tells the server that the request body contains JSON0frmatted data.

**3. Accept**

Specifies the response format that the client can accept.

Example:
'Accept: application/json'

**4. Authorization**

Can contain authorization credentials, such as an access token, used by the server to verify the client's identity or permissions.

Example:
'Authorization: Bearer <token>'

**Important distinction:**

- Content-Type describes the format of the data being sent.
- Accept describes the response format the client can accept.

### 2.5 HTTP Request Body

The request body is the part of an HTTP request that contains data the client wants to send to the server.

It is commonly used when:

- Registering a new user.
- Submitting a login form.
- Creating a new product.
- Updating existing information.

A request body is not required for every HTTP request.
For example, a typical GET request retrieves information without needing a request body.

#### Understanding JSON

JSON (JavaScript Object Notation) is a lightweight data-interchange format used by applications to exchange structured information.

Example of a JSON request body:

    {
      "firstName": "John",
      "lastName": "Smith",
      "email": "john@example.com",
      "password": "password123"
    }

#### Understanding JSON Structure

A JSON object contains key-value pairs.

- Keys identify pieces of information.
- Values represent the information associated with those keys.
- A colon separates a key from its value.
- Commas separate key-value pairs.
- Curly brackets define a JSON object.

#### JSON Data Types

JSON supports six data types:

1. **String:** Text enclosed in double quotation marks.
2. **Number:** Numeric values, including integers and decimals.
3. **Boolean:** Logical values represented by `true` or `false`.
4. **Object:** A collection of key-value pairs enclosed in `{ }`.
5. **Array:** An ordered collection of values enclosed in `[ ]`.
6. **Null:** Represents the absence of a value.

The client sends JSON data in the request body, and the server processes it according to the API's logic.

### 2.6 Putting an HTTP Request Together

An HTTP request combines the method, endpoint, headers
and request body to communicate the client's intentions
to the server.

Example:

    PUT /api/products/25 HTTP/1.1
    Host: shop.example.com
    Content-Type: application/json
    Accept: application/json

    {
      "price": 9500,
      "inStock": false
    }

**Breaking down the request:**

1. **HTTP Method:** `PUT`
   - Indicates that the client wants to replace an existing
     resource with the supplied representation.

2. **Endpoint:** `/api/products/25`
   - Identifies the product with ID 25.

3. **Headers:**
   - `Host` identifies the server's domain.
   - `Content-Type` specifies that the request body
     contains JSON data.
   - `Accept` specifies that the client can accept
     a JSON response.

4. **Request Body:**
   - Contains the product information being submitted.
   - `price` has a numeric value of `9500`.
   - `inStock` has a Boolean value of `false`.

**What happens after the request is sent?**

1. The client sends the HTTP request.
2. The server receives and examines the request.
3. The server identifies the method and endpoint.
4. The server interprets the request headers.
5. The server processes and validates the request body.
6. The server performs the requested operation.
7. The server prepares and sends an HTTP response.

## Understanding HTTP Responses

### 3.1 The Three Main Components of an HTTP Response

An HTTP response is a message sent by a server to a client after receiving and processing an HTTP request.

An HTTP response consists of three main components:

1. **Status Code:** Indicates the outcome of the request.
2. **Headers:** Provide additional information about the response, such as the data format being returned.
3. **Body:** Contains the data returned by the server, if applicable.

Example of an HTTP response:

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
      "id": 15,
      "name": "John Smith",
      "email": "john@example.com"
    }

**Breaking down the response:**

- **Status Code (`200 OK`):** Indicates that the request was successfully processed.
- **Response Header (`Content-Type: application/json`):** Indicates that the response body contains JSON-formatted data.
- **Response Body:** Contains the information returned by the server, such as the user's ID, name and email address.

### 3.2 HTTP Status Code Categories

HTTP status codes communicate the outcome of an HTTP request. They are grouped into five categories based on the first digit of the status code.

| Category | Meaning | Description |
|---|---|---|
| 1xx | Informational | Indicates that the request has been received and the process is continuing. |
| 2xx | Success | Indicates that the request was successfully handled. |
| 3xx | Redirection | Indicates that further action is required, such as following a redirect. |
| 4xx | Client Error | Indicates that something about the request or the conditions for fulfilling it prevents the request from being completed successfully. |
| 5xx | Server Error | Indicates that the server encountered a problem while attempting to fulfil the request. |

**Important:**

The first digit of a status code identifies its category. The remaining digits identify the specific status within that category.

For example:

- `200` belongs to the 2xx success category.
- `404` belongs to the 4xx client error category.
- `500` belongs to the 5xx server error category.

### 3.3 Common HTTP Success Status Codes (2xx)

The 2xx category indicates that an HTTP request was successfully handled. Different status codes within this category communicate specific outcomes.

| Status Code | Meaning | Description |
|---|---|---|
| `200 OK` | Request successful | Indicates that the request was successfully handled. The server may return the requested data in the response body. |
| `201 Created` | Resource created | Indicates that the request was successfully handled and a new resource was created. |
| `204 No Content` | Successful request with no content | Indicates that the request was successfully handled, but the server has no response body to return. |

#### 200 OK

Indicates that a request was successfully handled.

Example: A client requests product information, and the server returns the requested product details.

#### 201 Created

Indicates that a request was successfully handled and a new resource was created.

Example: A client submits a registration request, and the server successfully creates a new student account.

#### 204 No Content

Indicates that a request was successfully handled, but the server does not return a response body.

Example: A client requests that a product be deleted, and the server successfully deletes it without returning additional data.

### 3.4 Common HTTP Client Error Status Codes (4xx)

The 4xx category indicates that something about the client's request or the conditions for fulfilling it prevents the server from completing the request successfully.

Common 4xx status codes include:

| Status Code | Meaning | Description |
|---|---|---|
| `400 Bad Request` | Invalid request | The server cannot process the request because it contains invalid or incorrect information. |
| `401 Unauthorized` | Authentication required | The client has not provided valid authentication credentials. |
| `403 Forbidden` | Access forbidden | The server refuses access because the client does not have the required permissions. |
| `404 Not Found` | Resource not found | The requested resource cannot be found. |

#### 400 Bad Request

Indicates that the request contains invalid or incorrect information.

Example: A client submits a registration form with missing or invalid required information.

#### 401 Unauthorized

Indicates that the client has not successfully authenticated.

Example: A client tries to access a protected account without valid login credentials.

#### 403 Forbidden

Indicates that the server refuses access because the client does not have the required permissions.

Example: A student logs into a university system but attempts to access a page reserved for lecturers.

#### 404 Not Found

Indicates that the requested resource cannot be found.

Example: A client requests a student profile using an ID that does not exist.

**Important distinction: 401 vs 403**

- Authentication verifies the identity of a user.
- Authorization determines what an authenticated user is allowed to access.
- `401` relates to authentication.
- `403` relates to permissions and access restrictions.

### 3.5 Common HTTP Server Error Status Codes (5xx)

The 5xx category indicates that the server encountered a problem while attempting to fulfil a client's request.

Common 5xx status codes include:

| Status Code | Meaning | Description |
|---|---|---|
| `500 Internal Server Error` | Internal server error | The server encountered an unexpected problem while processing the request. |
| `503 Service Unavailable` | Service unavailable | The server is temporarily unable to handle requests, often because of maintenance or overload. |

#### 500 Internal Server Error

Indicates that the server encountered an unexpected internal problem while processing a request.

Example: An unexpected error occurs in the server's application code, preventing it from retrieving student information.

#### 503 Service Unavailable

Indicates that the server is temporarily unable to handle requests.

Example: An API server becomes overloaded because thousands of clients are accessing it simultaneously.

The server may recover once the overload has been reduced.

A server may also include a `Retry-After` response header to indicate when the client should try again.

Example:

    HTTP/1.1 503 Service Unavailable
    Retry-After: 60

This tells the client to wait 60 seconds before retrying.

**Important distinction:**

- `500` indicates an unexpected internal server problem.
- `503` indicates that the server is temporarily unavailable.

### 3.6 HTTP Response Headers

HTTP response headers provide additional information (metadata) about the response being sent from the server to the client.

They help the client understand the response and determine how to handle the returned information.

Common HTTP response headers include:

**1. Content-Type**

Specifies the format of the data contained in the response body.

Example:

    Content-Type: application/json

This tells the client that the response body contains JSON-formatted data.

**2. Content-Length**

Indicates the size of the response body in bytes.

Example:

    Content-Length: 250

This indicates that the response body is 250 bytes long.

**3. Cache-Control**

Provides instructions about whether and how a response can be stored and reused from a cache.

Example:

    Cache-Control: no-cache

This means a cached response must be revalidated with the server before it is reused.

**4. Set-Cookie**

Instructs a browser to store a cookie, which can be sent back to the server in later requests.

Example:

    Set-Cookie: sessionId=abc123

This instructs the browser to store a cookie named `sessionId`.

**Important distinction: Accept vs Content-Type**

- `Accept` is a request header that tells the server which response formats the client can accept.
- `Content-Type` is a response header that specifies the format of the content being returned.

### 3.7 HTTP Response Body

The response body is the part of an HTTP response that contains the data returned by the server to the client.

The server uses the response body to provide the requested information or communicate the result of an operation.

Example:

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
      "productId": 25,
      "productName": "Laptop",
      "price": 12000
    }

**Breaking down the response:**

- `200 OK` indicates that the request was successfully handled.
- `Content-Type: application/json` indicates that the response body contains JSON-formatted data.
- The JSON object contains the product information returned by the server.

The response body contains three pieces of information:

- `productId`: Identifies the product with ID 25.
- `productName`: Contains the product's name, Laptop.
- `price`: Contains the product's price, 12000.

#### Does Every HTTP Response Have a Body?

No. Some HTTP responses do not contain a response body.

For example:

    HTTP/1.1 204 No Content

This indicates that the request was successfully handled, but the server has no response body to return.

#### Common Response Body Formats

Depending on the API, a response body can contain different data formats, including:

- JSON
- XML
- Plain text
- HTML

### 3.8 Putting an HTTP Request and Response Together

An HTTP request and response work together to allow a client and server to exchange information through an API.

Example: Registering a New Student

#### Part 1: HTTP Request

The client sends the following request:

    POST /api/students HTTP/1.1
    Host: university.example.com
    Content-Type: application/json
    Accept: application/json

    {
      "firstName": "Precious",
      "course": "Software Development"
    }

**Breaking down the request:**

- **HTTP Method (`POST`):** Requests the creation of a new student resource.
- **Host (`university.example.com`):** Identifies the server's domain.
- **Endpoint (`/api/students`):** Identifies the students resource.
- **Content-Type:** Specifies that the request body contains JSON data.
- **Accept:** Indicates that the client can accept JSON responses.
- **Request Body:** Contains the information required to register the student.

#### Part 2: Server Processing

After receiving the request, the server:

1. Identifies the HTTP method and endpoint.
2. Reads and interprets the request headers.
3. Processes the JSON request body.
4. Validates the submitted student information.
5. Creates a new student resource if the information is valid.
6. Prepares an HTTP response.

#### Part 3: HTTP Response

The server returns:

    HTTP/1.1 201 Created
    Content-Type: application/json

    {
      "studentId": 101,
      "firstName": "Precious",
      "course": "Software Development"
    }

**Breaking down the response:**

- **Status Code (`201 Created`):** Indicates that a new student resource was successfully created.
- **Response Header (`Content-Type`):** Specifies that the response body contains JSON data.
- **Response Body:** Contains the details of the newly created student.

#### Part 4: Client Receives the Response

The client receives the response, interprets the JSON data and can display the registration result to the user.

**Key Takeaway:**

The client sends an HTTP request containing instructions and, when necessary, data. The server processes the request and returns an HTTP response containing a status code, headers and, where applicable, a response body.

## 4. How an API Processes a Request and Returns a Response

When an API receives an HTTP request, the server follows a series of steps to process the request and return an appropriate response.

### 4.1 Stages of API Request Processing

The general stages of API request processing include:

1. **Receive the Request**

   The server receives the HTTP request sent by the client.

2. **Identify the Route**

   The API examines the HTTP method and endpoint to determine which operation needs to be performed.

3. **Validate the Request**

   The API checks whether the submitted information is valid and whether all required information has been provided.

4. **Execute Application Logic**

   The server performs the requested operation, such as retrieving, creating or updating information.

5. **Prepare the Response**

   The server determines the appropriate HTTP status code, response headers and response body.

6. **Send the Response**

   The server sends the HTTP response back to the client.

### Example: Registering a Student

Imagine an API receives a request to register a new student:

    POST /api/students
    Content-Type: application/json

    {
      "firstName": "Precious",
      "course": "Software Development"
    }

The API processes the request, validates the submitted information and creates the student record if everything is valid.

It then returns an appropriate HTTP response to the client.

**Important:**

If validation fails, the API should not proceed with the requested operation. Instead, it should return an appropriate error response explaining the problem.

### 4.2 Handling Successful and Unsuccessful Requests

An API can return either a success response or an error response depending on the outcome of request processing.

#### Successful Requests

A successful request occurs when the API completes the operation requested by the client.

Example: A client submits valid student information, and the API successfully creates the student record.

The server may return:

    HTTP/1.1 201 Created
    Content-Type: application/json

    {
      "studentId": 101,
      "firstName": "Precious",
      "course": "Software Development"
    }

#### Unsuccessful Requests

An unsuccessful request occurs when the API cannot complete the operation requested by the client.

This can happen because of:

- Invalid or missing information.
- Authentication or permission problems.
- Resources that cannot be found.
- Server-side or database failures.

Example: A client submits valid student information, but the database becomes unavailable when the API attempts to save the record.

The server may return:

    HTTP/1.1 503 Service Unavailable

A server may also include a `Retry-After` header to indicate when the client should try again.

#### Key Differences

| Successful Request | Unsuccessful Request |
|---|---|
| The requested operation is completed. | The requested operation cannot be completed. |
| Returns an appropriate 2xx status code. | Returns an appropriate error status code, such as 4xx or 5xx. |
| May return requested or newly created data. | May return an error message explaining the problem. |

**Important:**

A request can pass validation but still fail during execution. Successful validation does not guarantee that the requested operation will be completed.

### 4.3 How Different Programming Languages Communicate Through APIs

Applications written in different programming languages can communicate through APIs because they follow common communication protocols and use agreed data formats.

An API does not require the client and server to be written in the same programming language.

For example:
- A Python application can act as the client.
- A JavaScript application can act as the API server.
- Both applications can communicate using HTTP.
- They can exchange structured information using JSON.

#### Understanding the Difference Between Protocols and Data Formats

**Communication Protocol (HTTP)**

A protocol defines the rules that applications follow when communicating.

HTTP defines how clients send requests to servers and how servers return responses.

**Data Format (JSON)**

A data format defines how information is structured and represented when it is exchanged between applications.

JSON is commonly used because different programming languages can parse and generate JSON data.

**Key Takeaway:**

APIs allow applications written in different programming languages to communicate by using common protocols, such as HTTP, and agreed data formats, such as JSON.