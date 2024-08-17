## RFC
- "Request for Comments"
- Internet Stnadards from the Itnernet Engineering Task Force (IETF)
- https://datatracker.ietf.org/

## HTTP
- Hypertext Transfer Protocol (HTTP) is an application-layer protocol for transmitting hypermedia documents, such as HTML. It is the foundation of any data exchange on the Web and it is a protocol used for transmitting and receiving information across the Internet.
- Client and Server: Server listens for requests for resources from clients
- URL: Uniform Resource Locator (unique address for a resource) - combination of the Uniform Resource Name (url) and the Server to reach out to for the resource
  - https://datatracker.ietf.org/doc/html/rfc1738
- HTTP is the protocol for sending and receiving the bytes 
- https://developer.mozilla.org/en-US/docs/Web/HTTP
  
## HTTP Methods

HTTP defines a set of request methods, also known as HTTP verbs, that indicate the desired action to be performed on a resource. Here are some commonly used HTTP methods:

- GET: Retrieves a representation of the specified resource.
- POST: Submits data to be processed to the specified resource.
- PUT: Updates the specified resource with the provided data.
- DELETE: Deletes the specified resource.
- PATCH: Partially updates the specified resource.

Each HTTP method has a specific purpose and usage. It is important to choose the appropriate method based on the desired action and the semantics of the resource being manipulated.

For more information on HTTP methods and their usage, you can refer to the [HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) documentation on MDN.

## HTTP Status Codes

HTTP status codes are three-digit numbers that indicate the outcome of a HTTP request. They provide information about the success or failure of a request and help in troubleshooting and debugging. Here are some commonly used HTTP status codes:

- 200 OK: The request was successful.
- 201 Created: The request was successful, and a new resource was created.
- 400 Bad Request: The request was malformed or invalid.
- 404 Not Found: The requested resource could not be found.
- 500 Internal Server Error: An unexpected error occurred on the server.

HTTP status codes are grouped into different categories, such as 2xx for successful responses, 4xx for client errors, and 5xx for server errors. It is important to handle different status codes appropriately in your application to provide meaningful feedback to the user.

For a complete list of HTTP status codes and their meanings, you can refer to the [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) documentation on MDN.

## REST API Design Best Practices

REST (Representational State Transfer) is a set of principles and constraints for designing web services. It is built on top of the HTTP protocol and provides a standardized way to structure and interact with APIs. In this section, we will discuss some best practices for designing your REST API.

### Client-Server Separation
One of the key principles of REST is the separation of client and server. The client should not need to know the implementation details of the server, and the server should not have to know what kind of client is making the request. This separation allows for better scalability and flexibility in the system architecture.

### Uniform Interface
A uniform interface is another important aspect of REST. It means that the API should have a consistent and predictable structure. Endpoints should be named using nouns that represent the resources or collections of resources they return. Avoid using verbs in the endpoint names, as the HTTP methods act as the verbs. This makes the API more intuitive and easier to understand.

### Stateless
REST APIs should be stateless, meaning that each request from the client should contain all the necessary information for the server to process it. The server should not rely on any previous requests or store any client-specific data. This allows for better scalability and fault tolerance, as the server can be easily replaced or scaled horizontally using load balancers.

### Caching
Caching is an important optimization technique in REST APIs. It allows the server to store information that is frequently requested by clients, reducing the number of requests and improving performance. By setting appropriate caching headers, the server can indicate to the client how long the response can be cached.

### Layering (Abstraction)
REST APIs should expose the fewest details possible to the users. This promotes loose coupling and allows for better maintainability and extensibility. Users should not rely on any implementation details of the API, as they may change over time. Additionally, exposing unnecessary details can lead to security vulnerabilities.

For more in-depth guidelines and best practices for designing your REST API, you can refer to the article [Best Practices for Designing Your REST API](https://medium.com/@ibrahimsoliman97/summary-of-rest-api-design-rulebook-by-mark-mass%C3%A9-6f290fa04a2d).
