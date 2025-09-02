# Ollama Usage Guide - How It Works

## What is Ollama?

**Ollama** is a tool that makes it easy to run large language models (LLMs) locally on your computer. Instead of sending your data to external AI services, Ollama lets you run AI models completely offline and privately.

## How Ollama Works

### Architecture Overview
```
┌─────────────────────────────────────┐
│         Your Application            │
│      (PKC, Terminal, etc.)          │
├─────────────────────────────────────┤
│         Ollama API                  │
│     (HTTP REST Interface)           │
├─────────────────────────────────────┤
│        Ollama Server                │
│    (Model Management Layer)         │
├─────────────────────────────────────┤
│         AI Models                   │
│  (Llama2, Mistral, CodeLlama)      │
├─────────────────────────────────────┤
│      Your Computer Hardware         │
│        (CPU, RAM, GPU)              │
└─────────────────────────────────────┘
```

### Core Components

#### 1. **Ollama Server**
- Runs as a service on your computer
- Manages model loading and unloading
- Handles API requests from applications
- Default port: `http://localhost:11434`

#### 2. **Model Storage**
- Downloaded models stored locally on your computer
- Models are compressed and optimized for local use
- Typical location: `~/.ollama/models/`

#### 3. **API Interface**
- REST API for applications to communicate with models
- Compatible with OpenAI API format
- Supports chat, completions, and embeddings

## How Local AI Models Work

### Model Loading Process
1. **Download**: Model files downloaded to local storage
2. **Load**: Model loaded into computer memory (RAM/GPU)
3. **Ready**: Model ready to process requests
4. **Inference**: Model generates responses to prompts

### Memory Requirements
| Model Size | RAM Required | Response Speed | Quality |
|------------|--------------|----------------|---------|
| 7B | 8GB+ | Fast | Good |
| 13B | 16GB+ | Medium | Better |
| 70B | 64GB+ | Slow | Best |

## Detailed Usage Scenarios

### 1. Interactive Chat Sessions

#### Starting a Chat
```bash
# Start interactive mode
ollama run llama2

# You'll see a prompt like:
>>> Send a message (/? for help)
```

#### Chat Commands
```bash
# During chat, you can use:
/help          # Show available commands
/show          # Display model information
/load <model>  # Switch to different model
/save <name>   # Save conversation
/clear         # Clear conversation history
/bye           # Exit chat
```

### 2. API Integration

#### Basic API Request
```bash
# Send request via curl
curl http://localhost:11434/api/generate \
  -d '{
    "model": "llama2",
    "prompt": "Why is the sky blue?",
    "stream": false
  }'
```

#### Streaming Response
```bash
# Get streaming response
curl http://localhost:11434/api/generate \
  -d '{
    "model": "llama2", 
    "prompt": "Tell me a story",
    "stream": true
  }'
```

### 3. Programming Integration

#### Python Example
```python
import requests
import json

def chat_with_ollama(prompt, model="llama2"):
    url = "http://localhost:11434/api/generate"
    data = {
        "model": model,
        "prompt": prompt,
        "stream": False
    }
    
    response = requests.post(url, json=data)
    return response.json()["response"]

# Usage
answer = chat_with_ollama("What is machine learning?")
print(answer)
```

## Model Management Deep Dive

### Model Files Structure
```
~/.ollama/models/
├── blobs/              # Model weight files
├── manifests/          # Model metadata
└── registry/           # Registry information
```

### Model Variants
Models come in different sizes and formats:
- **7B, 13B, 70B**: Number of parameters (billions)
- **q4_0, q4_1**: Quantization levels (smaller file size)
- **instruct**: Fine-tuned for instruction following
- **chat**: Optimized for conversations

### Custom Models
```bash
# Create custom model from Modelfile
ollama create my-model -f ./Modelfile

# Example Modelfile content:
FROM llama2
PARAMETER temperature 0.7
SYSTEM "You are a helpful coding assistant"
```

## Integration with PKC

### How PKC Uses Ollama
1. **PKC starts up**: Connects to Ollama API
2. **User query**: PKC sends question to Ollama
3. **AI processing**: Ollama runs model inference
4. **Response**: AI-generated answer returned to PKC
5. **Display**: PKC shows response to user

### Configuration
PKC typically connects to Ollama via:
- **URL**: `http://localhost:11434`
- **Model**: Configurable in PKC settings
- **Context**: PKC maintains conversation context

## Performance Optimization

### Hardware Recommendations
- **CPU**: Modern multi-core processor
- **RAM**: 16GB+ recommended for 13B models
- **Storage**: SSD for faster model loading
- **GPU**: Optional, can accelerate inference

### Speed vs Quality Trade-offs
- **Smaller models** (7B): Faster but less capable
- **Larger models** (70B): Slower but more intelligent
- **Quantization**: Reduces quality but saves memory

### Performance Tips
```bash
# Use specific quantization for speed
ollama pull llama2:7b-q4_0

# Monitor resource usage
ollama ps
top -p $(pgrep ollama)
```

## Privacy and Security

### Data Privacy Benefits
- **No internet required**: Models run completely offline
- **No data sharing**: Conversations never leave your computer
- **Complete control**: You own and control the AI models
- **Compliance**: Meets strict data privacy requirements

### Security Considerations
- Ollama server runs locally (localhost only by default)
- No authentication required for local access
- Models are read-only after download
- No telemetry or usage tracking

## Troubleshooting Common Issues

### Model Won't Load
```bash
# Check available memory
free -h

# Verify model is downloaded
ollama list

# Try smaller model if out of memory
ollama pull llama2:7b-q4_0
```

### Slow Performance
- Close other memory-intensive applications
- Use smaller/quantized models
- Ensure SSD storage for model files
- Consider GPU acceleration if available

### Connection Issues
```bash
# Check if Ollama is running
curl http://localhost:11434/api/tags

# Restart Ollama service
ollama serve
```

## Advanced Usage

### Batch Processing
```python
# Process multiple prompts efficiently
prompts = [
    "Summarize quantum physics",
    "Explain machine learning", 
    "What is blockchain?"
]

for prompt in prompts:
    response = chat_with_ollama(prompt)
    print(f"Q: {prompt}")
    print(f"A: {response}\n")
```

### Custom System Prompts
```bash
# Run with custom system behavior
ollama run llama2 --system "You are a helpful coding assistant who explains concepts clearly"
```

### Model Comparison
```bash
# Compare different models for same prompt
models=("llama2" "mistral" "codellama")
prompt="Explain recursion in programming"

for model in "${models[@]}"; do
    echo "=== $model ==="
    ollama run $model "$prompt"
    echo
done
```

## Integration Examples

### Web Applications
- PKC (Personal Knowledge Container)
- Custom chatbots
- Content generation tools
- Code assistants

### Desktop Applications
- Text editors with AI features
- Research tools
- Writing assistants
- Development environments

### Command Line Tools
- Shell scripting with AI
- Automated documentation
- Code review assistants
- Data analysis helpers

---

*Ollama brings the power of large language models to your local environment, providing privacy-preserving AI capabilities that integrate seamlessly with applications like PKC.*
