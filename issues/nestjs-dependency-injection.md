# Dependency Injection in NestJS Reflection

**How does dependency injection improve maintainability?**
Dependency Injection (DI) drastically improves maintainability by decoupling the creation of an object from its actual usage. Because classes don't instantiate their own dependencies, it becomes incredibly easy to swap out implementations (e.g., swapping a real database service for a mock service during testing) without altering the consuming class. This makes the codebase modular, loosely coupled, and highly testable.

**What is the purpose of the `@Injectable()` decorator?**
The `@Injectable()` decorator is a marker that tells NestJS's Inversion of Control (IoC) container that a specific class can be managed as a "Provider." It attaches necessary metadata to the class, allowing NestJS to instantiate it and automatically resolve and inject its required dependencies when it is requested by other classes, like controllers or other services.

**What are the different types of provider scopes, and when would you use each?**
1. **DEFAULT (Singleton):** A single instance of the provider is shared across the entire application lifecycle. This is the most efficient and should be used 99% of the time.
2. **REQUEST:** A new, distinct instance of the provider is created exclusively for each incoming HTTP request and garbage-collected afterward. This is useful when the service needs to track specific request data, like the currently logged-in user's tenant ID, but it impacts performance.
3. **TRANSIENT:** A completely new instance is created every single time the provider is injected into another class, regardless of the request. Useful for stateful services where each consumer needs its own isolated instance.

**How does NestJS automatically resolve dependencies?**
NestJS uses TypeScript's reflection capabilities to inspect the types declared in a class's constructor. When the application bootstraps, the IoC container looks at the constructor parameters (e.g., `constructor(private myService: MyService)`), identifies the corresponding registered Provider in the current Module, instantiates it (if it hasn't already), and passes that exact instance into the constructor automatically.