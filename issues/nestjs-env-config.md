# Handling Environment Variables & Configuration Reflection

**How does `@nestjs/config` help manage environment variables?**
The `@nestjs/config` package internally uses `dotenv` to load environment variables from a `.env` file into the Node.js `process.env` object. It also provides a `ConfigService` that can be dependency-injected throughout the NestJS application, allowing developers to read configuration values safely and with TypeScript typings.

**Why should secrets (e.g., API keys, database passwords) never be stored in source code?**
Hardcoding secrets in the source code exposes them to anyone with read access to the version control repository. If the code is ever made public or compromised, attackers can instantly access databases, external APIs, and sensitive user data. Secrets must remain strictly in the deployment environment.

**How can you validate environment variables before the app starts?**
By using a schema validation library like `joi` inside the `ConfigModule.forRoot({ validationSchema: ... })` configuration, NestJS will evaluate the `.env` file during the bootstrapping phase. If any required variable is missing or has the wrong data type, the application will immediately crash and refuse to start, preventing unpredictable runtime errors.

**How can you separate configuration for different environments (e.g., local vs. production)?**
Configuration can be separated by using different `.env` files (like `.env.development`, `.env.test`, and `.env.production`) and dynamically loading the correct one based on the `NODE_ENV` variable. In a true production environment, `.env` files are typically ignored entirely, and the variables are injected directly by the hosting platform (like AWS, Heroku, or Docker).