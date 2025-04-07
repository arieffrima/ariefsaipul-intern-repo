## Reflection - Unit Testing React Components

### What are the benefits of using React Testing Library?

It tests how the user interacts with the UI, not how the code works inside. So the tests are more reliable and easier to understand. Even if we change the code later, the tests usually still work.

### What challenges did you face when simulating user interaction?

I forgot to use await when clicking buttons, so the result didn’t show up. Sometimes the test couldn’t find the element because it didn’t render properly. Took a few tries to get it working.
