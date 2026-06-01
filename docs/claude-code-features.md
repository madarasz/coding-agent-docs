# Claude Code Features (Feb 2025 – May 2026)

Significant user-facing features added to Claude Code since the research preview.
**Last updated:** June 2026 · Source: [CHANGELOG.md](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md)

---

## Agentic & Multi-Agent

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Dynamic Workflows](https://code.claude.com/docs/en/agent-view) | Orchestrate tens-to-hundreds of parallel agents automatically | Ask Claude to "create a workflow"; `/workflows` | `2.1.154` | May 2026 |
| [Agent view dashboard](https://code.claude.com/docs/en/agent-view) | Unified view of all running, blocked, and completed sessions | `claude agents` | `2.1.139` | May 2026 |
| [/goal command](https://code.claude.com/docs/en/commands) | Set a completion condition; Claude keeps working until it's met | `/goal <condition>` | `2.1.139` | May 2026 |
| [/ultrareview](https://code.claude.com/docs/en/commands) | Cloud-based multi-agent parallel code review | `/ultrareview` or `claude ultrareview` | `2.1.111` | Apr 2026 |
| Monitor tool | Stream events from background scripts; get notified when done | `Monitor` tool in Claude's toolset | `2.1.98` | Apr 2026 |
| [Git worktree isolation](https://code.claude.com/docs/en/worktrees) | Agents and sessions run in isolated git worktrees | `--worktree` / `isolation: worktree` in agent | `2.1.49` | Feb 2026 |
| [Background agents](https://code.claude.com/docs/en/agent-view) | Agents run asynchronously while you continue working | `&` prefix or `claude --bg` | `2.0.60` | Dec 2025 |
| Task/Todo list | Claude tracks structured tasks for multi-step work | Automatic; Claude creates/updates tasks | `0.2.93` | May 2025 |

---

## Context & Memory

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Auto-memory](https://code.claude.com/docs/en/memory) | Claude automatically saves useful context to project memory | Automatic; manage with `/memory` | `2.1.59` | Mar 2026 |
| [Named sessions](https://code.claude.com/docs/en/cli-reference) | Name, rename, and resume sessions by name | `/rename <name>`, `claude --resume <name>` | `2.0.64` | Dec 2025 |
| [`.claude/rules/` directory](https://code.claude.com/docs/en/memory) | Conditional context rules with `paths:` frontmatter | Create `.claude/rules/my-rule.md` | `2.0.64` | Dec 2025 |
| [CLAUDE.md imports](https://code.claude.com/docs/en/memory) | Modular project context via `@path/to/file.md` in CLAUDE.md | Add `@path/to/file.md` to `CLAUDE.md` | `0.2.107` | May 2025 |
| [Session resume](https://code.claude.com/docs/en/cli-reference) | Continue past conversations across restarts | `claude --continue` / `claude --resume` | `0.2.93` | May 2025 |
| [@-mention files](https://code.claude.com/docs/en/memory) | Reference any file directly in your prompt | `@filename` | `0.2.75` | Apr 2025 |
| [Auto-compaction](https://code.claude.com/docs/en/memory) | Automatic summarization enables infinite conversation length | Automatic; toggle via `/config` | `0.2.47` | Mar 2025 |

---

## Model Capabilities

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [/code-review](https://code.claude.com/docs/en/commands) | Structured code review with optional automatic fix application | `/code-review` or `/code-review --fix` | `2.1.147` | May 2026 |
| Real-time steering | Send messages to Claude while it's still working | Type and press `Enter` mid-run | `0.2.108` | May 2025 |
| Web search | Claude can search the web for live information | Automatic; Claude triggers it | `0.2.105` | May 2025 |
| Multimodal input (images) | Paste, drag, or @-mention images into prompts | `Ctrl+V`, drag, or `@image.png` | `0.2.59` | Apr 2025 |
| WebFetch tool | Claude can read and analyze URLs | Paste URL in prompt | `0.2.53` | Apr 2025 |
| [Thinking mode](https://www.anthropic.com/news/claude-3-7-sonnet) | Extended reasoning via "think harder" / "ultrathink" | Say `think`, `think harder`, or `ultrathink` in prompt | `0.2.44` | Mar 2025 |

---

## Extensibility & Control

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [MessageDisplay hook](https://code.claude.com/docs/en/hooks) | Transform or suppress assistant message text as displayed | `hooks.MessageDisplay` in settings | `2.1.152` | May 2026 |
| [Plugin auto-load from `.claude/skills`](https://code.claude.com/docs/en/plugins) | Local plugins load without a marketplace | Create `.claude/skills/<plugin>/` | `2.1.157` | May 2026 |
| [PostToolUse output replacement](https://code.claude.com/docs/en/hooks) | Hooks can rewrite tool output before Claude sees it | `hookSpecificOutput.updatedToolOutput` | `2.1.121` | Apr 2026 |
| [MCP tool-type hooks](https://code.claude.com/docs/en/hooks) | Hooks that invoke MCP tools directly | `type: "mcp_tool"` in hooks | `2.1.118` | Apr 2026 |
| Auto mode (safety classifier) | Permission mode using AI safety classification instead of prompts | `Shift+Tab` cycle or `defaultMode: "auto"` | `2.1.111` | Apr 2026 |
| [Subprocess sandboxing](https://code.claude.com/docs/en/sandboxing) | Bash tool processes run in isolated PID namespaces on Linux | `CLAUDE_CODE_SUBPROCESS_ENV_SCRUB=1` | `2.1.98` | Apr 2026 |
| [Plugin background monitors](https://code.claude.com/docs/en/plugins) | Plugins arm background monitoring scripts at session start | `monitors:` in `plugin.json` | `2.1.105` | Apr 2026 |
| [HTTP hooks](https://code.claude.com/docs/en/hooks) | Hooks that POST JSON to a URL instead of running a shell command | `type: "http"` in hooks config | `2.1.63` | Mar 2026 |
| [MCP wildcard permissions](https://code.claude.com/docs/en/mcp) | Allow/deny all tools from an MCP server at once | `mcp__server__*` in permissions | `2.0.70` | Dec 2025 |
| [Enterprise managed settings](https://code.claude.com/docs/en/settings) | IT policy enforcement via `managed-settings.json` | Deploy to system dirs | `2.0.68` | Dec 2025 |
| [Custom agents](https://code.claude.com/docs/en/sub-agents) | Define agents with system prompts, tool restrictions, and models | `--agent <name>` or `agent:` in settings | `2.0.59` | Dec 2025 |
| [PermissionRequest hook](https://code.claude.com/docs/en/hooks) | Auto-approve or deny tool permissions with custom logic | `hooks.PermissionRequest` in settings | `2.0.45` | Nov 2025 |
| [Output styles (plugin system)](https://code.claude.com/docs/en/plugins) | Plugins can ship custom response formatting styles | Via plugin install | `2.0.41` | Nov 2025 |
| [SlashCommand tool](https://code.claude.com/docs/en/skills) | Claude can invoke your custom slash commands programmatically | Claude uses it automatically | `1.0.23` | Jun 2025 |
| [Dynamic MCP headers](https://code.claude.com/docs/en/mcp) | Per-request custom headers for MCP servers via script | `headersHelper` in MCP server config | `1.0.119` | Sep 2025 |
| [Shared project permissions](https://code.claude.com/docs/en/settings) | Team-wide tool allow/deny rules in `.claude/settings.json` | Edit `.claude/settings.json` | `0.2.67` | Apr 2025 |
| [MCP project scope](https://www.anthropic.com/news/model-context-protocol) | Commit MCP server configs to repo in `.mcp.json` | `claude mcp add --scope project` | `0.2.50` | Mar 2025 |
| [Custom slash commands](https://code.claude.com/docs/en/skills) | `.md` files in `.claude/commands/` become slash commands | `/your-command` | `0.2.31` | Mar 2025 |

---

## Platforms & Environments

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Push notifications (mobile)](https://code.claude.com/docs/en/remote-control) | Claude sends push notifications to your phone via Remote Control | Enable in `/config` | `2.1.110` | Apr 2026 |
| Fullscreen TUI renderer | Flicker-free full-terminal rendering mode | `/tui fullscreen` | `2.1.110` | Apr 2026 |
| Native binary | Compiled native binary replaces bundled JavaScript | Automatic in new installs | `2.1.113` | Apr 2026 |
| PowerShell tool (Windows) | Native PowerShell as primary shell tool on Windows | Automatic on Windows; opt in with `CLAUDE_CODE_USE_POWERSHELL_TOOL=1` | `2.1.113` | Apr 2026 |
| [--channels (research preview)](https://code.claude.com/docs/en/channels) | MCP servers can push messages into your active session | `--channels` flag | `2.1.80` | Mar 2026 |
| [claude.ai MCP connectors](https://code.claude.com/docs/en/mcp) | Use cloud service connectors (Slack, Gmail, etc.) from claude.ai | Automatic when logged into claude.ai | `2.1.46` | Feb 2026 |
| LSP (Language Server) tool | Code intelligence: go-to-definition, find references, hover docs | Automatic with configured LSP servers | `2.0.74` | Dec 2025 |
| [Claude in Chrome](https://code.claude.com/docs/en/chrome) | Control your browser directly from Claude Code | Chrome extension at claude.ai/chrome | `2.0.72` | Dec 2025 |
| [Desktop App](https://www.anthropic.com/news/claude-opus-4-5) | Native macOS/Windows app | Download from claude.com/download | `2.0.51` | Nov 2025 |
| [Azure AI Foundry](https://code.claude.com/docs/en/azure-ai-foundry) | Use Claude Code via Microsoft Azure AI Foundry | Set Foundry env vars | `2.0.45` | Nov 2025 |
| [Streaming SDK output](https://code.claude.com/docs/en/agent-sdk/overview) | SDK streams partial messages in real-time | `--include-partial-messages` | `1.0.109` | Sep 2025 |
| [Streaming print mode](https://code.claude.com/docs/en/cli-reference) | `--print` mode with real-time JSON output for scripting | `claude -p --output-format=stream-json` | `0.2.66` | Apr 2025 |
