# REST API Interview Flashcards

<!-- Card Start -->
### Front
What does REST stand for?

A) Reliable External State Transfer  
B) Representational State Transfer  
C) Remote Execution State Transfer  
D) Resource Execution State Transfer

### Back
**Correct Answer**: B

**Explanation**: REST stands for **Representational State Transfer**, an architectural style for designing networked applications that relies on stateless communication and standard HTTP methods.

*Reference*: Roy Fielding's doctoral dissertation (2000)
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP method is idempotent and safe?

A) POST  
B) PUT  
C) DELETE  
D) GET

### Back
**Correct Answer**: D

**Explanation**: **GET** is both idempotent (multiple identical requests have the same effect) and safe (doesn't modify server state). PUT and DELETE are idempotent but not safe, while POST is neither.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What does HATEOAS stand for?

A) Hypertext As The Engine Of Application State  
B) HTTP Authentication Through External OAuth Services  
C) Hierarchical Access To External Object Application Services  
D) Hyperlink Access To External Online Application Systems

### Back
**Correct Answer**: A

**Explanation**: **HATEOAS** (Hypertext As The Engine Of Application State) is a constraint of REST where clients interact with the application entirely through hypermedia provided dynamically by application servers.

*Reference*: Roy Fielding's REST architectural style
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP status code indicates a successful resource creation?

A) 200 OK  
B) 201 Created  
C) 202 Accepted  
D) 204 No Content

### Back
**Correct Answer**: B

**Explanation**: **201 Created** indicates that a request has been fulfilled and resulted in one or more new resources being created. The response should include a Location header with the URI of the new resource.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What is the main difference between PUT and PATCH methods?

A) PUT is for updates, PATCH is for creation  
B) PUT replaces entire resource, PATCH applies partial modifications  
C) PUT is idempotent, PATCH is not  
D) PUT is safe, PATCH is not

### Back
**Correct Answer**: B

**Explanation**: **PUT** replaces the entire resource with the request payload, while **PATCH** applies partial modifications to a resource. Both are typically idempotent, but PATCH may not be depending on implementation.

*Reference*: RFC 5789 - PATCH Method for HTTP
<!-- Card End -->

<!-- Card Start -->
### Front
Which constraint requires that each request contains all information needed to understand it?

A) Client-Server  
B) Stateless  
C) Cacheable  
D) Uniform Interface

### Back
**Correct Answer**: B

**Explanation**: The **Stateless** constraint requires that each request from client to server must contain all information necessary to understand the request, without relying on stored context on the server.

*Reference*: Roy Fielding's REST architectural constraints
<!-- Card End -->

<!-- Card Start -->
### Front
What is the recommended approach for API versioning in REST?

A) Query parameters (?version=1)  
B) HTTP headers (Accept: application/vnd.api+json;version=1)  
C) URL path (/api/v1/users)  
D) All approaches are equally valid

### Back
**Correct Answer**: D

**Explanation**: All approaches are valid, each with trade-offs:
- **URL path**: Simple, cache-friendly
- **Headers**: Cleaner URLs, content negotiation
- **Query params**: Explicit, easy debugging

Choose based on your specific requirements and constraints.

*Reference*: REST API design best practices
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP status code should be returned when a resource is not found?

A) 400 Bad Request  
B) 401 Unauthorized  
C) 403 Forbidden  
D) 404 Not Found

### Back
**Correct Answer**: D

**Explanation**: **404 Not Found** indicates that the server has not found anything matching the Request-URI. This is the standard response when a requested resource doesn't exist.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What is the Richardson Maturity Model's highest level?

A) Level 0 - The Swamp of POX  
B) Level 1 - Resources  
C) Level 2 - HTTP Methods  
D) Level 3 - Hypermedia Controls

### Back
**Correct Answer**: D

**Explanation**: **Level 3 - Hypermedia Controls** is the highest level, where the API uses HATEOAS to guide clients through available actions. This represents true REST according to Fielding's definition.

*Reference*: Martin Fowler's Richardson Maturity Model
<!-- Card End -->

<!-- Card Start -->
### Front
Which caching strategy is most appropriate for frequently changing data?

A) Cache-Control: public, max-age=3600  
B) Cache-Control: private, no-cache  
C) Cache-Control: no-store  
D) ETag with conditional requests

### Back
**Correct Answer**: D

