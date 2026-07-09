# Docker Volume and Bind Mount with Nginx

This repository demonstrates a practical, hands-on approach to mastering storage options in Docker. It explores the key differences between **Docker Named Volumes** (managed by Docker for data persistence like logs) and **Bind Mounts** (linking a specific host directory to a container for instant source code updates).

---

## Step 1: Create a Docker Named Volume for Persistent Logs

Create a dedicated Docker volume named `nginx_logs` to ensure that Nginx access and error logs persist on the host machine even if the container is destroyed.

```bash
docker volume create nginx_logs
```
Verify the creation and inspect the volume's default storage path (Mountpoint) on your host machine:
```bash
docker volume inspect nginx_logs
```
