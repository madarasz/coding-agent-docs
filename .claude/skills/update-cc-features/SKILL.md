---
name: update-cc-features
description: Produces or updates docs/claude-code-features.md with the latest significant Claude Code features. Use when the user asks to refresh, update, or regenerate the Claude Code features document.
---

# Update Claude Code Features Document

Update `docs/claude-code-features.md` with new significant features from the Claude Code changelog.

## Step 1 — Fetch the changelog

Fetch the raw changelog in full:

```
https://raw.githubusercontent.com/anthropics/claude-code/refs/heads/main/CHANGELOG.md
```

The file is ~350KB. Read all version sections from the newest down to the last version already captured in `docs/claude-code-features.md` (check the oldest date in the file). Only sections newer than that date need to be processed.

## Step 2 — Map versions to dates

The changelog contains only version numbers, not dates. Fetch release dates from npm:

```
https://registry.npmjs.org/@anthropic-ai/claude-code
```

Extract the `time` object. It maps every version string to an ISO timestamp. Use this to convert version numbers to `Mon YYYY` strings (e.g. `2.1.154` → `May 2026`).

Version series and their approximate date ranges for orientation:
- `0.2.x` — Feb–May 2025 (research preview)
- `1.0.x` — May–Sep 2025
- `2.0.x` — Sep 2025–Jan 2026
- `2.1.x` — Jan 2026–present

## Step 3 — Find official URLs

For each new feature, look up the best available URL in this priority order:

1. **Anthropic news post** — `https://www.anthropic.com/news/<slug>` — use when a feature was announced alongside a model launch or major product announcement. Confirmed working slugs: `model-context-protocol`, `claude-3-7-sonnet`, `claude-4`, `claude-opus-4-5`.
2. **Official docs page** — `https://code.claude.com/docs/en/<page>` — use for features with dedicated documentation. Fetch `https://code.claude.com/docs/llms.txt` to discover all available page slugs without guessing. Confirmed pages include: `agent-view`, `hooks`, `memory`, `mcp`, `settings`, `skills`, `sub-agents`, `worktrees`, `chrome`, `channels`, `remote-control`, `sandboxing`, `plugins`, `azure-ai-foundry`, `cli-reference`, `commands`, `agent-sdk/overview`, `desktop`.
3. **No link** — leave the title as plain text if no relevant URL can be confirmed. Do not guess or invent URLs.

## Step 4 — Filter: what to keep vs. discard

### Keep a feature if it is

- A **new capability class**: something users couldn't do at all before (e.g. web search, background agents, multimodal input)
- A **new integration surface**: a new platform, environment, or external system Claude Code now works with (e.g. Desktop app, Chrome extension, Azure Foundry)
- A **new extensibility primitive**: hooks, plugin system features, MCP scoping, custom agents, slash command authoring — things developers build on top of
- A **workflow paradigm shift**: changes *how* you work, not just polish (e.g. named sessions, auto-memory, worktree isolation)
- A **security or trust architecture** feature that matters to teams or enterprises (e.g. managed settings, subprocess sandboxing, permission hooks)
- A **developer API milestone**: SDK features that unlock new programmatic usage patterns

### Discard a feature if it is

- **UI/UX polish**: keybindings, animations, autocomplete improvements, rendering fixes, fuzzy matching
- **Model releases**: individual Claude model versions (these are Anthropic product news, not Claude Code features)
- **Incremental improvements**: "better error messages", "faster startup", "improved display of X" — improvements to things already in the doc
- **Platform-specific bug fixes**: Windows/WSL/CJK rendering, IDE compatibility patches
- **Settings flags for existing behavior**: env vars and config knobs that tune things already present
- **Convenience aliases**: `/settings` as alias for `/config`, `/undo` as alias for `/rewind`
- **Minor observability additions**: OpenTelemetry attributes, status line JSON fields, log events
- **Gray area — apply judgment**: keep a slash command if it enables a previously-impossible workflow (`/ultrareview`, `/goal`); discard it if it's a convenience wrapper (`/recap`, `/powerup`)

## Step 5 — Assign to a category

Place each feature in exactly one of these five categories. When a feature could fit multiple, use the primary user intent.

| Category | What belongs here |
|----------|-------------------|
| **Agentic & Multi-Agent** | Features about running, coordinating, or monitoring multiple agents or autonomous sessions: background agents, worktrees, workflows, agent view, /goal, monitors |
| **Context & Memory** | Features about what Claude knows and remembers across a session or project: CLAUDE.md, auto-memory, @-mentions, session resume, named sessions, auto-compaction, rules |
| **Model Capabilities** | Features about what Claude can perceive, reason about, or produce: thinking mode, multimodal, web search, WebFetch, real-time steering, /code-review |
| **Extensibility & Control** | Features about extending Claude's behavior (hooks, plugins, MCP config, custom agents, slash command authoring) and controlling what it's allowed to do (permissions, managed settings, sandboxing, auto mode) |
| **Platforms & Environments** | Features about where Claude Code runs or how it connects to external systems: Desktop app, Chrome, IDE integrations, cloud providers, SDK streaming, channels, native binary, CLI modes |

## Step 6 — Write the output

Update `docs/claude-code-features.md` in place. Follow the existing format exactly:

**File header:**
```markdown
# Claude Code Features (<first month year> – <last month year>)

Significant user-facing features added to Claude Code since the research preview.
**Last updated:** <current month year> · Source: [CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)
```

Update the date range in the title if the newest feature extends it. Always update "Last updated" to the current month and year.

**Section headers:** Use the five category names exactly as written above (`## Agentic & Multi-Agent`, `## Context & Memory`, etc.).

**Table format** (one table per section, five columns):
```markdown
| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
```

- **Title**: plain text, or `[Title](url)` if a confirmed URL exists
- **Description**: one sentence, present tense, factual — what it does, not why it's good
- **Invocation**: the shortest accurate way to use it (command, flag, config key, or "Automatic")
- **Version**: backtick-wrapped, e.g. `` `2.1.154` ``
- **Date**: `Mon YYYY` format, e.g. `May 2026`

**Row ordering**: date descending within each table (newest at top). When two features share the same month, order by version number descending.

**Merge strategy for updates**: preserve all existing rows. Insert new rows in the correct date position. Do not remove existing rows unless they are factually wrong. Do not rewrite existing descriptions unless they are inaccurate.