**Explanation**: **ETag with conditional requests** allows efficient caching of frequently changing data. Clients can use If-None-Match headers to receive 304 Not Modified responses when data hasn't changed.

*Reference*: RFC 7232 - HTTP/1.1 Conditional Requests
<!-- Card End -->

<!-- Card Start -->
### Front
What is the primary purpose of the OPTIONS HTTP method?

A) Delete a resource  
B) Update a resource partially  
C) Discover allowed methods for a resource  
D) Create a new resource

### Back
**Correct Answer**: C

**Explanation**: **OPTIONS** is used to discover the allowed HTTP methods and other capabilities for a specific resource. It's commonly used in CORS preflight requests.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
Which media type is commonly used for API error responses?

A) text/plain  
B) application/xml  
C) application/problem+json  
D) text/html

### Back
**Correct Answer**: C

**Explanation**: **application/problem+json** (RFC 7807) is a standardized media type for representing problem details in HTTP API responses, providing structured error information.

*Reference*: RFC 7807 - Problem Details for HTTP APIs
<!-- Card End -->

<!-- Card Start -->
### Front
What is the main benefit of using hypermedia in REST APIs?

A) Faster response times  
B) Reduced coupling between client and server  
C) Smaller payload sizes  
D) Better security

### Back
**Correct Answer**: B

**Explanation**: **Reduced coupling** is the main benefit. Hypermedia allows servers to guide client behavior through links, enabling server-side changes without breaking clients that follow the hypermedia controls.

*Reference*: HATEOAS principle in REST
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP status code indicates that authentication is required?

A) 400 Bad Request  
B) 401 Unauthorized  
C) 403 Forbidden  
D) 405 Method Not Allowed

### Back
**Correct Answer**: B

**Explanation**: **401 Unauthorized** indicates that the request has not been applied because it lacks valid authentication credentials. The response must include a WWW-Authenticate header.

*Reference*: RFC 7235 - HTTP/1.1 Authentication
<!-- Card End -->

<!-- Card Start -->
### Front
What is the recommended approach for handling bulk operations in REST?

A) Single endpoint with array payload  
B) Multiple individual requests  
C) Custom RPC-style endpoint  
D) Depends on the use case and constraints

### Back
**Correct Answer**: D

**Explanation**: The approach **depends on constraints**:
- **Array payload**: Simple, atomic
- **Individual requests**: Pure REST, parallelizable
- **Batch endpoint**: Efficient for large operations

Consider performance, atomicity, and complexity requirements.

*Reference*: REST API design patterns
<!-- Card End -->

<!-- Card Start -->
### Front
Which principle states that the network architecture should not depend on the data being transferred?

A) Stateless  
B) Uniform Interface  
C) Layered System  
D) Code on Demand

### Back
**Correct Answer**: B

**Explanation**: **Uniform Interface** is the architectural constraint that decouples the architecture from the data representation, enabling independent evolution of components.

*Reference*: Roy Fielding's REST architectural constraints
<!-- Card End -->

<!-- Card Start -->
### Front
What is the purpose of the Accept header in HTTP requests?

A) Specify authentication credentials  
B) Indicate preferred response media types  
C) Set caching directives  
D) Define request body encoding

### Back
**Correct Answer**: B

**Explanation**: The **Accept header** specifies which media types the client can process in the response. It enables content negotiation between client and server.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP method should be used to replace an entire resource?

A) POST  
B) PUT  
C) PATCH  
D) UPDATE

### Back
**Correct Answer**: B

**Explanation**: **PUT** should be used to replace an entire resource. It's idempotent and requires the complete representation of the resource in the request body.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What does the principle of "Uniform Interface" include?

A) Only HTTP methods  
B) Resource identification, manipulation through representations, self-descriptive messages, HATEOAS  
C) Only URI design  
D) Only status codes

### Back
**Correct Answer**: B

**Explanation**: **Uniform Interface** includes four constraints:
1. **Resource identification** in requests
2. **Resource manipulation** through representations
3. **Self-descriptive messages**
4. **HATEOAS** (hypermedia as the engine of application state)

*Reference*: Roy Fielding's REST architectural style
<!-- Card End -->

<!-- Card Start -->
### Front
Which status code should be used when a client sends a request with invalid syntax?

A) 400 Bad Request  
B) 401 Unauthorized  
C) 422 Unprocessable Entity  
D) 500 Internal Server Error

