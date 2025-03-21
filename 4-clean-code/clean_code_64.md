# Reflection on Refactoring for Simplicity

## What made the original code complex?

The original code was complex due to several reasons:

1. **Nested Conditions**: The code applied multiple discount checks sequentially, which made it harder to follow. It was unclear how the discounts were applied in relation to one another.
2. **Repeated Logic**: The logic for applying different discounts was repeated in multiple places, which added unnecessary complexity.
3. **Lack of Modularity**: All the logic was bundled into a single function, making it difficult to understand and maintain.

## How did refactoring improve it?

The refactored version is much simpler:

1. **Modularity**: By breaking the code into smaller, single-purpose functions, each function now has a clear responsibility, making the overall code easier to understand and maintain.
2. **Reduced Complexity**: The logic for applying each discount is now contained in a separate function, which makes the flow of applying discounts more straightforward and easy to follow.
3. **Improved Readability**: The new structure is more readable, with descriptive function names that explain what each part of the code does. The overall process is clearer and easier to maintain.

Refactoring the code for simplicity makes it more maintainable, reusable, and less error-prone, while also improving readability for future developers.

## complicated code:

```javascript
function calculateDiscountedPrice(price, discount, isPremiumCustomer, hasVoucher) {
let finalPrice = applyDiscount(price, discount);
finalPrice = applyPremiumDiscount(finalPrice, isPremiumCustomer);
finalPrice = applyVoucherDiscount(finalPrice, hasVoucher);

    return Math.max(finalPrice, 0); // Ensure price doesn't go below zero

}

function applyDiscount(price, discount) {
return discount > 0 ? price - (price \* discount) : price;
}

function applyPremiumDiscount(price, isPremiumCustomer) {
return isPremiumCustomer ? price - (price \* 0.1) : price;
}

function applyVoucherDiscount(price, hasVoucher) {
return hasVoucher ? price - 20 : price;
}
```

- some of discount applied in confused lists
- Too much checked conditions

## more readable:

```javascript
function calculateDiscountedPrice(price, discount, isPremiumCustomer, hasVoucher) {
let finalPrice = applyDiscount(price, discount);
finalPrice = applyPremiumDiscount(finalPrice, isPremiumCustomer);
finalPrice = applyVoucherDiscount(finalPrice, hasVoucher);

    return Math.max(finalPrice, 0); // Ensure price doesn't go below zero

}

function applyDiscount(price, discount) {
return discount > 0 ? price - price * discount : price;
}

function applyPremiumDiscount(price, isPremiumCustomer) {
return isPremiumCustomer ? price - price * 0.1 : price;
}

function applyVoucherDiscount(price, hasVoucher) {
return hasVoucher ? price - 20 : price;
}
```

- Simple and easy to understand
- separate function
