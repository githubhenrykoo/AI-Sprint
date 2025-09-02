# Ollama Basic Commands Guide

## Essential Ollama Commands

### Installation Verification
```bash
# Check if Ollama is installed and running
ollama --version

# Check Ollama service status
ollama list
```

### Model Management

#### Download Models
```bash
# Download a lightweight model for beginners
ollama pull qwen3:0.6b

# Alternative small models (optional)
ollama pull phi3:3.8b
ollama pull gemma2:2b
```

#### List Models
```bash
# Show all downloaded models
ollama list

# Show detailed model information
ollama show qwen3:0.6b
```

#### Remove Models
```bash
# Delete a specific model
ollama rm qwen3:0.6b

# Remove alternative models if needed
ollama rm phi3:3.8b
```

### Running Models

#### Interactive Chat
```bash
# Start interactive chat with the lightweight model
ollama run qwen3:0.6b

# Alternative small models
ollama run phi3:3.8b
ollama run gemma2:2b
```

#### Single Prompts
```bash
# Send a single prompt
ollama run qwen3:0.6b "What is the capital of France?"

# Use quotes for complex prompts
ollama run qwen3:0.6b "Explain quantum computing in simple terms"
```

### Server Management

#### Start/Stop Ollama Service
```bash
# Start Ollama server (if not running)
ollama serve

# Stop Ollama (Ctrl+C if running in foreground)
```

#### Check Running Status
```bash
# List currently loaded models
ollama ps

# Check if server is responding
curl http://localhost:11434/api/tags
```

### Useful Commands

#### Help
```bash
# Show help information
ollama --help

# Show help for specific command
ollama pull --help
ollama run --help
```

#### Model Information
```bash
# Show model details
ollama show qwen3:0.6b

# List available small models online
ollama search qwen
ollama search phi
ollama search gemma
```

### Quick Reference

| Command | Purpose | Example |
|---------|---------|---------|
| `ollama pull <model>` | Download model | `ollama pull qwen3:0.6b` |
| `ollama run <model>` | Start interactive chat | `ollama run qwen3:0.6b` |
| `ollama list` | Show downloaded models | `ollama list` |
| `ollama rm <model>` | Remove model | `ollama rm qwen3:0.6b` |
| `ollama ps` | Show running models | `ollama ps` |
| `ollama serve` | Start server | `ollama serve` |

### Recommended Small Models for Beginners
- **qwen3:0.6b** - Lightweight Qwen model (~300MB) - **Recommended**
- **phi3:3.8b** - Microsoft's compact Phi model (~2GB)
- **gemma2:2b** - Google's small Gemma model (~1.6GB)
- **tinyllama** - Ultra-small model for testing (~637MB)

### Tips for Beginners
- **Start small**: Begin with qwen3:0.6b (only ~300MB download)
- **Fast downloads**: Small models download in minutes, not hours
- **Low resource usage**: Works on laptops with 8GB RAM
- **Quick responses**: Small models respond much faster
- **Perfect for learning**: Great for understanding Ollama basics
- Type `/bye` to exit interactive chat
- Press Ctrl+C to stop generation

### Why Small Models?
- **Faster setup**: Quick download and installation
- **Lower requirements**: Run on basic hardware
- **Good for practice**: Perfect for learning Ollama commands
- **Less storage**: Don't fill up your hard drive
