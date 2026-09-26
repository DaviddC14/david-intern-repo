# What is NestJS? (Framework Overview) Reflection

**What are the key differences between NestJS and Express.js?**
Express.js is a minimalist, unopinionated web framework that leaves architectural decisions entirely up to the developer, which can lead to messy codebases in large projects. NestJS, while typically using Express under the hood, is a highly opinionated framework. It provides a strict, Angular-inspired architecture out-of-the-box, enforcing the use of Modules, Controllers, and Services to ensure the codebase remains scalable, organized, and maintainable.

**Why does NestJS use decorators extensively?**
NestJS uses decorators (like `@Controller()`, `@Get()`, or `@Injectable()`) to attach metadata to classes, methods, and properties. This declarative approach allows the framework's internal execution context to gracefully handle complex tasks—such as routing HTTP requests, enforcing validation pipes, or resolving dependency injection—without cluttering the developer's business logic with repetitive boilerplate code.

**How does NestJS handle dependency injection?**
NestJS has a built-in Inversion of Control (IoC) container. When a class is marked with the `@Injectable()` decorator, it is registered as a "Provider." When another class (such as a Controller) declares that provider in its constructor, the IoC container automatically instantiates the dependency (or reuses a singleton) and injects it. This decouples object creation from usage, making the application highly modular and easy to test.

**What benefits does modular architecture provide in a large-scale app?**
A modular architecture divides a large-scale application into distinct, self-contained domains (e.g., an `AuthModule`, a `UsersModule`, a `TasksModule`). This explicit separation of concerns prevents tightly coupled "spaghetti code." It allows different teams to work on separate features simultaneously without conflicts, simplifies debugging, and paves the way for easily extracting modules into independent microservices if the application scales up in the future.