# OpenClaw Switch Skill

The missing model manager for OpenClaw. Robust, zero-dependency model switching and fallback visualization.

Designed for users who juggle multiple API keys (e.g., Paid + Free Gemini) or mix providers (Gemini + OpenAI + Local) and want automatic failover when rate limits (429) hit.

## Features

- **🛡️ Zero Dependencies**: Pure `bash` + `python3` stdlib. No `jq`, no `curl`, no external packages.
- **🔒 Secure**: Never transmits API keys. Masks keys in output. Reads local `openclaw.json` only.
- **⚡️ Fast**: Instant status check. < 150 lines of code.
- **🔌 Universal**: Works with any provider (Gemini, Anthropic, OpenAI, Ollama, etc.).

## Installation

Clone this repository into your OpenClaw skills directory:

```bash
cd ~/.openclaw/skills
git clone https://github.com/YOUR_USERNAME/openclaw-switch.git openclaw-switch
```

Or just copy the folder `openclaw-switch` to `~/.openclaw/skills/`.

## Usage

Run the script directly:

```bash
# Show current status & fallback chain
bash scripts/openclaw-switch.sh status

# List all available models
bash scripts/openclaw-switch.sh list

# Switch to a specific model (by number)
bash scripts/openclaw-switch.sh switch 2
```

## How Configuration Works

It reads your `~/.openclaw/openclaw.json`. Ensure you have `fallbacks` configured:

```json
"agents": {
  "defaults": {
    "model": {
      "primary": "gemini-paid/flash",
      "fallbacks": ["gemini-free/flash", "nvidia/kimi"]
    }
  }
}
```

## License

MIT
