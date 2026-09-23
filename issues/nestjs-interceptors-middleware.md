# Using Interceptors & Middleware in NestJS Reflection

**What is the difference between an interceptor and middleware in NestJS?**
Middleware runs at the very beginning of the request lifecycle (at the underlying Express/Fastify level) before any Guards, Pipes, or Interceptors are evaluated. It is unaware of the NestJS execution context. Interceptors, however, are deeply integrated into the NestJS lifecycle. They execute after middleware and guards, wrapping the route handler. Because they use RxJS Observables, interceptors can access the execution context, manipulate the outgoing response, or handle errors after the route has processed the request.

**When would you use an interceptor instead of middleware?**
You should use middleware for raw HTTP, cross-cutting tasks like rate-limiting, basic request logging, or setting CORS headers, as these don't need to know which specific controller method will handle the request. You should use an interceptor when you need to transform the response body (e.g., wrapping all responses in a `{ data: ... }` object), measure the exact execution time of a specific route handler, or cache responses, because interceptors have direct access to the route's returned data stream.

**How does `LoggerErrorInterceptor` help?**
In the context of robust logging (like using `nestjs-pino`), the `LoggerErrorInterceptor` helps by automatically catching exceptions that are thrown during the request lifecycle. Instead of letting the error silently fall through to the global exception filter (which only formats the HTTP response), this interceptor ensures that the full error details, including stack traces and context metadata, are properly recorded in the application logs for debugging and monitoring purposes.