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

## Step 4 — Triage: table row, Other Improvements, or drop

Every changelog entry gets exactly **one** of three outcomes. Decide in order — stop at the first that matches.

**Invocation method is irrelevant.** Automatic, slash command, config key, or flag — none of it affects the outcome. The only question is what the change lets a user do.

### A · Table row

Keep as a full feature row if it adds something users could not do before. Any one of:

- **New capability class** — an input type, web search, background agents, voice
- **New integration surface** — a new platform, IDE, chat app, cloud provider, or external system it now works with
- **New extensibility primitive** — hooks, plugins, MCP, custom agents, skills, slash-command authoring, SDK
- **New built-in workflow** — code review, autofix, modernization, plan mode, commit-message generation
- **Workflow paradigm shift** — named sessions, auto-memory, worktree isolation, task tracking, autonomous goals
- **New security or governance control** — sandboxing, permission modes, managed settings, BYOK, data residency

### B · Other Improvements bullet

A *named, real* change that falls below the table bar but a tracking reader still wants to know shipped. Pick exactly one reason per bullet — this is the full reason vocabulary (Step 6 reuses it):

- *UI polish* — animation, theme, rendering, syntax highlighting
- *config knob* — an option that tunes an existing feature
- *format/scripting flag* — `--json`, output schema, an alias exposing an existing command
- *convenience wrapper* — a shortcut for an already-documented capability
- *incremental improvement* — "better/faster X", an enhancement to an existing feature
- *platform expansion* — an existing feature reaching another IDE or OS
- *distribution channel* — a new install/package channel with no feature change
- *security infrastructure* — notarization, signing (not a user-facing control)
- *preview→GA, nothing new* — a maturity milestone that added no capability
- *power-user UX* — vim mode, keybinding presets

**Model releases collapse into one bullet** — never list individual model GAs separately. Emit a single line, e.g. `Model releases (GPT-5.x, Claude 4.x, Gemini 3) — tracked separately`.

### C · Drop — record nowhere

Pure noise, omitted from the doc entirely: bug/crash fixes, performance changes with no behavior change, internal refactors with no user-facing surface, typo and documentation edits.

### Calibration — paired examples

Same axis, opposite outcome. Use these to settle borderline calls:

| Axis | A · table row | B · Other Improvements |
|------|---------------|------------------------|
| Command | `/code-review` (new built-in workflow) | `/tui` toggle (config knob) |
| Session | Session Recap (new return-context workflow) | "Summarize up to here" (incremental improvement) |
| Input | PDF reading (new input class) | 1M context window default (capacity bump) |
| Speed | Fast Mode (new cost/speed tradeoff) | `xhigh` effort level (knob increment) |
| Worktree | Worktree isolation (new paradigm) | `worktree.bgIsolation:"none"` (config knob) |
| Surface | Push notifications (new distribution surface) | status-line PR info (incremental improvement) |

## Step 5 — Categorize

Place each feature in exactly one of these **seven** categories. They are written in presentation order — **Security & Governance is always last**. When a feature could fit multiple, use the **tie-breaker precedence** below.

| Category | What belongs here |
|----------|-------------------|
| **Agentic & Multi-Agent** | Background/parallel/multi-agent, workflows, worktree isolation, task tracking, autonomous goals, monitors, agent dashboards |
| **Context & Memory** | Memory across sessions, project config files, instructions, session resume/recap, named sessions, auto-compaction, spaces, context-retrieval search |
| **Model & Input** | Multimodal/image, PDF, voice, web search/fetch, thinking mode, real-time steering, effort/fast speed knobs, model selection |
| **Built-in Workflows** | Code review, autofix, app modernization, next-edit suggestions, plan mode, commit-message generation, one-click fixes |
| **Extensibility** | Hooks, plugins, MCP, custom agents, skills, slash-command authoring, SDK, output styles, channels, elicitation |
| **Platforms & Environments** | Desktop/mobile apps, IDE integrations, browser, cloud providers, OS support, distribution, remote control, SDK streaming, CLI modes, chat-app agent surfaces |
| **Security & Governance** | Sandboxing, permission modes, managed/enterprise settings, MDM, BYOK, data residency, FedRAMP, content exclusion, budget tracking, model rules, control plane |

**Tie-breaker precedence** (first match wins):

1. Security/permission/sandbox/enterprise-policy **mode or setting** (not authored via a hook/plugin) → **Security & Governance**
2. Hook / plugin / MCP / skill / custom-agent / slash-authoring / SDK primitive → **Extensibility**
3. Coordinates or monitors multiple agents/background processes → **Agentic & Multi-Agent**
4. Tool-provided end-to-end workflow (review, autofix, modernize, plan, commit-gen) → **Built-in Workflows**
5. Needs a model-level capability (input type, reasoning mode, web, voice, model/speed) → **Model & Input**
6. New runtime environment, distribution, or integration surface → **Platforms & Environments**
7. Otherwise → **Context & Memory**

