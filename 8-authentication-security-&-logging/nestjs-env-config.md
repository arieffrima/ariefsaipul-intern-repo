### How does @nestjs/config help manage environment variables?

`@nestjs/config` makes it easy for me to manage environment variables. It loads them from a `.env` file and lets me access them anywhere in the app using `ConfigService`.

### Why should secrets (e.g., API keys, database passwords) never be stored in source code?

Secrets should never be in the source code because if the code is shared or made public, those secrets can be exposed. Hackers could use them to access my database or APIs.

### How can you validate environment variables before the app starts?

I can validate environment variables by creating a DTO and using `class-validator`. This checks that the variables are correct before the app even starts running.

### How can you separate configuration for different environments (e.g., local vs. production)?

I can use different `.env` files for each environment, like `.env.local` for local and `.env.production` for production. Then, I can load the right one depending on the environment my app is running in.
