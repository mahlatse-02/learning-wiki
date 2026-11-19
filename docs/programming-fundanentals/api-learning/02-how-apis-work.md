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