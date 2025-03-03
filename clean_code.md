# Clean Code Principles

## Simplicity – Keep Code as Simple as Possible

Simplicity is key to writing clean code. The goal is to minimize complexity by avoiding over-engineering or adding unnecessary features. Code should be easy to understand and accomplish only what is needed, without complicating things unnecessarily. Simple code is easier to maintain, debug, and extend.

## Readability – Code Should Be Easy to Understand

Code is often read more than written, so making it readable is essential. This means using meaningful variable names, adding comments where necessary, and structuring code in a way that is easy to follow. Readable code improves collaboration and helps future developers (or even yourself) understand the logic quickly.

## Maintainability – Future Developers (Including You!) Should Be Able to Work with the Code Easily

Maintainability is the ability to modify or extend the code without introducing bugs or breaking functionality. Clean code is modular, with clearly defined responsibilities and well-organized functions, so changes can be made safely and efficiently.

## Consistency – Follow Style Guides and Project Conventions

Consistency is crucial in a collaborative environment. Following established coding conventions and style guides ensures that all team members write code in a similar manner. This includes naming conventions, indentation, and function organization, among other things. Consistent code improves readability and reduces confusion.

## Efficiency – Write Performant, Optimized Code Without Premature Over-Engineering

Efficiency means writing code that is performant but also balanced. While it's important to optimize for performance, it's crucial not to prematurely over-engineer the solution. Focus on clear, simple code first, and only optimize when necessary (for instance, when profiling indicates performance issues).

## Messy Code Example

import { Injectable } from '@nestjs/common';

@Injectable()
export class UserService {
private users = [
{ id: 1, email: 'user1@example.com' },
{ id: 2, email: 'user2@example.com' },
{ id: 3, email: 'user1@example.com' },
{ id: 4, email: 'user4@example.com' },
];

findDuplicateEmails() {
const duplicateEmails = [];
for (let i = 0; i < this.users.length; i++) {
for (let j = i + 1; j < this.users.length; j++) {
if (this.users[i].email === this.users[j].email) {
duplicateEmails.push(this.users[i].email);
}
}
}
return duplicateEmails;
}
}
This is Messy because:

- Nested loops are used to compare each user’s email with every other email, making it inefficient.
- Adding duplicates to the array inside the loop could result in the same email being added multiple times if more than two users share the same email.
- Code readability is lower due to nested logic, and it’s harder to maintain.

## Clean Code Example

import { Injectable } from '@nestjs/common';

@Injectable()
export class UserService {
private users = [
{ id: 1, email: 'user1@example.com' },
{ id: 2, email: 'user2@example.com' },
{ id: 3, email: 'user1@example.com' },
{ id: 4, email: 'user4@example.com' },
];

findDuplicateEmails() {
const seenEmails = new Set();
const duplicateEmails = new Set();

    this.users.forEach((user) => {
      if (seenEmails.has(user.email)) {
        duplicateEmails.add(user.email);
      } else {
        seenEmails.add(user.email);
      }
    });

    return Array.from(duplicateEmails);

}
}

This is Clean because:

- No nested loops: We use a single loop to iterate through the users and check for duplicates efficiently.
- Sets are used to track seen emails and duplicates, ensuring each email is only added once.
- Improved readability: The logic is clear and easy to follow, and the variable names are meaningful.
- Performance: Checking membership in a set is O(1), making it more efficient than using an array.

Arief Saipul
