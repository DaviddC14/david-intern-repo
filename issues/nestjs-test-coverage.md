# NestJS Test Coverage Reflection

**What does the coverage bar track, and why is it important?**
The coverage bar tracks the percentage of statements, branches, functions, and lines of code executed during the automated test suite. It is important because it highlights untested code paths, ensuring that developers don't accidentally ship unverified logic to production.

**Why does Focus Bear enforce a minimum test coverage threshold?**
Focus Bear enforces a minimum 80% coverage threshold to maintain a high standard of code quality, prevent regressions when new features are added, and ensure that the application's core functionality remains stable and reliable for all users.

**How can high test coverage still lead to untested functionality?**
High coverage simply means the code was executed during a test, not that the output was actually verified. If a developer runs a function but fails to write assertions checking the returned data or side effects, the test will pass (and coverage will increase) even if the function is fundamentally broken.

**What are examples of weak vs. strong test assertions?**
A weak assertion just checks if something exists, like `expect(response).toBeDefined();` or `expect(response).toBeTruthy();`. A strong assertion checks specific behaviors and data integrity, such as `expect(response.status).toBe(201);` and `expect(response.body.email).toBe('test@example.com');`.

**How can you balance increasing coverage with writing effective tests?**
I can balance this by focusing on testing actual behavior and business logic rather than just writing tests to hit a specific line of code. Instead of artificially inflating the coverage number, I will write tests that verify positive outcomes, negative outcomes, and edge cases.