### Back
**Correct Answer**: A

**Explanation**: **400 Bad Request** indicates that the server cannot process the request due to invalid syntax. For semantic errors with valid syntax, use 422 Unprocessable Entity.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What is the main advantage of stateless communication in REST?

A) Better performance  
B) Improved scalability and reliability  
C) Reduced bandwidth usage  
D) Enhanced security

### Back
**Correct Answer**: B

**Explanation**: **Improved scalability and reliability** are the main advantages. Stateless communication allows any server to handle any request, enabling load balancing, fault tolerance, and horizontal scaling.

*Reference*: REST architectural constraints
<!-- Card End -->

<!-- Card Start -->
### Front
Which header is used to specify the media type of the request body?

A) Accept  
B) Content-Type  
C) Content-Encoding  
D) Content-Length

### Back
**Correct Answer**: B

**Explanation**: **Content-Type** specifies the media type of the request or response body. Accept header is used to specify preferred response media types.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What is the recommended approach for handling nested resources in REST URLs?

A) /users/123/posts/456  
B) /users/123?posts=456  
C) /posts/456?user=123  
D) Both A and C are valid approaches

### Back
**Correct Answer**: D

**Explanation**: **Both approaches are valid**:
- `/users/123/posts/456`: Good when the relationship is hierarchical
- `/posts/456?user=123`: Good when posts can exist independently

Choose based on the logical relationship and access patterns.

*Reference*: REST API design best practices
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP status code indicates that the request was successful but there's no content to return?

A) 200 OK  
B) 201 Created  
C) 202 Accepted  
D) 204 No Content

### Back
**Correct Answer**: D

**Explanation**: **204 No Content** indicates that the server successfully processed the request but is not returning any content. Common for DELETE operations or updates that don't return data.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What is the main purpose of rate limiting in REST APIs?

A) Improve response times  
B) Protect against abuse and ensure fair usage  
C) Reduce server costs  
D) Enhance security through obscurity

### Back
**Correct Answer**: B

**Explanation**: **Rate limiting protects against abuse** and ensures fair usage by limiting the number of requests a client can make within a time window, preventing DoS attacks and resource exhaustion.

*Reference*: API security and scalability best practices
<!-- Card End -->

<!-- Card Start -->
### Front
Which constraint allows for the introduction of intermediate servers like proxies and gateways?

A) Client-Server  
B) Stateless  
C) Layered System  
D) Cacheable

### Back
**Correct Answer**: C

**Explanation**: **Layered System** constraint allows for architectural layers, enabling the introduction of intermediary servers like proxies, gateways, and load balancers without affecting client-server communication.

*Reference*: Roy Fielding's REST architectural constraints
<!-- Card End -->

<!-- Card Start -->
### Front
What is the recommended way to handle pagination in REST APIs?

A) Page numbers only (?page=1&size=20)  
B) Offset and limit (?offset=0&limit=20)  
C) Cursor-based pagination with links  
D) All approaches are valid depending on use case

### Back
**Correct Answer**: D

**Explanation**: **All approaches are valid** with different trade-offs:
- **Page numbers**: Simple, familiar
- **Offset/limit**: Flexible, standard
- **Cursor-based**: Consistent for real-time data

Choose based on data characteristics and performance requirements.

*Reference*: REST API pagination patterns
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP method is NOT idempotent?

A) GET  
B) PUT  
C) DELETE  
D) POST

### Back
**Correct Answer**: D

**Explanation**: **POST** is not idempotent. Multiple identical POST requests may have different effects (e.g., creating multiple resources). GET, PUT, and DELETE are idempotent by definition.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What is the purpose of the ETag header?

A) Authentication  
B) Resource versioning for cache validation  
C) Content encoding  
D) Request routing

### Back
**Correct Answer**: B

**Explanation**: **ETag** (Entity Tag) provides a mechanism for cache validation and optimistic concurrency control. It's an identifier for a specific version of a resource.

*Reference*: RFC 7232 - HTTP/1.1 Conditional Requests
<!-- Card End -->

<!-- Card Start -->
### Front
Which status code should be returned when a client attempts to create a resource that already exists?

A) 400 Bad Request  
B) 409 Conflict  
C) 422 Unprocessable Entity  
D) 500 Internal Server Error

### Back
**Correct Answer**: B

