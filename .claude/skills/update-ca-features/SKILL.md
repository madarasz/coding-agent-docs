---
name: update-ca-features
description: Produces or updates a coding-assistant features doc in docs/<assistant>-features.md. Use when the user asks to refresh, update, or regenerate features for Claude Code, Codex, GitHub Copilot, Cursor, Gemini CLI, Windsurf, or OpenCode.
---

# Update Coding Assistant Features Document

Update `docs/<assistant>-features.md` with new significant features from the target coding assistant's changelog.

## Step 0 — Identify the target

If the user has not specified which coding assistant to update, ask them. Accepted values and their output files:

| Input | Display Name | Output file |
|-------|-------------|-------------|
| `claude-code` | Claude Code | `docs/claude-code-features.md` |
| `codex` | OpenAI Codex | `docs/codex-features.md` |
| `copilot` | GitHub Copilot | `docs/copilot-features.md` |
| `cursor` | Cursor | `docs/cursor-features.md` |
| `gemini-cli` | Gemini CLI | `docs/gemini-cli-features.md` |
| `windsurf` | Windsurf | `docs/windsurf-features.md` |
| `opencode` | OpenCode | `docs/opencode-features.md` |

If the output file already exists, read the oldest date in the file to determine the cutoff — only process entries newer than that date.

## Step 1 — Fetch the changelog

Use the primary source for the target assistant. Fetch from the newest entries down to the cutoff date determined in Step 0.

| Assistant | Primary Source | Method |
|-----------|---------------|--------|
| **Claude Code** | `https://raw.githubusercontent.com/anthropics/claude-code/refs/heads/main/CHANGELOG.md` | WebFetch (raw markdown, ~350 KB) |
| **Codex** | `https://api.github.com/repos/openai/codex/releases` | GitHub API via Bash |
| **GitHub Copilot** | `https://docs.github.com/en/copilot/about-github-copilot/github-copilot-changelog` | WebFetch (rendered page) |
| **Cursor** | `https://cursor.com/changelog` | WebFetch (rendered page) |
| **Gemini CLI** | `https://www.geminicli.com/docs/changelogs` | WebFetch (rendered page) |
| **Windsurf** | `https://windsurf.com/changelog` | WebFetch (rendered page) |
| **OpenCode** | `https://api.github.com/repos/anomalyco/opencode/releases` | GitHub API via Bash |

**For GitHub-hosted tools (Codex, OpenCode) — use the GitHub Releases API:**

