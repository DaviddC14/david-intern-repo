# Logging & Error Handling in NestJS Reflection

**What are the benefits of using `nestjs-pino` for logging?**
Pino is an extremely fast Node.js logger that outputs structured JSON logs. Unlike standard `console.log()`, structured logging is easily ingested, queried, and analyzed by modern monitoring tools (like Datadog or Elasticsearch). It also adds significantly less performance overhead to the application.

**How does global exception handling improve API consistency?**
By implementing a global `HttpExceptionFilter`, the application guarantees that no matter where an error occurs (whether in a controller, a service, or a validation pipe), the client will always receive a standardized error response format. This predictability is crucial for frontend and mobile developers who need to parse and handle these errors gracefully.

**What is the difference between a logging interceptor and an exception filter?**
An Interceptor intercepts the normal request/response lifecycle. It is perfect for logging incoming requests, measuring request execution time, and transforming successful responses. An Exception Filter, on the other hand, only triggers when an error is thrown, taking control to handle the failure and format the outgoing HTTP error response.

**How can logs be structured to provide useful debugging information?**
Useful structured logs should include contextual metadata instead of just plain text messages. This includes the HTTP method, the request URL, the HTTP status code, timestamps, the user ID (if the request is authenticated), and a unique trace ID so that a single request can be tracked across multiple microservices.