Order matters: rule 1 before rule 2 routes enterprise-managed plugins → Governance, not Extensibility; rule 1 before rule 6 routes OS-specific sandboxes → Governance, not Platforms; rule 4 before rule 5 routes code-review commands → Built-in Workflows, not Model & Input.

**Canonical resolved examples:**

| Feature | Category | Reason |
|---------|----------|--------|
| Auto mode / safety classifier | Security & Governance | Permission mode, not a model feature |
| Subprocess sandboxing | Security & Governance | Security/trust control |
| Enterprise managed settings / BYOK / data residency | Security & Governance | Governance policy |
| `/code-review`, `/ultrareview`, Copilot code review | Built-in Workflows | Tool-provided workflow (rule 4 beats rule 5) |
| Copilot autofix / app modernization | Built-in Workflows | Tool-provided workflow, not a governance control |
| Monitor tool | Agentic & Multi-Agent | Streams background agent/script output |
| Custom agents / subagents | Extensibility | Primitive developers define (rule 2; not a security mode) |
| PermissionRequest hook | Extensibility | Authored via a hook (rule 2 beats rule 1) |
| Linux / Windows sandbox | Security & Governance | Security control (rule 1 beats rule 6) |
| Remote Control | Platforms & Environments | New distribution surface (browser/mobile) |

## Step 6 — Write the output

Create or update `docs/<assistant>-features.md` in place. Follow this format exactly:

**File header:**
```markdown
# <Display Name> Features (<first month year> – <last month year>)

Significant user-facing features added to <Display Name> since its public availability.
**Last updated:** <current month year> · Source: [<source label>](<primary source URL>)
```

Update the date range in the title if the newest feature extends it. Always update "Last updated" to the current month and year.

**Section headers:** Use the seven category names exactly as written above (`## Agentic & Multi-Agent`, `## Context & Memory`, etc.), in the Step 5 order — **Security & Governance always last**.

**Table format** (one table per section, five columns):
```markdown
| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
```

- **Title**: plain text, or `[Title](url)` if a confirmed URL exists; for a feature that shipped as preview then GA, fold both into one row and note `(GA Mmm YYYY)` after the title
- **Description**: one sentence, present tense, factual — what it does, not why it's good
- **Invocation**: the shortest accurate way to use it (command, flag, config key, or "Automatic")
- **Version**: backtick-wrapped, e.g. `` `2.1.154` `` or `` `v0.135.0` ``; use `N/A` for tools not version-tracked per release
- **Date**: `Mon YYYY` format, e.g. `May 2026`

**Row ordering**: date descending within each table (newest at top). When two features share the same month, order by version number descending.

**Merge strategy for updates**: preserve all existing rows. Insert new rows in the correct date position. Do not remove existing rows unless they are factually wrong. Do not rewrite existing descriptions unless they are inaccurate.

**Other Improvements section**: After the seven category tables, append a final section for the **Outcome B** items from Step 4 — named changes considered but kept below the table bar (an audit trail, so re-runs don't re-evaluate them). Use this format exactly:

```markdown
## Other Improvements

Notable changes that fell below the threshold for the main tables:

- Title (`version`) - *reason it was omitted*
- Title (`version`) - *reason it was omitted*
```

- One bullet per item, no description — only title, version, and omission reason
- Order by version number descending (highest first)
- The omission reason **must** be one phrase drawn from the Step 4 · B reason vocabulary — do not invent new phrasings
- **Collapse all individual model releases into a single bullet** (`Model releases (…) — tracked separately`); never list them one per line
- Outcome C items (bug fixes, perf, refactors, typos) do **not** appear here

## Step 7 — Validate before writing

Before writing the output file, run through this checklist:

1. **No duplicate features**: If the same feature appears under two different names or categories, merge into one row using the most accurate version number from the npm registry. Example: "Custom agents" and "Custom Subagents" are the same feature. Also collapse **preview→GA** announcements of the same feature into one row, dated at first ship, with `(GA Mmm YYYY)` noted in the title; keep a second row only if GA added new capability.
2. **Version/date accuracy**: For every row, confirm the version exists in the npm `time` map and the date matches. Fix any that don't.
3. **No config-only entries**: Review every row — if it represents only a settings knob or scripting alias with no new user workflow, re-triage it per Step 4 (Outcome B or C).
4. **Coverage sanity check**: Every major version series (e.g. `2.1.x`, `2.0.x`, `1.0.x`, `0.2.x`) should contribute at least a few entries unless that series was purely bugfixes. If a series has zero entries, explicitly verify this against the changelog before finalizing.
5. **Category consistency**: For every row, confirm it matches the canonical tie-breaker rules from Step 5. Re-check any feature that could fit multiple categories.
