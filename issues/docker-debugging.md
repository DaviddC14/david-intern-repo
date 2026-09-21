# Debugging & Managing Docker Containers Reflection

**How can you check logs from a running container?**
You can check the logs using the `docker logs <container_name_or_id>` command. To monitor the logs in real-time as they are generated, you can append the follow flag: `docker logs -f <container_name>`. You can also use `--tail 50` to only see the last 50 lines if the log history is too massive.

**What is the difference between `docker exec` and `docker attach`?**
`docker exec` starts a *new* process (like a bash shell) inside an already running container, allowing you to explore the filesystem or run debugging commands without interrupting the application. `docker attach` connects your terminal directly to the container's *primary* running process (PID 1). If you use `Ctrl+C` while attached, you will likely kill the main process and stop the entire container.

**How do you restart a container without losing data?**
You can gracefully restart it using `docker restart <container_name>`. However, to ensure data (like database records) is never lost even if the container is removed (`docker rm`) or rebuilt (`docker-compose down && up`), the data must be stored in a **Docker Volume** or a bind mount that maps a directory inside the container to a secure location on the host machine's hard drive.

**How can you troubleshoot database connection issues inside a containerized NestJS app?**
First, use `docker logs <nestjs_container>` to read the exact database connection error. Next, verify that both the app and the database containers are on the same Docker network (`docker network inspect <network_name>`). Finally, use `docker exec -it <nestjs_container> /bin/sh` to enter the app container and use tools like `ping <database_container_name>` or `nc -vz <database_container_name> 5432` to verify internal DNS resolution and port connectivity. Remember that containerized apps must use the database container's name as the host, not `localhost`.