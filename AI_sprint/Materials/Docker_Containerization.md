# Docker (Containerization)

## What is Docker?

**Docker** is a platform that uses containerization technology to package applications and their dependencies into lightweight, portable containers that can run consistently across different environments.

## Container vs Virtual Machine

### Traditional Virtual Machines
```
┌─────────────────────────────────────┐
│          Application A              │
├─────────────────────────────────────┤
│         Guest OS (Linux)            │
├─────────────────────────────────────┤
│          Hypervisor                 │
├─────────────────────────────────────┤
│         Host OS (Windows)           │
├─────────────────────────────────────┤
│          Hardware                   │
└─────────────────────────────────────┘
```

### Docker Containers
```
┌─────────────────────────────────────┐
│          Application A              │
├─────────────────────────────────────┤
│        Docker Container             │
├─────────────────────────────────────┤
│         Docker Engine               │
├─────────────────────────────────────┤
│         Host OS (Any)               │
├─────────────────────────────────────┤
│          Hardware                   │
└─────────────────────────────────────┘
```

### Key Differences
| Virtual Machines | Docker Containers |
|------------------|-------------------|
| Full OS required | Shares host OS |
| Heavy resource usage | Lightweight |
| Slow startup | Fast startup |
| GB of storage | MB of storage |
| Strong isolation | Process-level isolation |

## Core Docker Concepts

### Images
- **Definition** - Read-only templates used to create containers
- **Layers** - Built in layers for efficiency
- **Reusable** - One image can create many containers
- **Shareable** - Can be shared via registries

### Containers
- **Definition** - Running instances of Docker images
- **Isolated** - Each container runs independently
- **Ephemeral** - Can be stopped, started, deleted easily
- **Stateless** - Data doesn't persist unless configured

### Dockerfile
- **Definition** - Text file with instructions to build an image
- **Automated** - Defines the environment and setup steps
- **Reproducible** - Same Dockerfile creates identical images
- **Version Control** - Can be tracked like code

### Docker Compose
- **Definition** - Tool for defining multi-container applications
- **YAML Configuration** - Uses docker-compose.yml files
- **Service Orchestration** - Manages multiple connected containers
- **Development Focus** - Simplifies local development environments

## How Docker Works

### Build Process
1. **Write Dockerfile** - Define the environment and application
2. **Build Image** - Create reusable template
3. **Run Container** - Start the application from image
4. **Manage Lifecycle** - Stop, start, update, remove containers

### Docker Commands
```bash
# Build an image
docker build -t myapp .

# Run a container
docker run -p 8080:80 myapp

# List running containers
docker ps

# Stop a container
docker stop container_name

# Remove a container
docker rm container_name
```

## Docker in the AI Sprint Program

### Session 3: Local Gaming with TOSIOS
- **TOSIOS Container** - Game server runs in Docker container
- **Benefits**: Easy deployment, consistent environment
- **Learning**: Understand containerized applications

### Session 4: Docker Deep Dive
- **Hosting TOSIOS** - Learn to deploy containerized applications
- **PKC Deployment** - Understand how PKC runs in containers
- **Docker Compose** - Manage multi-service applications

### Session 6-8: Complete PKC System
- **PKC Infrastructure** - All components run in containers
- **Database Containers** - Persistent data storage
- **Web Interface** - Frontend served from containers
- **AI Integration** - Ollama integration with containerized PKC

## Docker Compose for PKC

### Example docker-compose.yml
```yaml
version: '3.8'
services:
  pkc-frontend:
    image: pkc/frontend:latest
    ports:
      - "3000:3000"
    depends_on:
      - pkc-backend
      
  pkc-backend:
    image: pkc/backend:latest
    ports:
      - "8000:8000"
    environment:
      - DATABASE_URL=postgresql://db:5432/pkc
      - OLLAMA_URL=http://ollama:11434
    depends_on:
      - database
      - ollama
      
  database:
    image: postgres:15
    environment:
      - POSTGRES_DB=pkc
      - POSTGRES_USER=pkc_user
      - POSTGRES_PASSWORD=secure_password
    volumes:
      - pgdata:/var/lib/postgresql/data
      
  ollama:
    image: ollama/ollama:latest
    ports:
      - "11434:11434"
    volumes:
      - ollama_data:/root/.ollama

volumes:
  pgdata:
  ollama_data:
```

## Benefits of Docker

### Development Benefits
- **Consistent Environment** - "Works on my machine" problems eliminated
- **Easy Setup** - New developers can start quickly
- **Dependency Management** - All dependencies packaged together
- **Version Control** - Environment configurations tracked

### Deployment Benefits
- **Portability** - Run anywhere Docker is installed
- **Scalability** - Easy to scale applications up or down
- **Isolation** - Applications don't interfere with each other
- **Rollback** - Easy to revert to previous versions

