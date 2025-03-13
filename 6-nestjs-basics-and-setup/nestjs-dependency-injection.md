### 1. **How Does Dependency Injection Improve Maintainability?**
   - **Decoupling**: Reduces dependencies between components, making the system easier to understand, test, and modify.
   - **Testability**: Makes it easier to mock or replace components for unit testing.
   - **Flexibility and Reusability**: Allows easy replacement of implementations without changing consuming components.
   - **Consistency**: Ensures consistent injection of dependencies throughout the application.
   - **Centralized Management**: All dependencies are managed in one place by the DI container.

### 2. **What is the Purpose of the `@Injectable()` Decorator?**
   - Marks a class as a provider that can be injected into other classes through DI.
   - Tells NestJS that the class can be managed, instantiated, and injected as a dependency.

### 3. **What Are the Different Types of Provider Scopes, and When Would You Use Each?**
   - **SINGLETON**: Default scope; a single instance is shared across the entire application. Use for stateless services.
   - **REQUEST**: A new instance for each HTTP request. Use for request-specific data like user sessions.
   - **TRANSIENT**: A new instance for each injection. Use when you need a fresh instance every time.

### 4. **How Does NestJS Automatically Resolve Dependencies?**
   - **Dependency Resolution**: NestJS checks the constructor parameters to resolve and inject required dependencies.
   - **Automatic Injection**: Automatically instantiates and injects the required dependencies.
   - **Provider Registration**: Providers must be registered in the module’s `providers` array for DI to resolve them.
