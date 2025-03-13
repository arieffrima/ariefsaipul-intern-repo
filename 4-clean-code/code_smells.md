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
  private calculateTotal(order: any): number {
    return order.items.reduce((sum, item) => sum + item.price * item.quantity, 0);
  }

  private applyDiscount(total: number, discount: number): number {
    return discount ? total - total * discount : total;
  }

  private applyPremiumDiscount(total: number, isPremium: boolean): number {
    return isPremium ? total - total * 0.1 : total;
  }

  processOrder(order: any) {
    let total = this.calculateTotal(order);
    total = this.applyDiscount(total, order.discount);
    total = this.applyPremiumDiscount(total, order.customer.isPremium);

    console.log(`Order Total: ${total}`);
  }
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
@Injectable()
export class AuthService {
  private validateUser(username: string, password: string): string | null {
    const users = {
      admin: "admin123",
      user: "user123",
    };

    return users[username] === password ? username : null;
  }

  login(user: any) {
    const role = this.validateUser(user.username, user.password);
    return role ? { status: "success", role } : { status: "failed" };
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
  processPayment(order: any) { /* payment logic */ }
  generateInvoice(order: any) { /* invoice logic */ }
  sendEmailNotification(order: any) { /* email logic */ }
}
```

### **Refactored - Separate Services:**
```typescript
@Injectable()
export class PaymentService {
  processPayment(order: any) { /* payment logic */ }
}

@Injectable()
export class InvoiceService {
  generateInvoice(order: any) { /* invoice logic */ }
}

@Injectable()
export class NotificationService {
  sendEmailNotification(order: any) { /* email logic */ }
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
    if (!user || !user.isActive || !user.hasSubscription || !user.subscription.isValid()) {
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

