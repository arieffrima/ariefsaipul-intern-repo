# NestJS Setup - Reflection

## 1. What Files Are Included in a Default NestJS Project?

A default NestJS project includes the following key files and directories:

- **`src/`**: This folder contains the main application code.
  - **`app.controller.ts`**: Contains the default controller with one route (`GET /`).
  - **`app.controller.spec.ts`**: The unit test file for the `app.controller.ts`.
  - **`app.module.ts`**: The root module that imports and configures components like controllers and services.
  - **`app.service.ts`**: Contains the business logic, which in the default setup returns a "Hello World!" message.
  - **`app.service.spec.ts`**: The unit test file for the `app.service.ts`.

- **`test/`**:
  - **`app.e2e-spec.ts`**: An end-to-end test file that tests the entire application.

- **Configuration files**:
  - **`tsconfig.json`**: TypeScript configuration file for compiling the NestJS project.
  - **`nest-cli.json`**: Configuration file for the NestJS CLI.
  - **`package.json`**: Defines the project dependencies, scripts, and other configurations.

These files and directories provide a foundation for building a modular, testable, and scalable application.

## 2. How Does `main.ts` Bootstrap a NestJS Application?

The **`main.ts`** file is the entry point for a NestJS application. It initializes and bootstraps the application by calling the `NestFactory.create()` method, which creates an instance of the NestJS application.

- **NestFactory.create()**: This method creates the application instance using the root module (usually `AppModule`). It allows it configure global settings like middleware, global filters, pipes, etc.
  
  ```typescript
  async function bootstrap() {
    const app = await NestFactory.create(AppModule);
    await app.listen(3000);
  }
  bootstrap();
