# Claudex — Claude Handoff

## What this project is

Claudex is a single-file static web app (`index.html`) — a complete Claude Code reference. Every slash command, shortcut, CLI flag, config option, tip, and plugin in one searchable page.

**Repo:** DalrockGoons/Claudex (GitHub org, not personal)  
**Deployed:** Vercel — auto-deploys on push to `main`  
**Git user:** Claudex

---

## How to add or update content

All data lives as JS arrays inside `index.html`. No build step.

| Array | Tab | Entry shape |
|-------|-----|-------------|
| `COMMANDS` | Commands | `{ name, icon, cat, badge, desc, usage, aliases? }` |
| `SHORTCUTS` | Shortcuts | `{ group, rows: [{ key, desc, note }] }` |
| `CLI` | CLI | `{ group, rows: [{ key, desc, note }] }` |
| `CONFIG` | Config | `{ group, rows: [{ key, desc, note }] }` |
| `TIPS` | Tips | `{ title, body }` |
| `PLUGINS` | Plugins | `{ name, icon, cat, badge, desc, usage }` |

**Categories for COMMANDS:** `session`, `git`, `config`, `memory`, `debug`, `tools`, `workflow`, `skills`, `plugin`

Before adding a new feature, verify its description using the `claude-code-guide` subagent — don't invent flag names or behavior.

---

## Periodic maintenance checklist

At the end of each session (or when asked), do all of the following:

1. **Update README.md changelog** — add dated entries for any new cards, corrections, or removals
2. **Update memory files** — refresh `~/.claude/projects/D--ClaudeCode-ClaudeHelper/memory/project.md` if anything changed about the project structure
3. **Commit** — stage `index.html` and `README.md`, write a clear commit message
4. **Push** — push to `origin main` so Vercel deploys

---

## Current content inventory (as of 2026-04-05)

**Commands tab categories:**
- Session: /help, /clear, /compact, /cost, /status, /btw, /resume, /rename, /branch, /rewind, /copy, /export, /login, /logout, /exit
- Git: /commit, /pr, /pr-comments, /review, /security-review, /diff, /install-github-app
- Config: /config, /model, /effort, /fast, /init, /theme, /color, /permissions, /terminal-setup, /statusline, /keybindings, /vim, /voice, /privacy-settings, /sandbox, Auto Mode
- Memory: /memory, /dream, /insights, /stats, /context
- Debug: /doctor, /bug, /release-notes, /usage, /extra-usage
- Tools: /mcp, /hooks, /tasks, /add-dir, /remote-control, /desktop, /ide, /plugin, /reload-plugins, /skills
- Workflow: /plan
- Skills: /batch, /loop, /simplify, /debug

**Plugins tab:** frontend-design, computer-use

---

## Style rules

- Descriptions: 2–3 sentences max, factual, no fluff
- Usage examples: show real invocations, one per line
- Icons: single Unicode char or symbol — match the aesthetic of existing entries
- Never invent CLI flags — verify with the claude-code-guide agent
