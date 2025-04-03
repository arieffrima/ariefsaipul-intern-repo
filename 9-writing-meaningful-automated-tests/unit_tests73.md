# Reflection - Unit Tests

## Why is it important to mock API calls in tests?  
- Avoids making real network requests, so tests run faster and don’t depend on external services  
- Prevents hitting API rate limits or getting unexpected failures due to API issues  
- Helps test different responses like success, failure, or timeouts without actually calling the API  
- Keeps tests isolated and reliable  

## Common pitfalls when testing asynchronous code  
- Not awaiting promises, so tests might pass before the async task finishes  
- Incorrectly mocking functions, which can cause unexpected errors  
- Flaky tests due to race conditions or unexpected delays  
- Using setTimeout or waiting for real delays, making tests slow and unreliable  
- Forgetting to handle promise rejections, leading to misleading test failures  
![Screenshot 2025-03-28 070846](https://github.com/user-attachments/assets/0a2b2aea-567b-402b-aed7-e3228fc187d9)
