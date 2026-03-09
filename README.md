# Animus Engine - Unraid Template

Unraid Community Applications template for [Animus Engine](https://github.com/craigtut/animus), an autonomous AI assistant with persistent inner life.

## Installation

### Via Community Applications (once approved)

1. Open the **Apps** tab in Unraid
2. Search for "Animus Engine"
3. Click **Install**
4. Fill in your API key and adjust settings
5. Click **Apply**

### Manual Template Install

1. In Unraid, go to **Apps > Settings** (gear icon)
2. Under **Template Repositories**, add:
   ```
   https://github.com/craigtut/animus-unraid-template
   ```
3. Click **Save**
4. Search for "Animus Engine" in the Apps tab

## Configuration

| Setting | Default | Description |
|---------|---------|-------------|
| Web UI Port | 3000 | Port for the web interface |
| Data Directory | /mnt/user/appdata/animus-engine | Persistent storage for databases, models, and logs |
| Anthropic API Key | (empty) | Required if using Claude (default provider) |
| OpenAI API Key | (empty) | Required only if using Codex provider |
| Log Level | info | Options: debug, info, warn, error |

## Data Storage

All persistent data is stored in the mapped data directory:

- `databases/` - Seven SQLite databases (system, persona, heartbeat, memory, messages, agent_logs, contacts)
- `databases/lancedb/` - Vector embeddings for semantic search
- `huggingface_cache/` - Downloaded embedding models (BGE-small-en-v1.5)
- `logs/` - Application log files

## Requirements

- Unraid 6.12+
- At least 512MB RAM (8GB recommended for optimal performance)
- An API key for your chosen LLM provider (Anthropic recommended)

## Docker Image

> **Note**: The Docker image reference (`ghcr.io/animus-labs/animus-engine`) is a placeholder. This will be updated once the image is published to a container registry.

To build and push the image manually from the [Animus repository](https://github.com/craigtut/animus):

```bash
# Build for amd64 (typical Unraid architecture)
docker buildx build --platform linux/amd64 -t ghcr.io/animus-labs/animus-engine:latest . --load

# Push to registry
docker push ghcr.io/animus-labs/animus-engine:latest
```

## Links

- [Animus Engine Repository](https://github.com/craigtut/animus)
- [Report Issues](https://github.com/craigtut/animus/issues)
