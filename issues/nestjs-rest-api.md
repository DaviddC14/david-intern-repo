# Creating REST APIs with NestJS Reflection

**What is the role of a controller in NestJS?**
In NestJS, a controller's sole responsibility is to handle incoming HTTP requests and return responses to the client. It acts as a routing mechanism that receives a specific request (like a GET or POST), extracts any necessary data from the request (such as body payloads, URL parameters, or query strings), and delegates the actual processing of that data to a provider (a Service).

**How should business logic be separated from the controller?**
Business logic should be entirely abstracted away into Services (Providers). Controllers should remain "thin," meaning they only contain the logic required to route the request and return the correct HTTP status code. The actual heavy lifting—such as database interactions, complex calculations, or third-party API calls—should happen strictly inside the injected Service classes.

**Why is it important to use services instead of handling logic inside controllers?**
Delegating logic to services promotes the Single Responsibility Principle, making the codebase highly modular and maintainable. It drastically improves reusability, as a single Service method (like `verifyUser()`) can be injected and used across multiple different controllers. It also makes unit testing much easier, as you can test the business logic in isolation without needing to mock the entire HTTP request lifecycle.

**How does NestJS automatically map request methods (GET, POST, etc.) to handlers?**
NestJS handles routing through the use of built-in HTTP method decorators such as `@Get()`, `@Post()`, `@Put()`, `@Patch()`, and `@Delete()`. When you place one of these decorators above a method in a controller class, NestJS reads this metadata during the application bootstrap phase and automatically binds that specific class method to the underlying Express or Fastify routing engine for the corresponding HTTP verb and path.