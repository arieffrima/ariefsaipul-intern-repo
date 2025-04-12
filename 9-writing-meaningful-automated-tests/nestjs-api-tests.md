# Reflection (nestjs-api-tests.md)

- **How does Supertest help test API endpoints?**
  Supertest lets you send requests to your API and check the responses. It’s great for testing if your API is working as expected by checking things like status codes, response data, and headers.

- **What is the difference between unit tests and API tests?**
  Unit tests check small pieces of code, like functions, on their own. API tests check if your whole API works by sending real HTTP requests and seeing if it gives the right responses.

- **Why should authentication be mocked in integration tests?**
  Mocking authentication makes tests simpler and faster. You don’t need to actually log in or deal with real authentication, so you can focus on testing the API itself.

- **How can you structure API tests to cover both success and failure cases?**
  Test both good and bad inputs. For example, check that the API works when you send the right data (success case) and that it gives errors when the data is wrong or missing (failure case).

![Image](https://github.com/user-attachments/assets/91ba15fd-e28f-4d79-8acf-1371861f59f8)
