# Animus Engine - Unraid Template

Unraid Community Applications template for [Animus Engine](https://github.com/craigtut/animus), an autonomous AI assistant with persistent inner life.

## Installation

### Via Community Applications (once approved)

1. Open the **Apps** tab in Unraid
2. Search for "Animus Engine"
3. Click **Install**
4. Adjust settings if needed
5. Click **Apply**
6. Add your API key via the container's environment variables (see [Optional Environment Variables](#optional-environment-variables))

### Manual Install

1. Download [`animus-engine.xml`](animus-engine.xml) from this repository
2. Copy it to your Unraid flash drive at:
   ```
   /boot/config/plugins/dockerMan/templates-user/animus-engine.xml
   ```
3. In Unraid, go to **Docker > Add Container**
4. Select "Animus Engine" from the template dropdown
5. Adjust settings if needed and click **Apply**

## Configuration

| Setting | Default | Description |
|---------|---------|-------------|
| Web UI Port | 3180 | Port for the web interface (maps to container port 3000) |
| Data Directory | /mnt/user/appdata/animus | Persistent storage for databases, models, and logs |
| Log Level | info | Options: debug, info, warn, error |

## Optional Environment Variables

These are not exposed in the template by default but can be added manually via the Unraid Docker container settings (click **Add another Path, Port, Variable, Label, or Device** and choose **Variable**).

| Variable | Description |
|----------|-------------|
| `ANTHROPIC_API_KEY` | Your Anthropic API key for Claude. Required if using Claude as the agent provider (default). |
| `OPENAI_API_KEY` | Your OpenAI API key. Required only if using Codex as the agent provider. |
| `NODE_ENV` | Node environment. Defaults to `production` inside the container. |
| `HOST` | Network interface to bind to. Defaults to `0.0.0.0`. |
| `PORT` | Internal container port. Defaults to `3000`. |
| `ANIMUS_DATA_DIR` | Internal data storage path. Defaults to `/app/data`. |

## Data Storage

All persistent data (databases, vector embeddings, model cache, and logs) is stored in the single mapped data directory. By default this is `/mnt/user/appdata/animus`.

## Requirements

- Unraid 6.12+
- An Anthropic or OpenAI account (subscription or API key)

## Links

- [Animus Engine Repository](https://github.com/craigtut/animus)
- [Report Issues](https://github.com/craigtut/animus/issues)