**Explanation**: **409 Conflict** indicates that the request could not be completed due to a conflict with the current state of the resource, such as attempting to create a duplicate resource.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What is the main principle behind REST resource identification?

A) Resources are identified by SQL queries  
B) Resources are identified by URIs  
C) Resources are identified by object references  
D) Resources are identified by database keys

### Back
**Correct Answer**: B

**Explanation**: **Resources are identified by URIs** (Uniform Resource Identifiers). Each resource should have a unique URI that serves as its identifier in the REST architecture.

*Reference*: REST architectural style principles
<!-- Card End -->

<!-- Card Start -->
### Front
Which approach is recommended for API authentication in modern REST APIs?

A) Basic Authentication  
B) API Keys in URL parameters  
C) JWT tokens in Authorization header  
D) Session cookies

### Back
**Correct Answer**: C

**Explanation**: **JWT tokens in Authorization header** (Bearer token) is recommended for modern REST APIs as it's stateless, secure, and supports fine-grained access control without server-side session storage.

*Reference*: OAuth 2.0 and JWT best practices
<!-- Card End -->

<!-- Card Start -->
### Front
What does the "Code on Demand" constraint allow in REST architecture?

A) Server-side code execution  
B) Client downloading and executing code from server  
C) Dynamic API generation  
D) Code compilation on the server

### Back
**Correct Answer**: B

**Explanation**: **Code on Demand** (optional constraint) allows clients to download and execute code from the server, such as JavaScript in web browsers, extending client functionality dynamically.

*Reference*: Roy Fielding's REST architectural constraints
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP header is used for conditional requests based on modification time?

A) If-Match  
B) If-None-Match  
C) If-Modified-Since  
D) If-Unmodified-Since

### Back
**Correct Answer**: C

**Explanation**: **If-Modified-Since** is used in conditional GET requests to retrieve a resource only if it has been modified since the specified date, enabling efficient caching.

*Reference*: RFC 7232 - HTTP/1.1 Conditional Requests
<!-- Card End -->

<!-- Card Start -->
### Front
What is the recommended approach for handling partial failures in bulk operations?

A) Fail the entire operation  
B) Return partial success with detailed status for each item  
C) Retry failed items automatically  
D) Ignore failed items silently

### Back
**Correct Answer**: B

**Explanation**: **Return partial success with detailed status** allows clients to understand which operations succeeded/failed and take appropriate action. Use HTTP 207 Multi-Status for batch operations.

*Reference*: HTTP batch processing patterns
<!-- Card End -->

<!-- Card Start -->
### Front
Which principle states that REST components should not retain client state between requests?

A) Client-Server separation  
B) Stateless communication  
C) Uniform Interface  
D) Layered System

### Back
**Correct Answer**: B

**Explanation**: **Stateless communication** requires that servers do not store client context between requests. Each request must contain all necessary information for processing.

*Reference*: REST stateless constraint
<!-- Card End -->

<!-- Card Start -->
### Front
What is the main benefit of using standardized media types in REST APIs?

A) Reduced bandwidth usage  
B) Improved interoperability and loose coupling  
C) Better performance  
D) Enhanced security

### Back
**Correct Answer**: B

**Explanation**: **Improved interoperability and loose coupling** allows different clients and servers to communicate effectively without tight coupling to specific implementations or data formats.

*Reference*: REST uniform interface constraint
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP status code should be used when a client sends semantically incorrect data with valid syntax?

A) 400 Bad Request  
B) 401 Unauthorized  
C) 422 Unprocessable Entity  
D) 500 Internal Server Error

### Back
**Correct Answer**: C

**Explanation**: **422 Unprocessable Entity** indicates that the server understands the content type and syntax of the request but was unable to process the contained instructions due to semantic errors.

*Reference*: RFC 4918 - HTTP Extensions for WebDAV
<!-- Card End -->

<!-- Card Start -->
### Front
What is the primary advantage of using HATEOAS in REST APIs?

A) Better performance  
B) Reduced API documentation needs  
C) Dynamic discoverability and evolvability  
D) Smaller response payloads

### Back
**Correct Answer**: C

**Explanation**: **Dynamic discoverability and evolvability** allows APIs to evolve without breaking clients, as clients follow hypermedia links rather than hardcoded URLs, enabling server-driven navigation.

*Reference*: HATEOAS constraint in REST architecture
<!-- Card End -->

<!-- Card Start -->
### Front
Which approach is recommended for handling API errors in REST?

