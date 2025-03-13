# Reflection on Avoiding Code Duplication

## What were the issues with duplicated code?

Duplicated code can cause several serious issues, including:

1. Difficult Maintenance\*: If we need to change the logic or fix a bug in the duplicated code, we have to modify it a every place it appears. This increases the risk of errors and makes changes more difficult.
2. Prone to Inconsistency: Duplication increases the possibility of inconsistency. For example, if we update one copy of the code and forget to update the others, it can lead to unintended behavior or bugs.
3. Increased Code Size: Duplication also makes our code larger and harder to understand. More code means more places to check when debugging or refactoring.

## How did refactoring improve maintainability?

By cleaning up the code and eliminating duplication, we made the code more modular and organized. After refactoring, there is only one place for the logic to calculate the price after discount, making it easier to manage and update the code when needed. This reduces logical duplication and increases consistency across the project.

Moreover, well-organized and duplication-free code will be easier to read and understand, whether by other developers working on the same project or by ourselves in the future when performing maintenance or further refactoring.

## Example Bad Code:

function calculatePriceWithDiscount1(price, discount) {
return price - (price \* discount);
}

function calculatePriceWithDiscount2(price, discount) {
return price - (price \* discount);
}

function calculatePriceWithDiscount3(price, discount) {
return price - (price \* discount);
}

## Example Good Code:

function calculatePriceWithDiscount(price, discount) {
return price - (price \* discount);
}
