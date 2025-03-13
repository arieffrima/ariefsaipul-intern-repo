# Docker Debugging Guide

## 1. How to check logs from a running container?

To check the logs of a running container, use the following command:

bash
docker logs <container_name_or_id>

## What is the difference between docker exec and docker attach?

    - docker exec: This command runs a new command in a running container, and you can specify a new process. It’s useful for debugging or running one-time commands. For example:

    docker exec -it <container_name_or_id> bash

    - docker attach: This command attaches your terminal to a running container’s main process (the PID 1 process). It doesn’t start a new process; you’re simply interacting with the container’s main running application. For example:

    docker attach <container_name_or_id>

## How to restart a container without losing data?

To restart a container without losing data, ensure that any data you want to persist is stored in volumes or bind mounts. These are not affected by container restarts.

To restart the container:

- docker restart <container_name_or_id>

## How to troubleshoot database connection issues inside a containerized NestJS app?

- Check the environment variables: Ensure that the correct database URL, username, password, and other connection details are being passed to the NestJS app. These are often set as environment variables or passed through configuration files like .env.

- Check the database container status: Ensure that your database container is running correctly.

        docker ps

- Ping the database: Use docker exec to access the NestJS app container and ping the database container (if it’s on the same network).

        docker exec -it <nestjs_container_id> bash
        ping <database_container_name>

- Check logs: Inspect the logs of both the NestJS container and the database container for any errors related to the connection:

        docker logs <nestjs_container_id>
        docker logs <database_container_id>

- Check network configuration: Ensure both the database and the NestJS app are part of the same Docker network, especially when using Docker Compose. You can specify the --network flag when running the containers to ensure they are linked.

- Check database port: Verify that the database is exposing the correct port, and the NestJS app is connecting to the correct host and port.

  If using Docker Compose, you can specify service names as the hostname in the connection string, e.g., postgres:5432.

- Ensure correct dependencies: Make sure the NestJS app has the correct database driver (e.g., pg for PostgreSQL) and is configured correctly in the NestJS service module.