A) Always return 200 OK with error details in body  
B) Use appropriate HTTP status codes with structured error responses  
C) Return HTML error pages  
D) Use only generic error messages

### Back
**Correct Answer**: B

**Explanation**: **Use appropriate HTTP status codes with structured error responses** provides clear semantics through status codes and detailed information through standardized error response formats like RFC 7807.

*Reference*: RFC 7807 - Problem Details for HTTP APIs
<!-- Card End -->

<!-- Card Start -->
### Front
What is the purpose of the HEAD HTTP method?

A) Delete a resource  
B) Get metadata about a resource without the body  
C) Update a resource  
D) Create a new resource

### Back
**Correct Answer**: B

**Explanation**: **HEAD** retrieves the same headers as a GET request but without the response body. It's useful for checking resource existence, size, or last modification without transferring the full content.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP status code indicates that the server is temporarily unable to handle the request?

A) 500 Internal Server Error  
B) 502 Bad Gateway  
C) 503 Service Unavailable  
D) 504 Gateway Timeout

### Back
**Correct Answer**: C

**Explanation**: **503 Service Unavailable** indicates that the server is temporarily overloaded or undergoing maintenance. It should include a Retry-After header suggesting when to retry.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What is the main difference between 401 Unauthorized and 403 Forbidden?

A) 401 means bad credentials, 403 means no credentials  
B) 401 means authentication required, 403 means access denied despite valid authentication  
C) They are identical  
D) 401 is for users, 403 is for systems

### Back
**Correct Answer**: B

**Explanation**: **401 Unauthorized** means authentication is required or has failed. **403 Forbidden** means the server understood the request but refuses to authorize it, even with valid credentials.

*Reference*: RFC 7235 - HTTP/1.1 Authentication
<!-- Card End -->

<!-- Card Start -->
### Front
Which caching directive prevents any caching of the response?

A) Cache-Control: no-cache  
B) Cache-Control: no-store  
C) Cache-Control: private  
D) Cache-Control: max-age=0

### Back
**Correct Answer**: B

**Explanation**: **Cache-Control: no-store** prevents any caching of the response. **no-cache** allows caching but requires revalidation, while **private** prevents shared caches but allows private caches.

*Reference*: RFC 7234 - HTTP/1.1 Caching
<!-- Card End -->

<!-- Card Start -->
### Front
What is the recommended HTTP method for searching resources in REST?

A) POST to /search  
B) GET with query parameters  
C) SEARCH method  
D) Both A and B are valid

### Back
**Correct Answer**: D

**Explanation**: **Both approaches are valid**:
- **GET with query params**: RESTful, cacheable, simple searches
- **POST to /search**: Complex searches with large payloads or sensitive data

Choose based on search complexity and caching requirements.

*Reference*: REST API design patterns
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP header should be used to specify the expected format of a PATCH request body?

A) Accept  
B) Content-Type  
C) Content-Encoding  
D) Accept-Patch

### Back
**Correct Answer**: B

**Explanation**: **Content-Type** specifies the media type of the request body, including PATCH payloads (e.g., application/json-patch+json, application/merge-patch+json).

*Reference*: RFC 5789 - PATCH Method for HTTP
<!-- Card End -->

<!-- Card Start -->
### Front
What is the main benefit of using ETags for optimistic concurrency control?

A) Improved performance  
B) Prevent lost updates in concurrent modifications  
C) Reduced bandwidth  
D) Better security

### Back
**Correct Answer**: B

**Explanation**: **ETags prevent lost updates** by allowing clients to include If-Match headers, ensuring modifications only occur if the resource hasn't changed since it was last retrieved.

*Reference*: RFC 7232 - HTTP/1.1 Conditional Requests
<!-- Card End -->

<!-- Card Start -->
### Front
Which approach is recommended for handling long-running operations in REST APIs?

A) Synchronous processing with extended timeouts  
B) Asynchronous processing with 202 Accepted and status polling  
C) WebSocket connections  
D) Server-sent events

### Back
**Correct Answer**: B

**Explanation**: **Asynchronous processing with 202 Accepted** is recommended. Return 202 immediately with a status URL, allowing clients to poll for completion status without blocking.

*Reference*: REST asynchronous processing patterns
<!-- Card End -->

<!-- Card Start -->
### Front
What is the purpose of the Vary header in HTTP responses?