### Operational Benefits
- **Resource Efficiency** - Better hardware utilization
- **Fast Startup** - Containers start in seconds
- **Easy Updates** - Replace containers without downtime
- **Monitoring** - Built-in logging and monitoring capabilities

## Docker for Local-First Applications

### Privacy Benefits
- **Local Deployment** - Everything runs on your device
- **No Cloud Dependency** - Complete independence from external services
- **Data Control** - Your data never leaves your machine
- **Custom Configuration** - Tailor environment to your needs

### Self-Hosting Capabilities
- **Personal Services** - Host your own versions of web services
- **Knowledge Management** - Run PKC entirely locally
- **AI Processing** - Local AI models in containers
- **Development Environment** - Consistent local development setup

## Common Docker Use Cases

### Web Applications
- **Frontend Containers** - React, Vue, Angular applications
- **Backend Containers** - API servers, databases
- **Reverse Proxies** - Nginx, Traefik for routing
- **SSL Termination** - HTTPS handling

### Development Tools
- **Database Containers** - PostgreSQL, MongoDB, Redis
- **Testing Environments** - Isolated test environments
- **Build Systems** - Continuous integration pipelines
- **Development Servers** - Local development environments

### Self-Hosted Services
- **File Storage** - Nextcloud, Seafile
- **Media Servers** - Plex, Jellyfin
- **Communication** - Rocket.Chat, Mattermost
- **Productivity** - GitLab, Bookstack, Wikis

## Docker Security Considerations

### Container Security
- **Least Privilege** - Run containers with minimal permissions
- **Network Isolation** - Use Docker networks for segmentation
- **Secret Management** - Don't embed secrets in images
- **Regular Updates** - Keep base images and Docker updated

### Best Practices
- **Non-Root Users** - Avoid running as root inside containers
- **Minimal Images** - Use slim base images
- **Image Scanning** - Check for vulnerabilities
- **Resource Limits** - Set CPU and memory limits

## Docker Networking

### Network Types
- **Bridge** - Default network for containers
- **Host** - Container shares host's network
- **None** - No network access
- **Custom** - User-defined networks for specific needs

### PKC Networking Example
```yaml
networks:
  pkc-network:
    driver: bridge

services:
  pkc-app:
    networks:
      - pkc-network
  database:
    networks:
      - pkc-network
```

## Docker Storage

### Volume Types
- **Named Volumes** - Managed by Docker, persistent
- **Bind Mounts** - Direct host directory access
- **tmpfs Mounts** - In-memory storage, temporary

### Data Persistence for PKC
```yaml
volumes:
  # Persistent database storage
  postgres_data:
  
  # Ollama model storage
  ollama_models:
  
  # PKC document storage
  pkc_documents:
```

## Troubleshooting Docker

### Common Issues
- **Port Conflicts** - Another service using the same port
- **Permission Errors** - Docker daemon access issues
- **Out of Space** - Docker images consuming disk space
- **Network Issues** - Containers can't communicate

### Debugging Commands
```bash
# View container logs
docker logs container_name

# Access container shell
docker exec -it container_name /bin/bash

# Inspect container configuration
docker inspect container_name

# View resource usage
docker stats

# Clean up unused resources
docker system prune
```

## Docker Alternatives

### Other Containerization Tools
- **Podman** - Rootless containers, Docker-compatible
- **LXC/LXD** - System containers, more VM-like
- **Containerd** - Lower-level container runtime
- **rkt** - Alternative container engine (deprecated)

### Why Docker?
- **Ecosystem** - Largest community and tooling
- **Documentation** - Extensive resources and tutorials
- **Industry Standard** - Widely adopted and supported
- **Integration** - Works well with development tools

## Future of Containerization

### Trends
- **Rootless Containers** - Better security without root privileges
- **WebAssembly** - Lightweight alternative to containers
- **Edge Computing** - Containers on IoT and edge devices
- **AI/ML Workloads** - Optimized containers for AI applications

### Local-First Evolution
- **Personal Cloud** - Self-hosted services in containers
- **Privacy Computing** - Containerized privacy-preserving applications
- **Edge AI** - Local AI models in containers
- **Decentralized Services** - P2P applications in containers

## Why Docker Matters for PKC

### Simplified Deployment
- **One Command** - Start entire PKC system with docker-compose
- **Consistent Environment** - Works the same on any machine
- **Easy Updates** - Update PKC by replacing containers
- **Backup/Restore** - Simple data volume management

### Independence and Control
- **No Vendor Lock-in** - Can run on any system with Docker
- **Custom Configuration** - Modify containers for specific needs
- **Local Hosting** - Complete control over deployment
- **Resource Management** - Efficient use of system resources

---

*Docker enables the local-first, privacy-preserving deployment of complex applications like PKC, making advanced personal knowledge management accessible to everyone.*
