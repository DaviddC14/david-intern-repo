# Validating Requests with Pipes in NestJS Reflection

**What is the purpose of pipes in NestJS?**
Pipes in NestJS serve two primary purposes: **Transformation** and **Validation**. They operate on the arguments being processed by a route handler. A pipe can transform input data to the desired format (e.g., converting a string parameter like `"10"` into an integer `10`) or evaluate the input data and throw an exception if it does not meet specific validation criteria, preventing the route handler from executing with bad data.

**How does `ValidationPipe` improve API security and data integrity?**
The built-in `ValidationPipe` enforces a strict contract between the client and the backend. It ensures that incoming payloads perfectly match the expected structures. By configuring it with options like `whitelist: true` and `forbidNonWhitelisted: true`, it automatically strips out malicious or unexpected properties injected by an attacker and blocks malformed requests, ensuring that the business logic only processes clean, secure data.

**What is the difference between built-in and custom pipes?**
Built-in pipes (like `ValidationPipe`, `ParseIntPipe`, or `ParseUUIDPipe`) are provided out-of-the-box by NestJS to handle the most common data transformation and validation use cases. Custom pipes are built by developers (by implementing the `PipeTransform` interface) to handle highly specific, complex, or domain-level business validation logic that standard generic pipes cannot accommodate.

**How do decorators like `@IsString()` and `@IsNumber()` work with DTOs?**
These decorators, provided by the `class-validator` package, attach metadata to the properties of a Data Transfer Object (DTO) class. When a request arrives, the `ValidationPipe` reads this metadata at runtime, inspects the incoming JSON payload, and applies the validation rules. If a property decorated with `@IsString()` receives a boolean or an array, the decorator flags it, and the pipe automatically constructs and throws an HTTP 400 Bad Request error.