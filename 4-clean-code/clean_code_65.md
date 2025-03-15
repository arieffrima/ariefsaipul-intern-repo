## When should you add comments?

When the code has a complex or non-obvious logic that may not be immediately clear to other developers or even to your future self. Comments are helpful for explaining:

1. The **"why"** behind a certain decision, especially when the code's purpose or approach may not be apparent at first glance.
2. Any **workarounds**, **complex algorithms**, or **edge cases** that need to be clarified for future maintenance.
3. The **purpose** of functions, especially in larger projects where it's not always clear what each function does from just its name.

## When should you avoid comments and instead improve the code?

should avoid comments when:

1. The code is self-explanatory: If the code is clear and readable, there’s no need to add a comment. In such cases, focus on improving the code itself to make it more understandable.
2. The comment simply describes the code: Avoid writing comments that restate what the code is doing, e.g., "increment x" for `x++`.
3. The code can be improved for clarity: If the logic is complex or hard to understand, consider refactoring the code to make it clearer, instead of relying on comments to explain it. This often leads to more maintainable and readable code.

By following these principles, you can ensure that your comments are meaningful and truly add value to the codebase, instead of cluttering it with unnecessary or redundant information.

## example of poorly commented code:

```
function calculateTotal(price, tax) {
    // Calculate the tax
    const taxAmount = price * tax;
    // Calculate the total price including tax
    const total = price + taxAmount;
    return total;
}
```

- the comment is not clearly / do not give the specific information

## more useful:

```
function calculateTotal(price, tax, location) {
    // // Sales tax is only calculated for residents of Wyoming due to state-specific regulations

    if (location === 'Wyoming') {
        const taxAmount = price * tax;
        // Add the calculated tax amount to the price to get the total amount
        const total = price + taxAmount;
        return total;
    }
    // No tax is applied if the location is not Wyoming
    return price;
}

```

- the comment clearly and give the information about "why" not "what"
