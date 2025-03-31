# 🐳 Docker Commands Cheat Sheet

## 🧱 Basic Docker CLI
- `docker --version` – Check Docker version
- `docker info` – System-wide info
- `docker help` – Get CLI help

## 📦 Working with Images
- `docker pull nginx` – Download an image
- `docker images` – List local images
- `docker rmi nginx` – Remove an image

## 🚀 Running Containers
- `docker run hello-world` – Run a test container
- `docker run -it ubuntu` – Run interactive Ubuntu shell
- `docker run -d -p 8080:80 nginx` – Detached NGINX on port 8080

## 🛠️ Container Management
- `docker ps` – Show running containers
- `docker ps -a` – Show all containers
- `docker stop <container_id>` – Stop container
- `docker start <container_id>` – Start container
- `docker rm <container_id>` – Remove container
- `docker logs <container_id>` – Show logs
- `docker exec -it <container_id> bash` – Enter running container shell

## 📁 Volumes & Mounts
- `docker volume ls` – List volumes
- `docker run -v data:/data busybox` – Named volume
- `docker run -v $(pwd)/config:/app/config` – Bind mount

## 🧪 Dockerfile & Build
```dockerfile
# Example Dockerfile
FROM alpine
RUN apk add --no-cache curl
CMD ["curl", "https://example.com"]
```
- `docker build -t myimage .` – Build image
- `docker run myimage` – Run custom image

## 🧹 Cleanup
- `docker system prune` – Clean all unused stuff
- `docker volume prune` – Remove unused volumes
- `docker rmi $(docker images -q)` – Remove all images (careful!)

## 💡 Pro Tips
- Use `--name mycontainer` to name your container
- Use `-e VAR=value` to pass env variables
- Use `.dockerignore` like `.gitignore`
- Check `docker-compose` for multi-container setups
