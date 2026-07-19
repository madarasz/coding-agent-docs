# OpenCode Features (Jun 2025 – Jul 2026)

Significant user-facing features added to OpenCode since its public availability.
**Last updated:** Jul 2026 · Source: [GitHub Releases](https://github.com/anomalyco/opencode/releases)

## Agentic & Multi-Agent

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Background subagents | Running subagents can be sent to the background so the user can keep working in the same session. | Automatic / `opencode run` | `v1.16.2` | Jun 2026 |
| [Experimental background agents](https://opencode.ai/docs/agents/) | Subagent tasks can keep running independently while the user continues a primary session. | `experimental.background` config | `v1.14.51` | May 2026 |
| [Scout agent](https://opencode.ai/docs/agents/) | Built-in repo-research agent for codebase navigation, docs lookup, and dependency-source inspection. | `@scout` mention | `v1.14.42` | May 2026 |
| [Session forking](https://opencode.ai/docs/cli/) | Creates a new session branching from an existing conversation, including fork from Desktop. | `opencode` API / Desktop | `v1.1.13` | Jan 2026 |
| [Task tool / subagents](https://opencode.ai/docs/agents/) | Built-in task tool lets the primary agent spin up subtask child sessions to delegate work. | Automatic (agent-initiated) | `v1.0.120` | Nov 2025 |
| [Worktree isolation](https://opencode.ai/docs/tui/) | Sessions can be created inside git worktrees to isolate parallel work from the main workspace. | `opencode` in a worktree | `v0.13.6` | Oct 2025 |
| [Session warp between workspaces](https://opencode.ai/docs/tui/) | Moves a running session into another workspace or back to the local project, optionally carrying uncommitted changes. | TUI command palette | `v1.14.37` | May 2026 |
| [Session replay](https://opencode.ai/docs/cli/) | Interactive session replay with `run --replay` shows recent history when resuming past runs. | `opencode run --replay` | `v1.16.0` | Jun 2026 |
| Subagents & agents system | Agents and modes are unified — a single `agent` field defines the primary agent; `@mention` spawns subagents with optional auto-routing by description. | `agent` config key / `@mention` | `v0.4.0` | Aug 2025 |

## Context & Memory

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [MCP resource tools](https://opencode.ai/docs/mcp/) | MCP resource templates and resource read tools are now available to agents as standard tools. | Automatic (MCP config) | `v1.17.10` | Jun 2026 |
| [Pinned sessions with quick-switch slots](https://opencode.ai/docs/tui/) | Sessions can be pinned for fast recall; the TUI exposes quick-switch key slots for the most recent pinned sessions. | TUI session picker | `v1.15.1` | May 2026 |
| [Agent skills](https://opencode.ai/docs/skills/) | Skills are markdown-based instruction sets loadable from `.opencode/skills/`, `.agents/skills/`, or well-known URLs; invokable as slash commands. | `/skillname` or `@mention` | `v1.1.48` | Jan 2026 |
| [Native skill tool](https://opencode.ai/docs/skills/) | Dedicated skill tool with a permission system so agents can invoke skills as structured tool calls. | Automatic | `v1.0.190` | Dec 2025 |
| [References system](https://opencode.ai/docs/references/) | External context references (docs, repos, files) can be configured and `@`-mentioned to inject their content into the session. | `@reference` config | `v1.1.1` | Jan 2026 |
| [Automatic context compaction](https://opencode.ai/docs/config/) | Long sessions are automatically summarized when the context window fills, preserving recent turns verbatim. | Automatic / `OPENCODE_DISABLE_AUTOCOMPACT` | `v0.8.0` | Sep 2025 |
| [AGENTS.md / project instructions](https://opencode.ai/docs/rules/) | Per-project instruction files (`AGENTS.md`, `CLAUDE.md`) loaded from the workspace root for persistent project rules. | File-based | `v0.3.90` | Jul 2025 |
| [JSONC configuration](https://opencode.ai/docs/config/) | Configuration files accept JSONC (JSON with comments) and support schema autocomplete via `opencode.jsonc`. | `opencode.jsonc` file | `v0.3.100` | Jul 2025 |
| [SQLite session storage](https://opencode.ai/docs/config/) | Session data migrated from flat files to a single SQLite database for faster loading and filtering. | Automatic (migration on first run) | `v1.2.0` | Feb 2026 |
| [Session metadata API](https://opencode.ai/docs/sdk/) | Sessions can store and retrieve custom metadata through the API and SDK. | SDK / HTTP API | `v1.15.13` | May 2026 |
| [Config-dir cascade](https://opencode.ai/docs/config/) | Config loads from the opened directory upward so directory-specific settings and provider policies apply predictably. | Automatic | `v1.15.13` | May 2026 |

## Model & Input

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Video and audio input (Gemini) | Gemini models can receive video and audio media as message attachments. | File attachment | `v1.17.10` | Jun 2026 |
| [Web search tool](https://opencode.ai/docs/tools/) | Built-in websearch tool (backed by Exa) lets agents fetch live search results. | Automatic (agent-initiated) | `v0.3.112` | Aug 2025 |
| [Image input / paste](https://opencode.ai/docs/tui/) | Users can paste images (Ctrl+V), webp previews, and file paths; agents read and process image attachments. | Ctrl+V / file attachment | `v0.0.51` | May 2025 |
| [PDF attachment support](https://opencode.ai/docs/tui/) | PDF files can be attached to prompts for models that support document input. | File attachment | `v1.15.7` | May 2026 |
| [Thinking / reasoning blocks](https://opencode.ai/docs/config/) | Extended-thinking output is rendered inline as collapsible blocks; toggle persists across the session. | Automatic / toggle | `v1.0.120` | Nov 2025 |
| [Adaptive thinking levels](https://opencode.ai/docs/config/) | Users can select thinking effort variants (none / low / medium / high / max / xhigh) per model. | Model variant picker | `v1.0.115` | Nov 2025 |
| [Model variants](https://opencode.ai/docs/models/) | Provider-specific model variants (reasoning effort levels, fast/nano) selectable per session or in config. | Tab or variant picker | `v0.4.5` | Aug 2025 |
| [Web fetch tool](https://opencode.ai/docs/tools/) | Agents can fetch and read web page content as part of task execution; permission prompts shown before each fetch. | Automatic (agent-initiated) | `v0.4.5` | Aug 2025 |
| [Fast mode variants](https://opencode.ai/docs/config/) | Fast/nano model variants for Claude and GPT provide lower-cost alternatives with a single toggle. | Model variant picker | `v1.4.3` | Apr 2026 |
| [Directory read tool](https://opencode.ai/docs/tools/) | The read tool can now open and list directory contents in addition to reading files. | Automatic (agent-initiated) | `v1.1.60` | Feb 2026 |

## Built-in Workflows

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Git-backed session review](https://opencode.ai/docs/share/) | Session review shows uncommitted changes and branch diffs from git, with a synchronized desktop review pane. | Desktop review panel | `v1.3.0` | Mar 2026 |
| [Diff viewer (TUI)](https://opencode.ai/docs/tui/) | In-TUI diff viewer with a file tree, hunk navigation, and comparison against the main branch. | TUI keybind / command palette | `v1.15.6` | May 2026 |
| [/review built-in command](https://opencode.ai/docs/commands/) | Built-in `/review` slash command asks the agent to review uncommitted changes and detect behavior-changing edits. | `/review` | `v1.1.57` | Feb 2026 |
| [Plan mode](https://opencode.ai/docs/agents/) | A dedicated plan agent that can read and explore but not modify files, enabling safe pre-work analysis. | `--agent plan` / agent config | `v0.4.0` | Aug 2025 |
| [Session sharing](https://opencode.ai/docs/share/) | Sessions can be published to a public share page with configurable auto/disabled sharing. | `/share` | `v0.3.2` | Jul 2025 |
| [Snapshot and undo](https://opencode.ai/docs/tui/) | Git-backed snapshots are taken before each edit; users can revert messages to restore any prior file state. | TUI revert / undo | `v0.3.82` | Jul 2025 |
| [Formatter integration](https://opencode.ai/docs/formatters/) | After file edits the agent automatically runs configured formatters (e.g. prettier, black, cargo fmt, biome). | Automatic / `formatter` config | `v0.3.105` | Jul 2025 |
| [Todo list tool](https://opencode.ai/docs/tools/) | Built-in todoread/todowrite tools let agents track and display task lists within a session. | Automatic (agent-initiated) | `v0.10.0` | Sep 2025 |
| [Structured output](https://opencode.ai/docs/sdk/) | Claude agent SDK-style structured outputs available via the OpenCode SDK for typed results. | SDK | `v1.1.60` | Feb 2026 |
| [export --sanitize](https://opencode.ai/docs/cli/) | `opencode export --sanitize` redacts PII and confidential data from session transcripts. | `opencode export --sanitize` | `v1.4.4` | Apr 2026 |

## Extensibility

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Code mode MCP adapter](https://opencode.ai/docs/mcp/) | Agents can run confined orchestration scripts that call multiple connected MCP tools programmatically through a hidden `execute` tool, instead of invoking tools one at a time. | Config toggle (enables `execute` tool) | `v1.17.14` | Jul 2026 |
| [V2 plugin API](https://opencode.ai/docs/plugins/) | New Effect- and Promise-based plugin API with namespaced hook APIs and TUI plugin support. | `@opencode-ai/plugin` | `v1.17.10` | Jun 2026 |
| [MCP server support](https://opencode.ai/docs/mcp/) | Full MCP server integration with OAuth auth flows, timeout management, `cwd` support, and catalog pagination. | `mcp` config section | `v0.3.76` | Jul 2025 |
| [Custom slash commands](https://opencode.ai/docs/commands/) | User-defined slash commands with `$ARGUMENTS` substitution, `@file` references, and mode-specific execution. | `/commandname` | `v0.0.49` | May 2025 |
| [Plugin system](https://opencode.ai/docs/plugins/) | JavaScript/TypeScript plugins can register providers, tools, hooks, and agents; installed from npm or local files. | `.opencode/plugins/` | `v0.3.129` | Aug 2025 |
| [SDK](https://opencode.ai/docs/sdk/) | TypeScript/JavaScript SDK (`@opencode-ai/sdk`) for building integrations, custom tools, and workspace adaptors. | `@opencode-ai/sdk` npm package | `v0.5.13` | Aug 2025 |
| [LSP auto-discovery and integration](https://opencode.ai/docs/lsp/) | Automatically discovers and installs language servers for 20+ languages; configurable per project. | Automatic / `lsp` config | `v0.0.45` | May 2025 |
| [Custom tools](https://opencode.ai/docs/tools/) | Users can define additional tools in config or via plugins that the agent can call. | `tools` config / plugin | `v0.10.0` | Sep 2025 |
| [Hooks](https://opencode.ai/docs/plugins/) | Plugin hook APIs expose lifecycle events (`chat.message`, `tool.definition`, `shell.env`, `compaction.autocontinue`) for programmatic control. | Plugin hook registration | `v1.1.50` | Feb 2026 |
| [ACP (Agent Client Protocol)](https://opencode.ai/docs/sdk/) | Protocol for integrating external clients (IDEs, CI) with a running opencode session over SSE/HTTP. | `acp` channel | `v0.15.10` | Oct 2025 |
| [GitHub Actions integration](https://opencode.ai/docs/github/) | Trigger opencode sessions from GitHub Actions workflows via `/oc` or `/opencode` comment commands. | GitHub Actions workflow | `v1.0.185` | Dec 2025 |
| [GitLab Agent Platform](https://opencode.ai/docs/gitlab/) | Full GitLab Agent Platform integration with WebSocket-based workflow models and local tool access. | GitLab config | `v1.3.0` | Mar 2026 |
| [Opencode-managed provider integrations](https://opencode.ai/docs/providers/) | First-class managed provider integration IDs exposed in the SDK and config for hosted model routing. | Config / SDK | `v1.17.10` | Jun 2026 |

## Platforms & Environments

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Desktop app (Electron)](https://opencode.ai/docs/ide/) | Native Electron desktop application with tabbed sessions, terminal pane, file tree, and mobile PWA support. | App download | `v0.9.1` | Sep 2025 |
| [WSL Desktop support](https://opencode.ai/docs/windows-wsl) | Desktop app integrates with WSL backends, including WSL server management and per-server session tabs on Windows. | Desktop / WSL | `v1.17.0` | Jun 2026 |
| [Web app / `opencode web`](https://opencode.ai/docs/web/) | Browser-based UI accessible via `opencode web` command for remote or headless server access. | `opencode web` | `v0.11.4` | Sep 2025 |
| [VS Code extension](https://opencode.ai/docs/ide/) | VS Code and VS Code Insiders extension that surfaces the TUI inside the editor with a dedicated keybinding. | VS Code extension | `v0.3.80` | Jul 2025 |
| [Slack integration](https://opencode.ai/docs/ecosystem/) | Slack bot package using the Bolt framework for driving opencode from Slack messages. | `@opencode-ai/slack` | `v0.15.4` | Oct 2025 |
| [Remote server / `opencode attach`](https://opencode.ai/docs/cli/) | `opencode attach` connects a TUI to a remote opencode server for headless or CI environments. | `opencode attach` | `v0.9.9` | Sep 2025 |
| [OpenTUI 1.0 rewrite](https://opencode.ai/docs/tui/) | Complete rewrite of the TUI from Go/Bubbletea to a Zig/SolidJS framework (OpenTUI) with a command bar and improved performance. | Automatic (upgrade) | `v1.0.0` | Oct 2025 |
| [Node.js runtime support](https://opencode.ai/docs/cli/) | opencode can run on Node.js in addition to Bun, broadening install compatibility. | `npx opencode` | `v1.3.0` | Mar 2026 |
| [Non-interactive / headless mode](https://opencode.ai/docs/cli/) | `opencode run` executes a single prompt non-interactively with `--json` output and tool-restriction flags. | `opencode run` | `v0.0.51` | May 2025 |
| [Mobile bottom navigation (PWA)](https://opencode.ai/docs/web/) | Desktop PWA gains a mobile-optimized bottom navigation bar and safe-area insets for iOS. | PWA on mobile | `v1.17.10` | Jun 2026 |
| [OTLP observability export](https://opencode.ai/docs/config/) | Exports AI SDK telemetry spans to any OTLP trace backend for session-level observability. | `otel` config | `v1.4.0` | Apr 2026 |

## Security & Governance

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Yolo mode](https://opencode.ai/docs/permissions/) | A permission mode that auto-approves all tool prompts while still honoring explicit deny rules, for users who fully trust agent actions. | TUI command palette (`Enable auto-approve permissions`) | `v1.17.12` | Jun 2026 |
| [Granular permission system](https://opencode.ai/docs/permissions/) | Per-tool permission rules with allow/deny/ask, wildcard pattern matching, and agent-level permission scopes. | `permission` config key | `v1.1.1` | Jan 2026 |
| [Plan Mode security boundary](https://opencode.ai/docs/agents/) | Plan mode agent enforces a read-only boundary so subagents cannot override parent-agent deny rules. | `--agent plan` config | `v1.14.46` | May 2026 |
| [macOS MDM managed preferences](https://opencode.ai/docs/enterprise/) | macOS managed preferences allow MDM-enforced configuration policies for enterprise deployments. | MDM plist / `enterprise` config | `v1.3.14` | Apr 2026 |
| [Server password authentication](https://opencode.ai/docs/network/) | HTTP server supports password authentication (`OPENCODE_SERVER_PASSWORD`) for protecting remote access. | `OPENCODE_SERVER_PASSWORD` env | `v1.1.15` | Jan 2026 |
| [Webfetch permission prompts](https://opencode.ai/docs/permissions/) | Web fetch requests require explicit permission approval before agents can access external URLs. | Permission dialog | `v0.4.5` | Aug 2025 |
| [bash tool sandboxing / cwd guard](https://opencode.ai/docs/permissions/) | Bash commands are parsed with tree-sitter to detect and block commands that navigate outside the project directory. | Automatic | `v0.3.90` | Jul 2025 |

## Other Improvements

Notable changes that fell below the threshold for the main tables:

- Home page command palette session search (`v1.18.3`) - *convenience wrapper*
- Configurable subagent nesting depth via `subagent_depth` (`v1.18.2`) - *config knob*
- Desktop v2 UI redesign completed, with legacy-layout toggle during transition (`v1.18.0`) - *preview→GA, nothing new*
- OpenAI pro reasoning mode support (`v1.17.19`) - *incremental improvement*
- xAI response storage disabled by default (`v1.17.19`) - *security infrastructure*
- OAuth support for Luna Responses Lite (`v1.17.19`) - *platform expansion*
- Per-prompt model selection in composer (`v1.17.19`) - *incremental improvement*
- Composer add menu for files/commands/context/shell mode (`v1.17.16`) - *convenience wrapper*
- Streamlined WSL server setup with distro checks and install flow (`v1.17.13`) - *platform expansion*
- SDK live event streaming and paged session history endpoints (`v1.17.12`) - *incremental improvement*
- Session cost/token totals shown in context panel (`v1.17.12`) - *incremental improvement*
- Session snapshot revert controls extended to roll back file changes (`v1.17.11`) - *incremental improvement*
- Chrome-style desktop tab-cycle shortcuts and draggable tabs (`v1.17.11`) - *power-user UX*
- `--mini` CLI mode (`v1.17.10`) - *config knob*
- MCP server instructions in context (`v1.17.10`) - *incremental improvement*
- Diff viewer hunk navigation (`v1.16.2`) - *incremental improvement*
- Snowflake Cortex provider (`v1.16.2`) - *platform expansion*
- Skill discovery and file-based agent loading (`v1.16.0`) - *incremental improvement*
- `run --replay` for session replay (`v1.16.0`) - *convenience wrapper*
- Workspace management dialog in TUI (`v1.15.12`) - *incremental improvement*
- Prompt size config (`v1.15.11`) - *config knob*
- Collapsed thinking inline view (`v1.15.1`) - *UI polish*
- DigitalOcean OAuth and Inference Router (`v1.14.49`) - *platform expansion*
- Scout agent repo-research skills (`v1.14.49`) - *incremental improvement*
- Customize-opencode built-in skill (`v1.14.46`) - *convenience wrapper*
- HTTP API response compression (`v1.14.42`) - *incremental improvement*
- OTLP telemetry spans (`v1.4.0`) - *config knob*
- Azure prompt caching (`v1.4.8`) - *incremental improvement*
- Fast mode variants for Claude/GPT (`v1.4.3`) - *config knob*
- Poe OAuth provider (`v1.3.1`) - *platform expansion*
- Venice AI provider (`v1.3.14`) - *platform expansion*
- PowerShell first-class support on Windows (`v1.3.7`) - *platform expansion*
- Multistep OAuth authentication flows (`v1.3.0`) - *incremental improvement*
- Interactive upgrade confirmation dialog (`v1.3.0`) - *UI polish*
- tool.definition hook for plugins (`v1.1.65`) - *incremental improvement*
- shell.env hook for environment manipulation (`v1.1.50`) - *incremental improvement*
- Skills as slash commands in TUI (`v1.1.48`) - *convenience wrapper*
- Session import command (`v1.0.30`) - *convenience wrapper*
- Custom themes from `.opencode/themes/` (`v1.0.60`) - *UI polish*
- Light mode TUI support (`v1.0.10`) - *UI polish*
- Favorites in model selector (`v1.0.115`) - *UI polish*
- Git branch display in TUI status bar (`v0.3.82`) - *UI polish*
- JSONC config file support (`v0.3.100`) - *config knob*
- Formatter config (enable/disable per formatter) (`v0.3.105`) - *config knob*
- Configurable permissions (allow/deny/wildcard) (`v0.3.102`) - *config knob*
- Session sharing auto/disabled config (`v0.3.2`) - *config knob*
- small_model config for title generation (`v0.3.10`) - *config knob*
- VertexAI provider support (`v0.0.50`) - *platform expansion*
- Non-interactive tool restriction flags (`v0.0.51`) - *config knob*
- Auto-compact / summarize for indefinite sessions (`v0.0.45`) - *incremental improvement*
- auto LSP discovery/configuration (`v0.0.45`) - *incremental improvement*
- Model releases (Claude Sonnet 4.6, Claude Opus 4.7+, GPT-5 series, Gemini 3.x, Kimi K2, GLM-5.2, Mistral, DeepSeek, etc.) — tracked separately
