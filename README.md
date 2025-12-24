# Prompt Stack Runtimes

Pre-built binaries for tools, languages, and AI agents used by Prompt Stack.

## Installation

Install a runtime via CLI:

```bash
pstack install python
pstack install ffmpeg
pstack install claude
```

## Supported Runtimes

### Languages (Core)

| Runtime | Version | Platform | Purpose |
|---------|---------|----------|---------|
| **node** | 20.11.0 | All | JavaScript/TypeScript execution |
| **python** | 3.12.0 | All | Python scripts and data processing |
| **deno** | 1.40.0 | All | Secure TypeScript runtime |
| **bun** | 1.0.0 | All | Fast JavaScript runtime |

### AI Agents

| Agent | Provider | Installation |
|-------|----------|--------------|
| **claude** | Anthropic | `npm install -g @anthropic-ai/claude-cli` |
| **codex** | OpenAI | `npm install -g openai-codex` |
| **gemini** | Google | `npm install -g google-gemini-cli` |
| **ollama** | Open Source | Pre-built binary |

### Data & Media Tools

| Tool | Version | Purpose |
|------|---------|---------|
| **ffmpeg** | 6.0.0 | Audio/video processing |
| **pandoc** | 3.5.0 | Document format conversion |
| **imagemagick** | 7.1.0 | Image processing and manipulation |
| **ytdlp** | 2024.01.01 | Video download from YouTube and other sites |
| **jq** | 1.7.0 | JSON parsing and transformation |
| **yq** | 4.40.0 | YAML parsing and transformation |
| **sqlite** | 3.44.0 | Local relational database |

### Cloud & Infrastructure

| CLI | Service | Purpose |
|-----|---------|---------|
| **vercel** | Vercel | Deploy applications to Vercel |
| **netlify** | Netlify | Deploy static sites to Netlify |
| **wrangler** | Cloudflare | Deploy Workers to Cloudflare |
| **railway** | Railway | Deploy applications to Railway |
| **flyio** | Fly.io | Deploy containers to Fly.io |
| **supabase** | Supabase | Manage Supabase databases locally |

### Utilities

| Tool | Purpose |
|------|---------|
| **git** | Version control (pre-bundled) |
| **ripgrep** | Fast file searching (pre-bundled) |
| **chromium** | Browser automation |
| **rclone** | Cloud storage access (Google Drive, S3, etc.) |

## How It Works

Runtimes are downloaded and installed into:

```
~/.prompt-stack/bin/
└── <runtime-name>/
    ├── bin/
    ├── lib/
    └── ...
```

When you run a stack that requires a runtime, the CLI automatically:

1. Checks if it's already installed
2. Downloads from this repository if missing
3. Extracts to `~/.prompt-stack/bin/`
4. Adds to PATH for the duration of execution

## Adding a New Runtime

To contribute a new runtime:

### 1. Build Binary

Build a cross-platform binary for all supported platforms:

```bash
# Package as tarball
tar -czf python-3.13-darwin-arm64.tar.gz python/
```

### 2. Create Runtime Descriptor

File: `packages/runtimes/<name>/runtime.yaml`

```yaml
id: my-tool
name: My Tool
version: 1.0.0
description: What this tool does
homepage: https://...
license: MIT

platforms:
  darwin-arm64:
    url: https://releases.../my-tool-1.0.0-darwin-arm64.tar.gz
    sha256: abc123...
  darwin-x64:
    url: https://releases.../my-tool-1.0.0-darwin-x64.tar.gz
    sha256: def456...
  linux-x64:
    url: https://releases.../my-tool-1.0.0-linux-x64.tar.gz
    sha256: ghi789...
  linux-arm64:
    url: https://releases.../my-tool-1.0.0-linux-arm64.tar.gz
    sha256: jkl012...

checksum: sha256
```

### 3. Submit Pull Request

Submit PR with your runtime descriptor to this repository.

## Platform Support

Runtimes are available for:

- **darwin-arm64** - macOS with Apple Silicon
- **darwin-x64** - macOS with Intel CPU
- **linux-x64** - Linux x86-64
- **linux-arm64** - Linux ARM64 (Raspberry Pi, etc.)

Windows support is planned.

## Troubleshooting

### Runtime Not Found

Check available runtimes:

```bash
pstack search --all --runtimes
```

### Verify Installation

```bash
pstack which python
# Output: /Users/username/.prompt-stack/bin/python/bin/python3
```

### Remove a Runtime

```bash
pstack remove python
```

## Contributing

See [CONTRIBUTING.md](../CONTRIBUTING.md) for how to add runtimes.

## License

Each runtime retains its original license. See LICENSE files in each runtime directory.
