# Docker Setup Reflection

## 1. What is the difference between `docker run` and `docker-compose up`?

- **`docker run`**:

  - The `docker run` command is used to start a single container from a specified image. It provides options to configure container parameters like environment variables, volume mounts, network settings, and more. However, it is mainly used to start one container at a time.
  - Example:
    ```bash
    docker run -d --name my-container ubuntu
    ```

- **`docker-compose up`**:
  - The `docker-compose up` command is used to start multiple containers defined in a `docker-compose.yml` file. It reads the configuration file and starts all services (containers) with the specified settings in the file. It's more suitable for managing multi-container applications.
  - Example:
    ```bash
    docker-compose up
    ```

## 2. How does Docker Compose help when working with multiple services?

Docker Compose simplifies managing multiple services in a multi-container environment. It allows you to define and configure multiple containers in a single `docker-compose.yml` file. Some of the benefits include:

- **Simplified Configuration**: Instead of managing multiple `docker run` commands, you can define services, networks, and volumes all in one place.
- **Easy Scaling**: Docker Compose allows you to scale services (e.g., multiple instances of a service) with a single command.
- **Networking**: By default, Docker Compose creates a dedicated network for the services, making communication between them seamless.
- **Multi-Container Management**: You can start, stop, and manage all services with simple commands (`docker-compose up`, `docker-compose down`).

## 3. What commands can you use to check logs from a running container?

You can use the following commands to check logs from a running container:

- **`docker logs <container_name_or_id>`**:

  - This command retrieves logs from a specific container.
  - Example:
    ```bash
    docker logs my-container
    ```

- **`docker-compose logs`**:

  - If using Docker Compose, you can check logs for all services defined in the `docker-compose.yml` file.
  - Example:
    ```bash
    docker-compose logs
    ```

- **`docker logs -f <container_name_or_id>`**:
  - This command follows the log output in real-time.
  - Example:
    ```bash
    docker logs -f my-container
    ```

## 4. What happens when you restart a container? Does data persist?

When you restart a container, the container itself is stopped and started again. The following happens:

- **Container Restart**:
  - The container's state (running processes) is reset, meaning the container will start fresh, and any running applications or processes inside it will be stopped and restarted.
- **Data Persistence**:

  - **Non-Persistent Data**: If the container stores data in its internal filesystem, any data not stored in a volume will be lost when the container is restarted or removed.
  - **Persistent Data**: Data stored in Docker **volumes** or **bind mounts** will persist across restarts. Volumes are designed to persist data even if the container is removed or restarted.

  For example, if you use a volume to store database data, the data will remain even if the container is stopped or restarted.

  - Example of creating a volume:
    ```bash
    docker run -d --name my-container -v my-volume:/data ubuntu
    ```