A) Specify caching directives  
B) Indicate which request headers affect the response  
C) Define content encoding  
D) Set response timeouts

### Back
**Correct Answer**: B

**Explanation**: **Vary header** tells caches which request headers were used to determine the response, ensuring proper cache key generation for content negotiation scenarios.

*Reference*: RFC 7234 - HTTP/1.1 Caching
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP status code should be used when request processing will take a significant amount of time?

A) 200 OK  
B) 201 Created  
C) 202 Accepted  
D) 204 No Content

### Back
**Correct Answer**: C

**Explanation**: **202 Accepted** indicates that the request has been accepted for processing but processing has not been completed. It's ideal for asynchronous operations.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What is the main advantage of using JSON:API or HAL for hypermedia in REST APIs?

A) Smaller response sizes  
B) Standardized hypermedia format  
C) Better performance  
D) Enhanced security

### Back
**Correct Answer**: B

**Explanation**: **Standardized hypermedia formats** like JSON:API or HAL provide consistent, well-defined structures for including links and relationships, improving interoperability and tooling support.

*Reference*: JSON:API and HAL specifications
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP method should be used for partial updates when the update semantics are not idempotent?

A) PUT  
B) PATCH  
C) POST  
D) UPDATE

### Back
**Correct Answer**: C

**Explanation**: **POST** should be used when update operations are not idempotent (e.g., incrementing a counter). PATCH is typically idempotent, while PUT requires complete resource replacement.

*Reference*: HTTP method semantics and idempotency
<!-- Card End -->

<!-- Card Start -->
### Front
What is the recommended approach for handling API rate limit responses?

A) Return 429 with Retry-After header  
B) Return 503 with custom headers  
C) Return 400 with error message  
D) Return 200 with rate limit info in body

### Back
**Correct Answer**: A

**Explanation**: **429 Too Many Requests** with **Retry-After header** is the standard approach. Include additional headers like X-RateLimit-Limit and X-RateLimit-Remaining for client guidance.

*Reference*: RFC 6585 - Additional HTTP Status Codes
<!-- Card End -->

<!-- Card Start -->
### Front
Which approach is best for handling resource relationships in REST APIs?

A) Always embed related resources  
B) Always use separate endpoints  
C) Use links with optional embedding based on query parameters  
D) Use only resource IDs

### Back
**Correct Answer**: C

**Explanation**: **Links with optional embedding** provides flexibility. Use hypermedia links by default, allow embedding via query parameters (?include=comments) to reduce round trips when needed.

*Reference*: REST API relationship modeling patterns
<!-- Card End -->

<!-- Card Start -->
### Front
What is the purpose of the Location header in HTTP responses?

A) Specify the client's location  
B) Indicate the URI of a newly created or moved resource  
C) Define the server's location  
D) Set redirection timeouts

### Back
**Correct Answer**: B

**Explanation**: **Location header** specifies the URI of a newly created resource (with 201 Created) or the target URI for redirections (with 3xx status codes).

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
Which content negotiation mechanism allows clients to specify preferred response languages?

A) Accept header  
B) Accept-Language header  
C) Content-Language header  
D) Accept-Charset header

### Back
**Correct Answer**: B

**Explanation**: **Accept-Language header** allows clients to specify their preferred natural languages for the response content, enabling internationalization support.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
What is the recommended approach for handling partial responses in REST APIs?

A) Always return complete resources  
B) Use query parameters to specify fields (?fields=id,name)  
C) Use custom HTTP headers  
D) Use different endpoints for different views

### Back
**Correct Answer**: B

**Explanation**: **Query parameters like ?fields=id,name** allow clients to request specific fields, reducing bandwidth and improving performance. This is also known as sparse fieldsets.

*Reference*: REST API optimization patterns
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP status code indicates that the request could not be completed due to insufficient storage?

A) 507 Insufficient Storage  
B) 413 Payload Too Large  
C) 500 Internal Server Error  
D) 503 Service Unavailable

### Back
**Correct Answer**: A

**Explanation**: **507 Insufficient Storage** indicates that the server is unable to store the representation needed to complete the request, typically due to storage limitations.

*Reference*: RFC 4918 - HTTP Extensions for WebDAV
<!-- Card End -->

<!-- Card Start -->
### Front
What is the main purpose of the Accept-Encoding header?

