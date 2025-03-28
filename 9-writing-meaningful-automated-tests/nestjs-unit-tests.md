# Reflection: Unit Testing in NestJS

### Why is it important to test services separately from controllers?

Testing services separately is key because services have the core logic, while controllers just handle requests. If you test them together, it’s harder to spot where the issue is. Testing services alone helps focus on the actual logic.

### How does mocking dependencies improve unit testing?

Mocking dependencies helps you isolate the unit you're testing. Without mocks, tests would interact with real services or databases, making things slower and unpredictable. Mocks let you focus on testing just the unit, making things quicker and more reliable.

### What are common pitfalls when writing unit tests in NestJS?

- Not mocking dependencies properly, which makes tests slower and harder to control.
- Forgetting edge cases, like testing with invalid or weird inputs.
- Trying to test too much in one go, making it unclear what’s actually being tested.

### How can you ensure that unit tests cover all edge cases?

- Test with invalid inputs like null, undefined, or empty values.
- Make sure to check how errors are handled.
- Use TDD (test-driven development) to think of edge cases before writing the code.

![Screenshot 2025-03-25 161607](https://github.com/user-attachments/assets/f088f962-4850-4c58-98e8-069263e04861)
