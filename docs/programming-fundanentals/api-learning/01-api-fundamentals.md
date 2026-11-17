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