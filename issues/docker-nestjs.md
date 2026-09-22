# Using Docker for NestJS Development Reflection

**How does a `Dockerfile` define a containerized NestJS application?**
A `Dockerfile` acts as a blueprint, providing step-by-step instructions for Docker to build an image. It specifies the base operating system (like Node.js Alpine), sets the working directory, copies the `package.json` to install dependencies, copies the source code, builds the TypeScript application into JavaScript, and defines the final command (`CMD`) to start the NestJS server.

**What is the purpose of a multi-stage build in Docker?**
Multi-stage builds optimize the final Docker image. In a NestJS app, the first stage includes all development tools (like the TypeScript compiler and `devDependencies`) to build the application. The second stage uses a fresh, lightweight base image, copies only the compiled `dist` folder and production dependencies from the first stage, and discards the rest. This drastically reduces the image size and improves security by keeping build tools out of the production environment.

**How does Docker Compose simplify running multiple services together?**
Docker Compose uses a single `docker-compose.yml` declarative file to configure and launch multiple containers simultaneously. For a NestJS app needing a database, Compose creates an isolated internal network so the API container can communicate with the PostgreSQL container using just its service name (e.g., `db`) instead of an IP address, handling all the environment variables and port mappings automatically.

**How can you expose API logs and debug a running container?**
When running services via Docker Compose, you can expose and follow the combined logs using `docker-compose logs -f`. If you only want to see the NestJS API logs, you can run `docker-compose logs -f api`. To debug internally, you can attach an interactive shell to the running container using `docker exec -it <container_name> /bin/sh`, allowing you to inspect the file system or run network diagnostics.