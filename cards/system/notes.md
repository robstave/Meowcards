One of the key questions they asked me was to explain how I would design and build a secure and scalable RESTful API using Java and Spring Boot, which aligns directly with the role’s requirements



  Card Start -->
### Front
What are the key goals when designing a secure and scalable RESTful API?

### Back
The main goals are:

- **Security**: Ensure data integrity, confidentiality, and access control
- **Scalability**: Support growth in users or traffic without performance loss
- **Maintainability**: Follow clean architecture and separation of concerns
- **Resilience**: Handle failures gracefully
- **Observability**: Make the system measurable and debuggable
- **Versioning**: Prevent breaking changes for existing clients

<!-- Card End --> <!-- Card Start -->
### Front
Which annotations are commonly used to define RESTful endpoints in Spring Boot?

### Back
Key annotations:

- `@RestController` – Marks the class as a REST API controller
- `@RequestMapping` – Base path mapping for controller
- `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping` – Map HTTP methods to handler functions
- `@PathVariable` and `@RequestParam` – Extract dynamic parts of the URL or query params
- `@RequestBody` – Bind request body to a DTO

<!-- Card End --> <!-- Card Start -->
### Front
How would you structure a scalable Spring Boot API project?

### Back
Use a layered architecture:

- **Controller Layer**: Exposes REST endpoints
- **Service Layer**: Contains business logic
- **Repository Layer**: Manages persistence (e.g., via JPA)
- **DTOs**: For request/response decoupling
- **Global Exception Handler**: With `@ControllerAdvice`

<!-- Card End --> <!-- Card Start -->
### Front
How do you secure a Spring Boot REST API?

### Back
- Use Spring Security to manage authentication and authorization
- Implement JWT tokens or integrate with OAuth2 providers
- Use `@PreAuthorize` for method-level security
- Enforce HTTPS and secure HTTP headers
- Encrypt secrets using Spring Config or HashiCorp Vault
- Validate CORS policies

<!-- Card End --> <!-- Card Start -->
### Front
How do you handle input validation in Spring Boot?

### Back
- Use annotations like `@NotNull`, `@Size`, `@Email` in DTOs
- Add `@Valid` in controller method parameters
- Capture validation errors with `@ControllerAdvice` and handle `MethodArgumentNotValidException`
- Return structured error responses with helpful messages

<!-- Card End --> <!-- Card Start -->
### Front
What is the role of `@ControllerAdvice` in Spring Boot?

### Back
`@ControllerAdvice` is used for:

- Global exception handling
- Centralized logging of errors
- Returning consistent and structured error responses (e.g., status code, message, timestamp)
- Reducing boilerplate error handling code in individual controllers

<!-- Card End --> <!-- Card Start -->
### Front
How can you ensure that a Spring Boot API is scalable?

### Back
- Design for statelessness
- Use connection pooling and asynchronous processing with `@Async`
- Introduce caching (e.g., Redis, Caffeine)
- Support horizontal scaling with load balancers and containers
- Offload long-running tasks to queues like Kafka or RabbitMQ

<!-- Card End --> <!-- Card Start -->
### Front
What tools and techniques help observe and monitor a Spring Boot API?

### Back
- Use Spring Boot Actuator for health checks and metrics
- Log in JSON format for structured logs
- Export metrics to Prometheus and visualize with Grafana
- Use Elastic Stack for centralized logging
- Add trace IDs for distributed tracing (e.g., Sleuth, Zipkin)

<!-- Card End --> <!-- Card Start -->
### Front
What are some options for versioning a REST API?

### Back
- **URI versioning**: `/api/v1/resource`
- **Header-based versioning**: `Accept: application/vnd.myapp.v1+json`
- Keep older versions alive while introducing non-breaking changes
- Use semantic versioning to track changes

<!-- Card End --> <!-- Card Start -->
### Front
How do you test a Spring Boot REST API?

### Back
- Use JUnit and Mockito for unit tests
- Use `@SpringBootTest` for integration testing
- Use MockMvc to test web layers without running a server
- Use Postman or RestAssured for functional and contract tests
- Automate tests in CI/CD pipelines

<!-- Card End -->
Let me know if you'd like a separate set just focused on security (e.g., JWT, OAuth2) or if you'd like this exported into a .md or .txt file for download/import.