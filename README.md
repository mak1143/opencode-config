# opencode-config

Personal [opencode](https://opencode.ai) configuration: rules, skills, agents, commands, and MCP setup.

## What's inside

| Area | Contents |
|---|---|
| `rules/` | Global instructions auto-loaded into every session (code style, security, testing, review, debugging…) |
| `skills/` | Reusable skills (API design, docker, CI, design systems, UI/UX, test writing…) |
| `agents/` | Specialized subagents (frontend-engineer, python, linux-assistant, debugger…) |
| `commands/` | Slash-commands for workflows, learning, and engineering tasks |
| `opencode.json` | Providers (ollama, openrouter), MCP servers, instructions glob |

## Install

Clone this repo into your global opencode config directory:

```sh
git clone https://github.com/mak1143/opencode-config.git ~/.config/opencode
```

Then review and adjust for your own machine:

1. **`opencode.json`** — merge anything you already have (auth, providers, MCP keys). Provider keys come from env vars, never hardcoded:
   - `OPENROUTER_API_KEY` for openrouter
   - `CONTEXT7_API_KEY` for the Context7 MCP server
2. **`mcp.filesystem`** — change the `/home/shoyo` root to your own home directory.
3. **`shell`** — set to your shell (e.g. `/bin/zsh`, `/bin/bash`).
4. Restart opencode so the new config loads.

## What's intentionally excluded

- `memory/` — personal learning notes, not shared
- `.env`, secrets — set your own env vars
- `package.json` / `node_modules` — plugin dependencies, install your own if needed

## Verify

```sh
git status            # working tree clean
git log --oneline     # history
```
