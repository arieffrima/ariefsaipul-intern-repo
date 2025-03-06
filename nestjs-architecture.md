## **Reflection on NestJS Architecture**

### **1. What is the Purpose of a Module in NestJS?**
- Modules group related components like controllers, providers, and other modules.
- They help organize the application into logical sections.
- Modules promote scalability and maintainability by isolating different features.

### **2. How Does a Controller Differ from a Provider?**
- **Controller**: Handles incoming HTTP requests and returns responses. Defines routes and delegates logic to providers.
- **Provider**: Contains business logic and interacts with external resources (e.g., databases, APIs). It’s injected into controllers or other providers via dependency injection.

### **3. Why is Dependency Injection Useful in NestJS?**
- **Decoupling**: Reduces tight coupling between components.
- **Testability**: Makes unit testing easier by allowing mocks or substitutes.
- **Flexibility**: Enables easy swapping of implementations.
- **Scalability**: Manages complexity in larger applications through consistent service management.

### **4. How Does NestJS Ensure Modularity and Separation of Concerns?**
- **Modules**: Group related components, isolating different domains of functionality.
- **Controllers**: Handle routing and request-response cycle, delegating business logic to providers.
- **Providers**: Handle business logic and data manipulation, separate from HTTP request handling.
