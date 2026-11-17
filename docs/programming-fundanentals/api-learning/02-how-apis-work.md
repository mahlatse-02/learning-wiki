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

3. **Response:** The server receives a response containing the result of the request and an appropriate HTTP status code.

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

1. **HTTP Method:** Specifies the action the client wants the server to perform

2. **URL (Endpoint):** Provide additional informatiion about the request, such as the content type or authorization details.

3. **Headers:** Provide additional information about the request, such as the content type or authentication detais.

4. **Body:** Contains data sent from the client to the server. It is commonly used when creating or updating resources.


**Example: User Registration**

A registration request body might contain:

- Email address
- Password
- First name
- Last name


The server processes this information and validates it before creating a new user.

**Important**

The request bosy carries the submitted information, but the server is responsible for validating it. For example, the server shoud check whether an email address is already registered before creating a new account.