The API returns structured JSON with version, date, and release notes in one call — far more reliable than scraping the rendered releases page. Run this Bash command (paginate with `&page=2` if the cutoff hasn't been reached):

```bash
curl -s "https://api.github.com/repos/<owner>/<repo>/releases?per_page=100" \
  | python3 -c "
import json, sys
for r in json.load(sys.stdin):
    if not r['prerelease']:
        print(f\"## {r['tag_name']} ({r['published_at'][:10]})\n{r['body']}\n\")
"
```

Stop processing once you pass the cutoff date from Step 0. Because `published_at` is included in the response, **skip the npm date lookup in Step 2 for these tools**.

**For Claude Code — handle large changelogs:**
The file may be too large to process in one pass. If the response is truncated, make additional fetches to cover the missing range. Process version blocks from newest to oldest and stop once you reach the cutoff version/date from Step 0. Do not skip sections — if a fetch is incomplete, explicitly fetch the missing range before proceeding.

## Step 2 — Map versions to dates

**GitHub API tools (Codex, OpenCode):** Dates are already in `published_at` from Step 1 — no additional lookup needed.

**For Claude Code and Gemini CLI**, fetch the `time` object from the npm registry to convert version numbers to `Mon YYYY` strings:

| Assistant | npm registry URL |
|-----------|-----------------|
| Claude Code | `https://registry.npmjs.org/@anthropic-ai/claude-code` |
| Gemini CLI | `https://registry.npmjs.org/@google/gemini-cli` |

Use this Bash command to extract stable versions with their dates:

```bash
curl -s "<registry-url>" | python3 -c "
import json, sys
t = json.load(sys.stdin).get('time', {})
stable = [(v, ts) for v, ts in t.items()
          if v not in ('created', 'modified') and '-' not in v]
for v, ts in sorted(stable, key=lambda x: x[1], reverse=True)[:50]:
    print(f'{v}: {ts}')
"
```

Format timestamps as `Mon YYYY` (e.g. `"2026-05-14T10:22:00.000Z"` → `May 2026`). If a version is absent, use the nearest lower version present.

**Web-only changelogs (Copilot, Cursor, Windsurf):** Dates are embedded in the page content — extract them directly from the rendered text.

## Step 3 — Find official URLs

For each new feature, find the best available URL in this priority order:

1. **Dedicated docs page** for the feature (most useful — explains the feature with examples)
2. **Official announcement post** on the assistant's blog or news page (use for features with no docs page yet)
3. **No link** — leave the title as plain text if no relevant URL can be confirmed. Do not guess or invent URLs.

**Never link to GitHub release pages** (e.g. `github.com/*/releases/tag/*`) — they contain raw changelogs, not explanatory content. If no better URL exists, leave the title as plain text.

Per-assistant docs and blog roots:

| Assistant | Docs root | Blog / news |
|-----------|-----------|-------------|
| Claude Code | `https://code.claude.com/docs/en/` | `https://www.anthropic.com/news/` |
| Codex | `https://developers.openai.com/codex/` | `https://openai.com/blog/` |
| GitHub Copilot | `https://docs.github.com/en/copilot/` | `https://github.blog/changelog/` |
| Cursor | `https://docs.cursor.com/` | `https://cursor.com/blog/` |
| Gemini CLI | `https://www.geminicli.com/docs/` | `https://blog.google/products/gemini/` |
| Windsurf | `https://docs.windsurf.com/` | `https://windsurf.com/blog/` |
| OpenCode | `https://opencode.ai/docs` | `https://github.com/anomalyco/opencode` |

### Known URL patterns by assistant

**Claude Code** — docs are at `https://code.claude.com/docs/en/<topic>`. Confirmed sections:
`agent-view`, `worktrees`, `session-recap`, `cli-reference`, `memory`, `hooks`, `plugins`, `sandboxing`, `channels`, `keybindings`, `mcp`, `commands`, `skills`, `fast-mode`, `chrome`, `azure-ai-foundry`, `remote-control`, `agent-sdk/overview`

**Codex** — docs are at `https://developers.openai.com/codex/<topic>`. Confirmed sections:
`cli/features`, `cli/slash-commands`, `cli/reference`, `memories`, `memories/chronicle`, `config-basic`, `config-advanced`, `config-reference`, `prompting`, `subagents`, `concepts/subagents`, `concepts/sandboxing`, `concepts/sandboxing/auto-review`, `permissions`, `mcp`, `plugins`, `plugins/build`, `hooks`, `skills`, `rules`, `guides/agents-md`, `agent-approvals-security`, `models`, `sdk`, `noninteractive`, `remote-connections`, `app-server`, `windows`, `cloud`, `workflows`, `use-cases/<slug>` (55+ use-case articles at `https://developers.openai.com/codex/use-cases/`)

**GitHub Copilot** — most feature announcements live at `https://github.blog/changelog/<date>-<slug>/`. Docs at `https://docs.github.com/en/copilot/<topic>`.

## Step 4 — Filter: what to keep vs. discard

**Invocation method is irrelevant to the keep/discard decision.** Whether a feature is triggered automatically, via a slash command, a config key, or a flag does not affect its eligibility. The only question is: does this represent a significant improvement to the coding workflow?

### Keep a feature if it is

- A **new capability class**: something users couldn't do at all before (e.g. web search, background agents, multimodal input)
- A **new integration surface**: a new platform, environment, or external system it now works with
- A **new extensibility primitive**: hooks, plugins, MCP config, custom agents, slash command authoring — things developers build on top of
- A **workflow paradigm shift**: changes *how* you work, not just polish (e.g. named sessions, auto-memory, worktree isolation, task/todo tracking)
- A **security or trust architecture** feature that matters to teams or enterprises (e.g. managed settings, sandboxing, permission controls)
- A **developer API milestone**: SDK features that unlock new programmatic usage patterns

**Borderline kept — use these as anchors:**

| Feature | Reason kept |
|---------|-------------|
| Session Recap (`/recap`) | New workflow: returning to a session with a context summary — users couldn't get this before |
| Push notifications via Remote Control | New integration surface: mobile notifications |
| PDF Reading | New input type class |
| `/code-review` | Built-in command enabling a previously-manual workflow |
| Fast Mode | Changes the cost/speed tradeoff in a user-configurable way |
| Task/Todo list | Creates a visible, structured artifact that changes how users track multi-step work — workflow paradigm shift |

### Discard a feature if it is

- **UI/UX polish**: animations, autocomplete improvements, rendering fixes
- **Model releases**: individual model version bumps (product news, not tool features)
- **Incremental improvements**: "better error messages", "faster startup", "improved display of X"
- **Platform-specific bug fixes**: OS/IDE compatibility patches, e.g. ARM64 binaries, musl/Alpine support
- **Config knobs / flags for existing features**: options that tune existing behavior without enabling new workflows — e.g. `worktree.bgIsolation: "none"`, `--json` output format flags, `--bare` headless mode, effort level increments (`xhigh`)
- **Scripting aliases**: `--json` output or similar flags that expose existing commands in a new format without unlocking new workflows
- **Invocation convenience only**: syntax shortcuts for capabilities already documented (e.g. `@-mention files` when file referencing is already covered)
- **Minor observability additions**: telemetry attributes, log events, status fields
- **Gray area — apply judgment**: keep a command if it enables a previously-impossible workflow; discard if it's a convenience wrapper

## Step 5 — Categorize

Place each feature in exactly one of these five categories. When a feature could fit multiple, use the **tie-breaker precedence** below.

| Category | What belongs here |
|----------|-------------------|
| **Agentic & Multi-Agent** | Background agents, worktrees, workflows, multi-agent coordination, autonomous sessions, monitors |
| **Context & Memory** | Memory across sessions, project-level config files, session resume, named sessions, auto-compaction |
| **Model Capabilities** | Thinking mode, multimodal input, web search, real-time steering, built-in code review |
| **Extensibility & Control** | Hooks, plugins, MCP config, custom agents, slash command authoring, permissions, sandboxing, auto mode |
| **Platforms & Environments** | Desktop apps, IDE integrations, browser extensions, cloud providers, SDK streaming, CLI modes |

**Tie-breaker precedence** (when a feature fits multiple categories):

1. If it's a permission/safety/trust architecture → **Extensibility & Control**
2. If it primarily coordinates or monitors multiple agents/background processes → **Agentic & Multi-Agent**
3. If it requires model-level capability to function (new input type, reasoning mode, built-in command) → **Model Capabilities**
4. If it adds a new runtime environment or distribution channel → **Platforms & Environments**
5. Otherwise → **Context & Memory**

**Canonical resolved examples:**

| Feature | Category | Reason |
|---------|----------|--------|
| Auto mode / safety classifier | Extensibility & Control | Permission architecture, not a model feature |
| Monitor tool | Agentic & Multi-Agent | Used to stream background agent/script output |
| `/ultrareview` | Model Capabilities | Primary intent is running a code review, not orchestrating agents |
| Subprocess sandboxing | Extensibility & Control | Security/trust architecture |
| Remote Control | Platforms & Environments | New distribution surface (browser/mobile) |
| Custom agents / subagents | Extensibility & Control | Extensibility primitive developers define and configure |

## Step 6 — Write the output

Create or update `docs/<assistant>-features.md` in place. Follow this format exactly:

**File header:**
```markdown
# <Display Name> Features (<first month year> – <last month year>)

Significant user-facing features added to <Display Name> since its public availability.
**Last updated:** <current month year> · Source: [<source label>](<primary source URL>)
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
- **Version**: backtick-wrapped, e.g. `` `2.1.154` `` or `` `v0.135.0` ``; use `N/A` for tools not version-tracked per release
- **Date**: `Mon YYYY` format, e.g. `May 2026`

**Row ordering**: date descending within each table (newest at top). When two features share the same month, order by version number descending.

**Merge strategy for updates**: preserve all existing rows. Insert new rows in the correct date position. Do not remove existing rows unless they are factually wrong. Do not rewrite existing descriptions unless they are inaccurate.

**Other Improvements section**: After the five category tables, append a final section for notable items that were considered but didn't meet the bar for the main tables. Use this format exactly:

```markdown
## Other Improvements

Notable changes that fell below the threshold for the main tables:

- Title (`version`) - *reason it was omitted*
- Title (`version`) - *reason it was omitted*
```

- One bullet per item, no description — only title, version, and omission reason
- Order by version number descending (highest first)
- Omission reason should be a short phrase, not a sentence explaining what the feature does
- Typical reasons: *UI polish*, *config knob for an existing feature*, *improvement to existing behavior*, *convenience wrapper*, *distribution channel expansion*, *security infrastructure*, *purely internal implementation change*

## Step 7 — Validate before writing

Before writing the output file, run through this checklist:

1. **No duplicate features**: If the same feature appears under two different names or categories, merge into one row using the most accurate version number from the npm registry. Example: "Custom agents" and "Custom Subagents" are the same feature.
2. **Version/date accuracy**: For every row, confirm the version exists in the npm `time` map and the date matches. Fix any that don't.
3. **No config-only entries**: Review every row — if it represents only a settings knob or scripting alias with no new user workflow, re-apply discard criteria.
4. **Coverage sanity check**: Every major version series (e.g. `2.1.x`, `2.0.x`, `1.0.x`, `0.2.x`) should contribute at least a few entries unless that series was purely bugfixes. If a series has zero entries, explicitly verify this against the changelog before finalizing.
5. **Category consistency**: For every row, confirm it matches the canonical tie-breaker rules from Step 5. Re-check any feature that could fit multiple categories.
