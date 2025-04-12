# Test Coverage and Assertions

## 1. What does the coverage bar track, and why is it important?

The coverage bar tracks how much of your code is tested by tests. It shows the percentage of lines, functions, and branches covered by tests. It's important because it helps make sure your code works well and reduces bugs.

## 2. Why does Focus Bear enforce a minimum test coverage threshold?

Focus Bear enforces a minimum test coverage threshold (like 80%) to ensure that most of the code is tested before it’s deployed. This helps catch bugs early and keeps the code quality high.

## 3. How can high test coverage still lead to untested functionality?

High test coverage can still miss important functionality if the tests don't actually check if the code works as expected. Sometimes, tests are written just to cover code lines but don't verify the actual behavior, leaving some bugs hidden.

## 4. What are examples of weak vs. strong test assertions?

- **Weak Assertions:**
    - Just checking if something exists:
      ```javascript
      expect(result).toBeDefined();
      ```
      This only checks that something is there, but doesn’t say if it’s correct.

- **Strong Assertions:**
    - Checking if the result is exactly what you expect:
      ```javascript
      expect(result).toBe(5);  // checks the exact value
      expect(result).toEqual({ id: 1, name: 'John' });  // checks object structure and values
      ```
      These assertions make sure the code actually does what it’s supposed to do.

## 5. How can you balance increasing coverage with writing effective tests?

- I don’t just aim for high coverage. I focus on writing tests that check the behavior of the code.
- I write tests that actually check if things work, not just if they run.
- I test edge cases (unusual or unexpected inputs) to cover more scenarios.
- If I have weak tests, I refactor them to check for correct behavior, not just execution.

![Screenshot 2025-03-26 215734](https://github.com/user-attachments/assets/631b7d6a-8f3a-4e2f-a83c-51b6da07dce7)

