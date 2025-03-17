

## 1. What is the purpose of pipes in NestJS?
Pipes in NestJS are used to **transform and validate** incoming data before it reaches the controller. They ensure that the request data is correctly formatted, improving security and consistency. Pipes can also modify data (e.g., converting strings to numbers) and reject invalid requests, making API handling more robust.

## 2. How does `ValidationPipe` improve API security and data integrity?
`ValidationPipe` enhances API security and data integrity by:
- **Ensuring valid input** → Automatically checks if incoming data meets the defined constraints in the DTO.
- **Preventing unwanted data** → With `whitelist: true`, extra fields that are not part of the DTO are removed.
- **Rejecting bad requests** → With `forbidNonWhitelisted: true`, requests with unrecognized fields are blocked.
- **Converting data types** → With `transform: true`, it converts request payloads into properly typed DTO instances.

This prevents invalid or malicious data from reaching the service layer, reducing security risks and potential errors.

## 3. What is the difference between built-in and custom pipes?
- **Built-in Pipes** → Provided by NestJS, such as:
  - `ValidationPipe` (for validating DTOs)
  - `ParseIntPipe` (for converting strings to numbers)
  - `ParseBoolPipe`, `ParseUUIDPipe`, etc.
- **Custom Pipes** → User-defined pipes that allow specific validation or transformation logic.
  - Example: A pipe that trims strings or checks if a number falls within a specific range.
  - Custom pipes implement the `PipeTransform` interface to define custom logic.

## 4. How do decorators like `@IsString()` and `@IsNumber()` work with DTOs?
Decorators from `class-validator` define validation rules for DTO properties. When `ValidationPipe` is enabled, NestJS checks incoming data against these rules:
- `@IsString()` → Ensures the property is a valid string.
- `@IsEmail()` → Validates if a string is a properly formatted email.
- `@IsInt()` → Ensures the property is an integer.
- `@Min(18)` / `@Max(100)` → Enforces numeric range constraints.

For example, in the `CreateUserDto`:

```typescript
export class CreateUserDto {
  @IsString()
  name: string;

  @IsEmail()
  email: string;

  @IsInt()
  @Min(18)
  @Max(100)
  age: number;
}
```
![Screenshot 2025-03-17 161323](https://github.com/user-attachments/assets/fe471ffc-3d40-4dd8-a111-cb1a89abb1aa)

#### More Details  - [https://github.com/arieffrima/my-nestjs-project](https://github.com/arieffrima/arief-nestjs)
