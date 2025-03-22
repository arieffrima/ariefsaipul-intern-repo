# Reflection: (nestjs-security.md)

1. **What are the most common security vulnerabilities in a NestJS backend?**

   - The most common vulnerabilities are injection attacks (like SQL injection), Cross-Site Scripting (XSS), Cross-Site Request Forgery (CSRF), and misconfigured CORS settings. These can lead to data breaches or unauthorized access.

2. **How does @fastify/helmet improve application security?**

   - @fastify/helmet helps secure HTTP headers by setting security-related HTTP headers like Content Security Policy (CSP), X-Content-Type-Options, and X-Frame-Options. It makes it harder for attackers to exploit common vulnerabilities like clickjacking or MIME-sniffing.

3. **Why is rate limiting important for preventing abuse?**

   - Rate limiting helps prevent abuse like brute-force attacks or DoS (Denial of Service) attacks by restricting how many requests a user or client can make in a short period. This helps protect the backend from being overwhelmed by too many requests.

4. **How can sensitive configuration values be protected in a production environment?**
   - Sensitive configuration values like API keys or database credentials should never be hard-coded in the source code. Instead, use environment variables stored in a `.env` file. In production, these values should be securely stored using secret management tools, like AWS Secrets Manager or Vault by HashiCorp.
