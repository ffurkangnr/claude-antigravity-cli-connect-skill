---
name: agy-cli
description: Delegate tasks to Google Antigravity CLI (agy) from Claude. Use when the user asks to run a task via Antigravity, agy, or an Antigravity-hosted model (Gemini, Claude, etc.).
---

# Antigravity CLI (`agy`) Integration Skill

Use this skill when the user wants to run prompts, coding tasks, or model queries through the local **Google Antigravity CLI (`agy`)**.

## 1. Locate `agy`

First check if `agy` is on `PATH`. If not, check the default Windows install path:
- Cross-platform: `agy --help`
- Windows fallback: `"$env:LOCALAPPDATA\agy\bin\agy.exe" --help`

If `agy` is not installed or not authenticated, tell the user to install and sign in to Antigravity CLI first.

## 2. Discover Available Models

Before choosing a model (or if the user asks which models are available), run:
```bash
agy models
```

## 3. Run Non-Interactive Tasks (`--print` / `-p`)

Always use `-p` (`--print`) when calling `agy` from Claude so it runs non-interactively and returns the output:

```bash
agy -p "Your prompt here"
```

### Useful Flags
- **Select model:** `agy -p "..." --model <model-id>`
- **Reasoning effort:** `--effort <low|medium|high|xhigh|max>`
- **Execution mode:**
  - `--mode plan` (read-only / planning)
  - `--mode accept-edits` (apply file edits)
  - `--mode auto` (autonomous execution)
- **Continue last conversation:** `agy -c -p "Follow-up prompt"`
- **Add workspace directory:** `--add-dir "/path/to/project"`
- **Structured output:** `--output-format <text|json|stream-json>`

## 4. Safety Rules

- Default to read-only or `--mode plan` unless the user explicitly asks `agy` to modify files or run commands.
- Never use `--dangerously-skip-permissions` unless the user explicitly requests it.
- Never print, read, or commit credential files from `~/.gemini` or `~/.claude`.
