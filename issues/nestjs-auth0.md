# Authentication in NestJS with Auth0 & JWT Reflection

**How does Auth0 handle authentication compared to traditional username/password auth?**
Instead of the backend application storing, hashing, and verifying passwords directly in a local database, Auth0 acts as an external Identity Provider (IdP). It handles the entire login flow securely and simply returns a signed token to the client. This offloads the security burden and allows for easy integration of features like Multi-Factor Authentication (MFA) and social logins.

**What is the role of JWT in API authentication?**
A JSON Web Token (JWT) serves as a stateless, verifiable credential. Because the token contains both the user's identity (payload) and a cryptographic signature, the backend API does not need to look up a session ID in a database for every single request. It simply validates the signature and reads the payload to authenticate the user, which makes scaling the backend much easier.

**How do `jwks-rsa` and public/private key verification work in Auth0?**
Auth0 signs the JWT using a private key that only they possess. The `jwks-rsa` library allows the NestJS backend to automatically fetch Auth0's public keys from their JSON Web Key Set (JWKS) endpoint. NestJS then uses this public key to verify the token's signature. If the signature matches, it mathematically proves the token was issued by Auth0 and has not been tampered with.

**How would you protect an API route so that only authenticated users can access it?**
I would use the `@nestjs/passport` package to create a `JwtStrategy` that defines how to extract and verify the token. Then, I would apply the `@UseGuards(AuthGuard('jwt'))` decorator to the specific controller or route handler. This guard intercepts the request, runs the strategy, and automatically blocks the request with a `401 Unauthorized` error if the token is missing, invalid, or expired.