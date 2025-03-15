# Common Code Smells & Their Impact

## Magic Numbers & Strings

**Problem:** Hardcoded values make code unclear and difficult to modify.  
**Solution:** Use named constants or enums.

### **Bad Example:**

```typescript
@Injectable()
export class UserService {
  createUser(userType: string) {
    if (userType === "admin") {
      return { role: "admin", permissions: ["ALL"] };
    } else if (userType === "user") {
      return { role: "user", permissions: ["READ"] };
    }
  }
}
```

### **Refactored Using Constants:**

```typescript
const USER_TYPES = {
  ADMIN: "admin",
  USER: "user",
};

const PERMISSIONS = {
  ADMIN: ["ALL"],
  USER: ["READ"],
};

@Injectable()
export class UserService {
  createUser(userType: string) {
    return { role: userType, permissions: PERMISSIONS[userType] || [] };
  }
}
```

---

## Long Functions

**Problem:** Hard to understand, debug, and maintain.  
**Solution:** Break into smaller, more focused functions.

### **Bad Example:**

```typescript
@Injectable()
export class OrderService {
  processOrder(order: any) {
    let total = 0;
    order.items.forEach((item) => {
      total += item.price * item.quantity;
    });

    if (order.discount) {
      total -= total * order.discount;
    }

    if (order.customer.isPremium) {
      total -= total * 0.1;
    }

    console.log(`Order Total: ${total}`);
  }
}
```

### **Refactored - Split into Smaller Functions:**

```typescript
@Injectable()
export class OrderService {
  // Calculates the total price of all items in the order
  private calculateTotal(order: Order): number {
    return order.items.reduce(
      (sum, item) => sum + item.price * item.quantity,
      0
    );
  }

  // Applies a general discount to the total price
  private applyDiscount(total: number, discount: Discount): number {
    return discount ? total - total * discount.value : total;
  }

  // Applies a premium discount if the customer is a premium member
  private applyPremiumDiscount(total: number, customer: Customer): number {
    return customer.isPremium ? total - total * 0.1 : total;
  }

  // Main function to process the order and calculate the total
  processOrder(order: Order) {
    let total = this.calculateTotal(order);
    total = this.applyDiscount(total, order.discount);
    total = this.applyPremiumDiscount(total, order.customer);

    console.log(`Order Total: ${total}`);
  }
}

// Interfaces to define the structure of the order and related data
interface Item {
  price: number;
  quantity: number;
}

interface Discount {
  value: number;
}

interface Customer {
  isPremium: boolean;
}

interface Order {
  items: Item[];
  discount: Discount;
  customer: Customer;
}
```

---

## Duplicate Code

**Problem:** Increases maintenance effort and potential for bugs.  
**Solution:** Extract repeated logic into reusable functions.

### **Bad Example:**

```typescript
@Injectable()
export class AuthService {
  loginAdmin(user: any) {
    if (user.username === "admin" && user.password === "admin123") {
      return { status: "success", role: "admin" };
    }
    return { status: "failed" };
  }

  loginUser(user: any) {
    if (user.username === "user" && user.password === "user123") {
      return { status: "success", role: "user" };
    }
    return { status: "failed" };
  }
}
```

### **Refactored - Single Function:**

```typescript
import { Injectable } from "@nestjs/common";
import { InjectRepository } from "@nestjs/typeorm";
import { Repository } from "typeorm";
import { User } from "./user.entity";
import { JwtService } from "@nestjs/jwt";
import * as bcrypt from "bcrypt";

@Injectable()
export class AuthService {
  constructor(
    @InjectRepository(User)
    private userRepository: Repository<User>,
    private jwtService: JwtService
  ) {}

  async validateUser(username: string, password: string): Promise<any> {
    const user = await this.userRepository.findOne({ where: { username } });
    if (user && (await bcrypt.compare(password, user.password))) {
      const { password, ...result } = user; // Don't return the password
      return result;
    }
    return null;
  }

  async login(user: any) {
    const payload = { username: user.username, sub: user.userId };
    return {
      access_token: this.jwtService.sign(payload),
    };
  }
}
```

---

## Large Classes (God Objects)

**Problem:** A single class handling too much logic violates the Single Responsibility Principle (SRP).  
**Solution:** Break into multiple smaller, focused classes.

### **Bad Example:**

```typescript
@Injectable()
export class OrderService {
  processPayment(order: any) {
    /* payment logic */
  }
  generateInvoice(order: any) {
    /* invoice logic */
  }
  sendEmailNotification(order: any) {
    /* email logic */
  }
}
```

### **Refactored - Separate Services:**

```typescript
@Injectable()
export class PaymentService {
  processPayment(order: any) {
    /* payment logic */
  }
}

@Injectable()
export class InvoiceService {
  generateInvoice(order: any) {
    /* invoice logic */
  }
}

@Injectable()
export class NotificationService {
  sendEmailNotification(order: any) {
    /* email logic */
  }
}
```

---

## Deeply Nested Conditionals

**Problem:** Makes code harder to read and debug.  
**Solution:** Use early returns, guard clauses, or refactor to design patterns.

### **Bad Example:**

```typescript
@Injectable()
export class AccessService {
  checkAccess(user: any) {
    if (user) {
      if (user.isActive) {
        if (user.hasSubscription) {
          if (user.subscription.isValid()) {
            return "Access Granted";
          }
        }
      }
    }
    return "Access Denied";
  }
}
```

### **Refactored - Use Early Returns & Guard Clauses:**

```typescript
@Injectable()
export class AccessService {
  checkAccess(user: any) {
    if (
      !user ||
      !user.isActive ||
      !user.hasSubscription ||
      !user.subscription.isValid()
    ) {
      return "Access Denied";
    }
    return "Access Granted";
  }
}
```

---

# Code Smells Reflection

## What Code Smells Did I Find?

- Found several instances of magic numbers, deeply nested conditionals, and long functions.
- Also noticed some duplicate code and inconsistent naming conventions.

## How Did Refactoring Help?

- Breaking long functions into smaller ones improved readability.
- Replacing magic numbers with constants made the code clearer.
- Removing deeply nested conditionals reduced complexity.

## How Can Avoiding Code Smells Help with Debugging?

- Clean code makes it easier to trace issues.
- Consistent naming prevents confusion when reading code.
- Reusable functions reduce the chances of introducing bugs.
