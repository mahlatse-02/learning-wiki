# 01 - API Fundamentals

## Learning Objectives

By the end of this section, I should be able to:

1. Define what an API is.
2. Explain why APIs exist and why they are important
3. Describe how APIs enable communication between software systems
4. Explain abstraction and how APIs allow systems to interact without exposing their internal implementation

## 1. What is an API?

An Application Programming Interface (API) is a set of rules, protocols
and definitions that allows two or more software applications to
communicate and exchange data or functionality without needing to
understand each other's internal implementation.

This concept is known as **abstraction**.

### Important terminology

- **Application:** A software program designed to perform specific tasks
- **Interface:** A point of interaction between two systems.
- **Protocol:** A set of rules governing communication.
- **Request:** A message asking another system for data or functionality
- **Response:** Information returned after a request is processed


## 2. Why do APIs exist?

APIs exist to alllow software applications to communicate and reuse functionality or data provided by other system. Instead of developing every feature from scratch, developers use existing functionality through APIs

### Benefits of APIs

1. **Reusability**: Developers can use already existing functionality and data through APIs without creating functionality from scratch
2. **Abstraction**: Developers do not need to know internal functionality of a server or system to be able to transfer data through APIs.
3. **Efficiency**: The reuse of functionality and data transfer increaases efficiency by decreasing development time, allowing developers to focus on more unique parts of a project.
4. **Integration**: Different software applications can work together through APIs.

### Quick knowledge check
Supppose a developer builds an online shopping application and uses a payment API to process customer payments.
**Why is using a payment API better than developing an entire payment processing system from scratch?**
    - **Answer**: Using a payment API decreases time spent on developing the system, thus increasing efficiency. Established payment providers often have security measures and processes already in place (**Security**). It is also easier for a developer to use existing functionality instead of maintaining an entire apyment infrastructure (**Reliability**)


## 3. How APIs enable communication

APIs enable communication between different software applications by defining standard rules, protocols and data formats.

Applications do not need to be developed using the same programming language. They only need to follow the communication standards defined by the API.

### Key Components
1. **Protocols**: Define the rules for exchanging requests and responses between applications. For example, HTTP
2. **Data format**: Define how informationn is structured so that different applications can interpret it. For example, JSON and XML 
3. **API Rules**: Define how an application can interact with another system, including available operations and expected request and response structures

### Example
A python application can communicate with a JavaScript application through an API because both applications can exchange information using HTTP and a common data format such as JSON

## 4. Understanding Abstraction

Abstraction is the concept of hiding the internal implementation of a system while exposing only the functionality needed to interact with it.

APIs apply abstraction by allowing application to access data or functionality without needing to understanding how the other application processes, store or manage information.

### Example: ATM

When withdrawing money from an ATM:

1. The user requests a withdrawal.
2. The ATM sends the request to the bank's systems.
3. The bank processes the request using its internal logic.
4. The bank returns the result.
5. The ATM displays the result and dispenses money if approved.

The user does not need to understand how the bank verifies
accounts, checks balances or processes transactions.

Similarly, applications use APIs without needing to understand
the internal implementation of the systems they communicate with.