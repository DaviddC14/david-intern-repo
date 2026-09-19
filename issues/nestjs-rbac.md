# Role-Based Authorization (RBAC) in NestJS Reflection

**How does Auth0 store and manage user roles?**
Auth0 manages user roles through its RBAC (Role-Based Access Control) system in the Auth0 Dashboard. Roles (like 'admin' or 'user') are assigned to user profiles. When a user logs in, Auth0 can be configured via "Actions" or "Rules" to inject these roles directly into the access JWT (JSON Web Token) as custom claims (e.g., under a custom namespace URL), making them accessible to the backend API.

**What is the purpose of a guard in NestJS?**
A Guard in NestJS is a single-responsibility class that implements the `CanActivate` interface. Its only job is to determine whether a given request should be allowed to reach the route handler or be blocked (typically returning a 403 Forbidden). It executes after middleware but before interceptors and pipes.

**How would you restrict access to an API endpoint based on user roles?**
I would first create a custom `@Roles()` decorator using NestJS's `SetMetadata` to define the required roles for a specific route. Then, I would apply a custom `RolesGuard` to the endpoint using `@UseGuards()`. Inside the guard, I would use the `Reflector` service to read the route's required roles and compare them against the roles stored in the `request.user` object (which is typically populated by a JWT authentication strategy).

**What are the security risks of improper authorization, and how can they be mitigated?**
Improper authorization can lead to Broken Access Control or Privilege Escalation, where standard users can access or modify administrative data. These risks can be mitigated by enforcing a strict "deny-by-default" policy on all routes, strictly validating JWT signatures on every request, never trusting client-side role assertions, and writing comprehensive unit and E2E tests to verify that unauthorized roles are successfully blocked.