A) Specify preferred response languages  
B) Indicate supported compression algorithms  
C) Define character encoding  
D) Specify content types

### Back
**Correct Answer**: B

**Explanation**: **Accept-Encoding** indicates which content encodings (compression algorithms) the client can handle, such as gzip, deflate, or brotli.

*Reference*: RFC 7231 - HTTP/1.1 Semantics and Content
<!-- Card End -->

<!-- Card Start -->
### Front
Which approach is recommended for API documentation that supports HATEOAS?

A) Static documentation only  
B) Interactive documentation that follows hypermedia links  
C) No documentation needed  
D) Separate documentation for each API version

### Back
**Correct Answer**: B

**Explanation**: **Interactive documentation that follows hypermedia links** allows documentation to evolve with the API, maintaining accuracy and demonstrating the hypermedia-driven nature of the API.

*Reference*: HATEOAS documentation best practices
<!-- Card End -->

<!-- Card Start -->
### Front
What is the current version of the OpenAPI Specification (formerly Swagger)?

A) OpenAPI 2.0  
B) OpenAPI 3.0  
C) OpenAPI 3.1  
D) OpenAPI 4.0

### Back
**Correct Answer**: C

**Explanation**: **OpenAPI 3.1** is the current version, released in 2021. It's fully compatible with JSON Schema Draft 2020-12 and includes improvements like webhooks support and enhanced schema composition.

*Reference*: OpenAPI Initiative specification
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP header is commonly used to serve OpenAPI documentation?

A) Content-Type: application/json  
B) Content-Type: application/yaml  
C) Content-Type: application/x-yaml  
D) All of the above can be valid

### Back
**Correct Answer**: D

**Explanation**: **All formats are valid** for serving OpenAPI specs:
- **application/json**: For JSON format
- **application/yaml** or **text/yaml**: For YAML format
- **application/x-yaml**: Alternative YAML MIME type

Choose based on client preferences and content negotiation.

*Reference*: OpenAPI specification and HTTP standards
<!-- Card End -->

<!-- Card Start -->
### Front
What is the primary benefit of using OpenAPI specifications in REST API development?

A) Better runtime performance  
B) Documentation generation and contract-first development  
C) Reduced server costs  
D) Enhanced security

### Back
**Correct Answer**: B

**Explanation**: **Documentation generation and contract-first development** are the primary benefits. OpenAPI specs enable automatic documentation, client SDK generation, server stubs, and API testing tools.

*Reference*: OpenAPI specification benefits and tooling ecosystem
<!-- Card End -->

<!-- Card Start -->
### Front
Which OpenAPI component is used to define reusable response objects?

A) parameters  
B) schemas  
C) responses  
D) components/responses

### Back
**Correct Answer**: D

**Explanation**: **components/responses** section defines reusable response objects that can be referenced throughout the OpenAPI specification using $ref, promoting consistency and reducing duplication.

*Reference*: OpenAPI 3.x specification structure
<!-- Card End -->

<!-- Card Start -->
### Front
Which HTTP methods are cacheable by default according to RFC 7231?

A) GET and HEAD  
B) GET, HEAD, and POST  
C) GET only  
D) GET, HEAD, and PUT

### Back
**Correct Answer**: A

**Explanation**: By default, responses to **GET** and **HEAD** are cacheable. **POST** responses may be cacheable only if explicitly indicated by cache directives.

*Reference*: RFC 7231, RFC 7234
<!-- Card End -->

<!-- Card Start -->
### Front
Which header enables safely retrying non-idempotent POST operations?

A) If-Match  
B) Retry-After  
C) Idempotency-Key  
D) Vary

### Back
**Correct Answer**: C

**Explanation**: An **Idempotency-Key** correlates retries so the server can de-duplicate repeated POSTs, ensuring only one side effect occurs.

*Reference*: Industry best practice (e.g., Stripe idempotency keys)
<!-- Card End -->

<!-- Card Start -->
### Front
Which header carries pagination navigation links like next/prev?

A) Pagination  
B) Link  
C) Content-Range  
D) Location

### Back
**Correct Answer**: B

**Explanation**: The **Link** header conveys hypermedia links for pagination using rel values like `next`, `prev`, `first`, and `last`.

*Reference*: RFC 8288 (Web Linking)
<!-- Card End -->

<!-- Card Start -->
### Front
Which header communicates planned deprecation or sunset of an API?

