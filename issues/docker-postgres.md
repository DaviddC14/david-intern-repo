# Running PostgreSQL in Docker Reflection

**What are the benefits of running PostgreSQL in a Docker container?**
Running PostgreSQL in Docker ensures a perfectly consistent development environment across the entire team, eliminating "it works on my machine" issues. It prevents polluting the host operating system with global database installations, allows developers to easily switch between different PostgreSQL versions, and makes onboarding new team members as simple as running a single command.

**How do Docker volumes help persist PostgreSQL data?**
By default, containers are ephemeral; if a container is removed, all its internal data is destroyed. Docker volumes solve this by mapping a directory inside the container (like `/var/lib/postgresql/data`) to a persistent location on the host machine's hard drive. This ensures that the database records survive container restarts, removals, and rebuilds.

**How can you connect to a running PostgreSQL container from a local database client?**
To connect locally, you must map the container's internal port to a host port using the `ports` configuration in `docker-compose.yml` (e.g., `"5432:5432"`). Once mapped, you can use a standard database GUI client (like pgAdmin, DBeaver, or VS Code extensions) and connect to `localhost:5432` using the environment variables defined in the container (`POSTGRES_USER` and `POSTGRES_PASSWORD`) as your credentials.