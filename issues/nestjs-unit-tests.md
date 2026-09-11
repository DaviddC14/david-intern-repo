# NestJS Unit Tests Reflection

**Why is it important to test services separately from controllers?**
Separation of concerns is key. Controllers are responsible for handling HTTP routing, validating payloads, and formatting responses, while services handle the core business logic. Testing them separately ensures that if a test fails, I know exactly whether the bug is in the HTTP layer or the business logic layer.

**How does mocking dependencies improve unit testing?**
Mocking isolates the System Under Test (SUT). By mocking dependencies like databases or external APIs, unit tests execute in milliseconds, remain completely deterministic (they won't fail randomly due to network issues), and prevent accidental side effects like modifying real data.

**What are common pitfalls when writing unit tests in NestJS?**
A frequent pitfall is forgetting to provide a mock for every dependency in the `TestingModule` array, which causes NestJS to throw injection errors during test compilation. Another mistake is testing implementation details rather than the actual behavior and output of the function.

**How can you ensure that unit tests cover all edge cases?**
I can ensure robust coverage by intentionally testing negative paths and boundary conditions. This includes passing `null`, `undefined`, or malformed data to the service methods and verifying that they throw the correct expected exceptions using Jest's `expect().rejects.toThrow()`.