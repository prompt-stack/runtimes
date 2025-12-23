# Prompt Stack Runtimes

Pre-built binaries and tools for Prompt Stack. Users install via `pstack runtime ensure <name>`.

## Available Runtimes

### Core Runtimes
| Runtime | Version | Description |
|---------|---------|-------------|
| node | 20.10.0 | JavaScript runtime (bundled) |
| python | 3.12 | Python with data/ML packages |
| deno | 1.40 | Secure TypeScript runtime |
| bun | 1.0 | Fast JavaScript runtime |

### AI Agents
| Agent | Description |
|-------|-------------|
| claude | Anthropic Claude Code CLI |
| codex | OpenAI Codex CLI |
| gemini | Google Gemini CLI |
| ollama | Local LLMs (Llama, Mistral, etc.) |

### Tools
| Tool | Version | Description |
|------|---------|-------------|
| rclone | 1.68 | Cloud storage (Google Drive, S3, Dropbox) |
| ffmpeg | 6.0 | Audio/video processing |
| pandoc | 3.5 | Document conversion |
| imagemagick | 7.1 | Image processing |
| chromium | 131 | Browser automation |
| jq | 1.7 | JSON processor |
| yq | 4.40 | YAML processor |
| sqlite | 3.44 | Local database |
| ytdlp | 2024.01 | Video downloader |

### Cloud CLIs
| CLI | Description |
|-----|-------------|
| supabase | Supabase local dev |
| vercel | Deploy to Vercel |
| netlify | Deploy to Netlify |
| wrangler | Cloudflare Workers |
| railway | Railway hosting |
| flyio | Fly.io edge hosting |

## Usage

```bash
# List available runtimes
pstack runtime list

# Install a runtime
pstack runtime ensure python
pstack runtime ensure rclone

# Update registry
pstack registry update
```

## How It Works

1. `registry.json` in releases defines available runtimes
2. CLI downloads and extracts to `~/.prompt-stack/runtimes/`
3. Binaries are added to PATH when running stacks

## Adding New Runtimes

1. Package binary as `{name}-{version}-{platform}-{arch}.tar.gz`
2. Upload to release
3. Add entry to `registry.json`

## Platforms

- `darwin-arm64` (Apple Silicon)
- `darwin-x64` (Intel Mac)
- `linux-x64` (Linux)
- `linux-arm64` (Linux ARM)
