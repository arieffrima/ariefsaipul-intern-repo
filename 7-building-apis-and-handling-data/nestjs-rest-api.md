# Reflection: NestJS REST API

## 1. What is the role of a controller in NestJS?

In NestJS, a **controller** is responsible for handling incoming requests and returning responses to the client. Controllers are the entry point for incoming requests, and they map HTTP requests (GET, POST, PUT, DELETE, etc.) to specific methods within the controller. The controller is like the "interface" of your application that directly interacts with the client-side. 

In my journey, I created the `UsersController`, which handles requests like creating a new user with the `POST` method or fetching all users with the `GET` method. The controller is focused on routing and delegating business logic to the service layer, keeping it clean and focused only on handling requests and responses.

## 2. How should business logic be separated from the controller?

Business logic should not be placed inside the controller. Controllers should only handle the routing and communication with the client, while the actual business logic, like database operations or complex calculations, should be handled in **services**.

In my journey, I created the `UsersService` to handle the business logic related to user creation, data validation, and management. This helps to keep the controller clean and focused on request handling, ensuring that the application is more maintainable and scalable in the long term.

## 3. Why is it important to use services instead of handling logic inside controllers?

Using **services** instead of handling logic inside controllers provides several benefits:

- **Separation of concerns**: By delegating business logic to services, controllers can focus on routing and handling HTTP requests. This keeps the code more modular and easier to maintain.
- **Reusability**: Services can be reused across different controllers or other parts of the application. For example, I can inject `UsersService` into other controllers if needed.
- **Testability**: Services are easier to test since they can be isolated from the controller’s HTTP request/response cycle. This improves the unit testing process by allowing business logic to be tested independently from the request-handling code.
- **Cleaner code**: The controller remains clean and focused on handling routes, reducing clutter and improving code readability.

In my case, placing the logic for creating, updating, and deleting users in the `UsersService` rather than the `UsersController` ensures that the controller only delegates responsibilities and doesn't become bloated with unnecessary business logic.

## 4. How does NestJS automatically map request methods (GET, POST, etc.) to handlers?

NestJS uses **decorators** to map HTTP request methods to specific controller methods. For example:

- `@Get()`: Maps to the HTTP GET method.
- `@Post()`: Maps to the HTTP POST method.
- `@Put()`: Maps to the HTTP PUT method.
- `@Delete()`: Maps to the HTTP DELETE method.

These decorators are used in the controller methods to define how each method should handle a particular HTTP request. For instance, in my `UsersController`, I used the `@Post()` decorator to handle the creation of a new user and the `@Get()` decorator to fetch all users. NestJS automatically takes care of routing and mapping the requests to these methods based on the URL and HTTP method.

Example:
```typescript
@Controller('users')
export class UsersController {
  @Post()
  create(@Body(new ValidationPipe()) createUserDto: CreateUserDto) {
    return this.usersService.create(createUserDto);
  }

  @Get()
  findAll() {
    return this.usersService.findAll();
  }
}
```
![Screenshot 2025-03-17 154837](https://github.com/user-attachments/assets/004665bf-cb41-4802-b9fa-afdb0b1b04ce)

#### Here's the detail : [https://github.com/arieffrima/my-nestjs-project](https://github.com/arieffrima/arief-nestjs/tree/feature)
