# NestJS API Tests Reflection

**How does Supertest help test API endpoints?**
Supertest allows us to simulate HTTP requests (GET, POST, PUT, DELETE) against our NestJS application without needing to start a live server on a physical network port. It hooks directly into the NestJS instance and provides built-in assertions to easily verify HTTP status codes, headers, and JSON body payloads.

**What is the difference between unit tests and API tests?**
Unit tests isolate a single function or class (like a specific Service method) by mocking all of its external dependencies to ensure the logic works in a vacuum. API tests (or e2e integration tests) evaluate the entire request lifecycle—starting from the route handler in the Controller, passing through validation pipes, hitting the Service layer, and returning the final HTTP response.

**Why should authentication be mocked in integration tests?**
Hitting a real authentication server (like Auth0 or a live database) during tests makes the test suite slow, brittle, and prone to network timeouts or rate limits. Mocking authentication allows us to reliably and quickly simulate different user roles and permissions without relying on external systems.

**How can you structure API tests to cover both success and failure cases?**
I structure my tests by grouping them within a `describe()` block for a specific endpoint (e.g., `describe('/users (POST)')`). Inside, I write one `it()` block for the "happy path" (expecting a 201 Created when passing valid data) and several separate `it()` blocks for negative paths, such as expecting a 400 Bad Request for missing data, or a 401 Unauthorized when a token is missing.