# Reflection: API Debugging with Bruno

- Bruno is like Postman but simpler and works offline. Unlike cURL, it has a nice UI, so I don’t have to type long commands.

- To send an authenticated request in Bruno, I add an Authorization header and pass a Bearer token. If using Auth0, I get the token from their dashboard or login flow.

- Organizing API requests in collections helps keep things neat. I can group endpoints by feature (e.g., "Users," "Auth," "Orders") and easily rerun tests.

- For a NestJS backend, I’d structure the collection with folders for different modules (e.g., `Auth`, `Users`, `Products`). Each folder has GET, POST, PUT, DELETE requests for that module.

![Image](https://github.com/user-attachments/assets/0af2fe2c-e501-4e08-b483-e61a1e27d878)

![Image](https://github.com/user-attachments/assets/fe6ba49a-011a-432b-be6f-21d1b473944f)
