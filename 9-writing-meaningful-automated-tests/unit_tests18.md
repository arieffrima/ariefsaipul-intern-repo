## Reflection on Testing Redux

### What was the most challenging part of testing Redux?

The hardest part was testing actions and reducers. I had to ensure that the state updates correctly and that async actions (like `redux-thunk`) worked as expected. Mocking state properly was tricky at times too.

### How do Redux tests differ from React component tests?

Redux tests focus on state management testing if actions and reducers work properly. React component tests focus on UI behavior making sure the component renders correctly and interacts with the Redux store as expected.

![Screenshot 2025-03-22 144947](https://github.com/user-attachments/assets/3fa10649-f4c4-47ac-9587-a72eb4bcba78)
