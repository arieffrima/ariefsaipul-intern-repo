# Reflections on Unit Testing

### How do unit tests help keep code clean?

- Unit tests help catch issues before they make it to production, reducing the amount of time spent fixing bugs later.
- Writing unit tests encourages developers to break code into smaller, manageable pieces, which makes it easier to understand and maintain.
- Unit tests act as documentation for future developers, showing how functions and components are expected to behave.
- With tests in place, it's easier to refactor code without the fear of breaking existing functionality, ensuring that the code remains efficient and clean.

### What issues did you find while testing?

- The initial issue was that the `"test"` script was not recognized, which was caused by a formatting issue in the `package.json` file.
- While running Jest, a warning appeared suggesting that I should enable `"esModuleInterop": true` in the `tsconfig.json` to avoid issues with module imports.
- Some required dependencies, like Jest and related packages, were not installed correctly, so they had to be added before tests could run successfully.
