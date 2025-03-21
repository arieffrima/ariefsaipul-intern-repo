# Reflections on Breaking Down Functions

## Why is breaking down functions beneficial?

Breaking down functions into smaller, single-purpose functions is beneficial for several reasons:

- **Improved Readability**: Smaller functions are easier to read and understand. Each function performs a well-defined task, making it clear what the code is doing.
- **Reusability**: Smaller, focused functions can be reused in different parts of the application without duplicating code.
- **Testability**: Testing smaller functions becomes easier, as each function does one thing. This allows for more focused unit tests.
- **Maintainability**: With smaller functions, it's easier to make changes without affecting the entire codebase. If a change is required, you can focus on a specific function rather than modifying a large, complex block of code.
- **Debugging**: Isolating functionality into smaller functions makes it easier to identify bugs because each function is more self-contained.

## How did refactoring improve the structure of the code?

Refactoring the `processOrder` function into smaller, focused functions improved the structure by:

- **Simplifying the logic**: Each function now does one thing, which reduces complexity and makes the overall logic easier to follow.
- **Separation of concerns**: Each function has a clear responsibility, and the refactoring ensures that tasks like calculating totals, applying discounts, and updating orders are separated and more manageable.
- **Improved maintainability**: Smaller functions are easier to modify or extend in the future, without breaking the logic of other tasks.
- **Easier testing**: Each smaller function is easier to unit test, ensuring that the logic is correct in isolation.

## Long and Complex Code:

```javascript
function processOrder(order) {
  if (!order.isValid) {
    throw new Error("Invalid order");
  }

  const discount = order.amount > 100 ? 0.1 : 0.05;
  const finalAmount = order.amount - order.amount * discount;

  let shippingCost = 0;
  if (order.isExpress) {
    shippingCost = 20;
  } else if (order.isOverseas) {
    shippingCost = 50;
  } else {
    shippingCost = 10;
  }

  const totalAmount = finalAmount + shippingCost;

  if (order.paymentMethod === "credit") {
    // apply additional processing for credit payment
    console.log("Processing credit payment...");
  } else {
    // apply different processing for other payment methods
    console.log("Processing non-credit payment...");
  }

  return {
    finalAmount: totalAmount,
    discount: discount,
    shippingCost: shippingCost,
  };
}
```

## Refactor multiple smaller functions with clear responsibilities:

```javascript
const HIGH_AMOUNT_THRESHOLD = 100;
const HIGH_DISCOUNT_RATE = 0.1;
const LOW_DISCOUNT_RATE = 0.05;

const EXPRESS_SHIPPING_COST = 20;
const OVERSEAS_SHIPPING_COST = 50;
const STANDARD_SHIPPING_COST = 10;

const PAYMENT_METHODS = {
  CREDIT: "credit",
  NON_CREDIT: "non-credit",
};

function validateOrder(order) {
  if (!order.isValid) {
    throw new Error("Invalid order");
  }
}

function calculateDiscount(order) {
  return order.amount > HIGH_AMOUNT_THRESHOLD ? HIGH_DISCOUNT_RATE : LOW_DISCOUNT_RATE;
}

function calculateFinalAmount(order, discount) {
  return order.amount - order.amount * discount;
}

function calculateShippingCost(order) {
  if (order.isExpress) {
    return EXPRESS_SHIPPING_COST;
  } else if (order.isOverseas) {
    return OVERSEAS_SHIPPING_COST;
  } else {
    return STANDARD_SHIPPING_COST;
  }
}

function processPayment(order) {
  if (order.paymentMethod === PAYMENT_METHODS.CREDIT) {
    console.log("Processing credit payment...");
  } else {
    console.log("Processing non-credit payment...");
  }
}

function processOrder(order) {
  validateOrder(order);
  const discount = calculateDiscount(order);
  const finalAmount = calculateFinalAmount(order, discount);
  const shippingCost = calculateShippingCost(order);
  processPayment(order);

  const totalAmount = finalAmount + shippingCost;

  return {
    finalAmount: totalAmount,
    discount: discount,
    shippingCost: shippingCost,
  };
}
```