A) Sunset  
B) Deprecation  
C) Expires  
D) Warning

### Back
**Correct Answer**: A

**Explanation**: **Sunset** advertises when an API will be retired. It can be paired with `Link: rel="deprecation"` to documentation.

*Reference*: RFC 8594 (Sunset Header Field)
<!-- Card End -->

<!-- Card Start -->
### Front
Which headers are sent in a CORS preflight request?

A) Origin only  
B) Access-Control-Request-Method and Access-Control-Request-Headers  
C) Access-Control-Allow-Origin and Access-Control-Allow-Methods  
D) Vary: Origin

### Back
**Correct Answer**: B

**Explanation**: The browser sends **Access-Control-Request-Method** and optionally **Access-Control-Request-Headers** with **Origin** in the preflight; the server responds with `Access-Control-Allow-*` headers.

*Reference*: CORS (Fetch/WHATWG)
<!-- Card End -->

<!-- Card Start -->
### Front
Which media type defines JSON Patch operations for partial updates?

A) application/merge-patch+json  
B) application/json-patch+json  
C) application/patch+json  
D) application/problem+json

### Back
**Correct Answer**: B

**Explanation**: **application/json-patch+json** specifies a sequence of operations (add, remove, replace, etc.). **Merge Patch** uses `application/merge-patch+json` with merge semantics.

*Reference*: RFC 6902 (JSON Patch), RFC 7396 (JSON Merge Patch)
<!-- Card End -->

<!-- Card Start -->
### Front
Which status code should be returned when none of the representations match the Accept header?

A) 400 Bad Request  
B) 406 Not Acceptable  
C) 415 Unsupported Media Type  
D) 422 Unprocessable Entity

### Back
**Correct Answer**: B

**Explanation**: **406 Not Acceptable** indicates the server cannot produce a response matching the Accept header’s criteria.

*Reference*: RFC 7231 - Content negotiation
<!-- Card End -->

<!-- Card Start -->
### Front
When are weak ETags more appropriate than strong ETags?

A) When byte-for-byte equality is required  
B) When semantically equivalent representations may differ in bytes  
C) When caching must be disabled  
D) When using Range requests

### Back
**Correct Answer**: B

**Explanation**: **Weak ETags** (prefixed with `W/`) validate semantic equivalence despite minor byte differences (e.g., formatting), while strong ETags require exact byte equality.

*Reference*: RFC 7232 - Validators
<!-- Card End -->

<!-- Card Start -->
### Front
Which status code indicates the server does not support the request Content-Type?

A) 406 Not Acceptable  
B) 415 Unsupported Media Type  
C) 405 Method Not Allowed  
D) 501 Not Implemented

### Back
**Correct Answer**: B

**Explanation**: **415 Unsupported Media Type** applies when the server cannot process the request payload format indicated by **Content-Type**.

*Reference*: RFC 7231 - HTTP semantics
<!-- Card End -->

<!-- Card Start -->
### Front
When returning 405 Method Not Allowed, which header must be included?

A) Allow  
B) Location  
C) Retry-After  
D) Vary

### Back
**Correct Answer**: A

**Explanation**: **Allow** lists the permitted methods for the target resource and is required with **405 Method Not Allowed**.

*Reference*: RFC 7231 - HTTP semantics
<!-- Card End -->

<!-- Card Start -->
### Front
Which status code is appropriate when a conditional update fails due to an ETag mismatch?

A) 409 Conflict  
B) 412 Precondition Failed  
C) 428 Precondition Required  
D) 304 Not Modified

### Back
**Correct Answer**: B

**Explanation**: **412 Precondition Failed** indicates the condition (e.g., `If-Match: <etag>`) was not met, preventing lost updates in optimistic concurrency.

*Reference*: RFC 7232 - Conditional Requests
<!-- Card End -->

<!-- Card Start -->
### Front
What is the recommended approach for versioning OpenAPI specifications?

A) Include version in the OpenAPI document only  
B) Use semantic versioning aligned with API versions  
C) Version the specification independently of the API  
D) Both A and B are recommended practices

### Back
**Correct Answer**: D

**Explanation**: **Both approaches are recommended**:
- **Document versioning**: Track spec changes using semantic versioning
- **API version alignment**: Keep spec version synchronized with actual API version

This ensures clear tracking of both specification evolution and API changes.

*Reference*: OpenAPI specification versioning best practices
<!-- Card End -->