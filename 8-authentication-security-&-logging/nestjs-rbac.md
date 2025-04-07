# Reflection (nestjs-rbac.md)

### How does Auth0 store and manage user roles?

Auth0 stores user roles in the access token. When a user logs in, Auth0 adds the roles to the token’s payload. These roles are set up in the Auth0 dashboard and can be added using rules.

### What is the purpose of a guard in NestJS?

A guard in NestJS is used to check if a user has permission to access a route. It’s like a checkpoint that checks if the user is logged in or has the right role before letting them through.

### How would you restrict access to an API endpoint based on user roles?

To restrict access use a Roles Guard. The user's roles are added to their JWT token. The guard checks if the role matches what the route requires. If not, the user gets blocked.

### What are the security risks of improper authorization, and how can they be mitigated?

With improper authorization, users might:

- Gain access to features they shouldn’t (privilege escalation).
- See sensitive data they aren’t allowed to (data leakage).

To prevent this:

- Use role-based access control (RBAC).
- Always check roles and permissions with guards.
- Keep tokens secure.
- Regularly update and review access control rules.

![Screenshot 2025-03-22 110830](https://github.com/user-attachments/assets/b85db83d-bf57-4bf0-a45e-bea38c658b35)
