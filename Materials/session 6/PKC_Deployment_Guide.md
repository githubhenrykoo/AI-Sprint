# PKC Deployment Guide

## Prerequisites

Before starting, ensure you have the following installed:

- **Git** - [Download Git](https://git-scm.com/downloads)
- **Docker Desktop** - [Download Docker Desktop](https://www.docker.com/products/docker-desktop/)

### Verify Installation
```bash
# Check Git installation
git --version

# Check Docker installation  
docker --version
docker-compose --version
```

## Step-by-Step Deployment

### Step 1: Clone the PKC Repository

Open your terminal/command prompt and run:

```bash
git clone https://github.com/githubhenrykoo/PKC.git
```

### Step 2: Navigate to Project Directory

```bash
cd PKC
```

### Step 3: Start Docker Desktop

1. **Open Docker Desktop** application on your computer
2. **Wait for Docker to start** (you'll see the Docker icon in your system tray/menu bar)
3. **Ensure Docker is running** (the whale icon should not have any warning indicators)

### Step 4: Deploy with Docker Compose

Run the following command in the PKC project directory:

```bash
docker compose up
```

**What happens next:**
- Docker will start **pulling required images** from Docker Hub
- Docker will also **download large language models** (LLMs) - this can take significant time depending on your internet connection
- You'll see logs showing the download progress and container startup
- **Be patient** - LLM downloads can be several gigabytes in size

### Step 5: Access the Application

Once deployment is complete:
1. **Open your web browser**
2. **Navigate to**: `http://localhost:4321`
3. **Wait for full initialization** - even after containers start, the application may take additional time to fully load the language models

## Common Commands

### Start PKC (Foreground)
```bash
docker compose up
```

### Start PKC (Background)
```bash
docker compose up -d
```

### Stop PKC
```bash
docker compose down
```

### View Running Containers
```bash
docker ps
```

### View Logs
```bash
docker compose logs
```

## Troubleshooting

### Problem: "Docker command not found"
**Solution**: Ensure Docker Desktop is installed and running

### Problem: "Permission denied" when cloning
**Solution**: 
- Use HTTPS instead of SSH: `https://github.com/githubhenrykoo/PKC.git`
- Or set up SSH keys for GitHub

### Problem: "Port already in use"
**Solution**: 
- Stop any applications using the same ports
- Or modify the docker-compose.yml file to use different ports

### Problem: Slow download speeds
**Solution**: 
- Check your internet connection
- Docker images can be large, be patient during first-time setup

## What You've Learned

By completing this deployment, you have:
- Cloned a Git repository
- Used Docker Compose for application deployment
- Understood containerized application architecture
- Gained experience with container orchestration

## Next Steps

- Explore the PKC application functionality
- Review the docker-compose.yml file to understand the service architecture
- Learn about container networking and port mapping
- Practice stopping and starting containers