### How does Auth0 handle authentication compared to traditional username/password auth?

Auth0 doesn't store passwords like traditional methods. Instead, it uses tokens (like JWT) and lets users log in using different accounts (Google, Facebook, etc.). It’s way more flexible and secure.

### What is the role of JWT in API authentication?

JWT is like a pass that says, "Hey, this user is legit!" After logging in, the server gives the client a token. When the client wants to call an API, it sends the token in the header. The server checks the token to make sure the user is allowed.

### How do jwks-rsa and public/private key verification work in Auth0?

`jwks-rsa` gets the public keys from Auth0. Auth0 signs the JWT with its private key, and the server uses the public key to check if the token is real and hasn’t been messed with.

### How would you protect an API route so that only authenticated users can access it?

To protect a route, you use a JWT guard in NestJS. It checks if the request has a valid JWT. If it does, the user gets in; if not, they get a "not allowed" message.

![Image](https://github.com/user-attachments/assets/79bc8915-5913-4738-9268-9836cbc29651)
