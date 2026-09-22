# Setting Up Docker and Docker Compose Reflection

**What is the difference between `docker run` and `docker-compose up`?**
`docker run` is a CLI command used to start a single container, requiring you to manually type out all configuration flags (such as ports, environment variables, and networks) directly in the terminal. `docker-compose up`, on the other hand, reads a declarative `docker-compose.yml` file to automatically spin up and orchestrate one or multiple interconnected containers simultaneously, using the predefined configurations.

**How does Docker Compose help when working with multiple services?**
When a backend relies on multiple dependent services (like a NestJS API, a PostgreSQL database, and a Redis cache), Docker Compose simplifies the setup by automatically creating an isolated internal network for them. This allows the containers to discover and communicate with each other using just their service names as hostnames, eliminating the need to manually link them or memorize dynamic IP addresses.

**What commands can you use to check logs from a running container?**
You can use `docker logs <container_name>` to view the static historical log output. To stream the logs live, you append the follow flag: `docker logs -f <container_name>`. When working with Docker Compose, you can view the interleaved logs of all running services using `docker-compose logs -f`, or isolate a specific service with `docker-compose logs -f <service_name>`.

**What happens when you restart a container? Does data persist?**
When a container is simply restarted using `docker restart`, the main process is stopped and started again, and the internal file system remains intact for that session. However, because containers are ephemeral by nature, if the container is ever removed or destroyed (e.g., running `docker-compose down` followed by `up`), any data written to its internal filesystem is lost permanently, unless that data was explicitly stored in a persistent Docker Volume mapped to the host machine.