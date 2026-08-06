# OpenAI Codex Features (Apr 2025 – Jul 2026)

Significant user-facing features added to OpenAI Codex since its public availability.
**Last updated:** Aug 2, 2026 · Source: [GitHub Releases](https://github.com/openai/codex/releases)

## Agentic & Multi-Agent

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Multi-Agent V2 (Configurable Sub-Agent Models & Reasoning) | Stabilizes the opt-in multi-agent v2 runtime with per-sub-agent model and reasoning-effort selection, concurrency limits, and restored agent roles | `multi_agent_v2` config / `spawn_agent` | `0.145.0` | Jul 2026 |
| Multi-Agent Delegation Mode Controls | Lets app-server clients configure multi-agent delegation as disabled, explicit-request-only, or proactive at the thread and turn level | App-server API / `agents` config | `0.142.0` | Jun 2026 |
| [Goals Workflow](https://developers.openai.com/codex/use-cases/follow-goals) | Tracks persistent goals with dedicated storage and progress across turns; supports create, pause, resume, and clear; enabled by default from v0.133.0 | `/goal` | `0.128.0` | Apr 2026 |
| [/side Conversations](https://developers.openai.com/codex/cli/slash-commands) | Opens a quick-question side conversation without interrupting or losing context from the active session thread | `/side` | `0.122.0` | Apr 2026 |
| [Thread Forking](https://developers.openai.com/codex/subagents) | Branches an active conversation into a new sub-agent thread while keeping the parent session intact | App-server API | `0.107.0` | Mar 2026 |
| [Multi-Agent Workflows](https://developers.openai.com/codex/subagents) | Spawns and coordinates sub-agent conversations programmatically with messaging, control, and path-based inter-agent communication | `spawn_agent` tool | `0.79.0` | Jan 2026 |
| Parallel Tool Calls | Executes multiple model-requested tool calls simultaneously in a single turn for faster multi-step operations | Automatic | `0.59.0` | Nov 2025 |

## Context & Memory

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Persisted Thread Names & Paginated History (experimental) | Adds paginated thread history with efficient resume, full-text occurrence search, user-assigned persisted names, and cross-thread memories | Session resume picker (experimental) | `0.145.0` | Jul 2026 |
| [Session Delete](https://developers.openai.com/codex/cli/slash-commands) | Permanently removes the current session transcript and all descendant sub-agent threads with confirmation safeguards | `codex delete` / `/delete` / `thread/delete` | `0.140.0` | Jun 2026 |
| [Unified @ Mentions Menu](https://developers.openai.com/codex/cli/features) | Opens a single fuzzy-search picker for files, directories, plugins, and skills when `@` is typed in the composer | `@` in TUI composer | `0.140.0` | Jun 2026 |
| [Session Archive](https://developers.openai.com/codex/cli/slash-commands) | Archives the current session to protect it from resume or fork until explicitly restored; reversible via unarchive | `/archive` / `codex archive` / `codex unarchive` | `0.136.0` | Jun 2026 |
| [Conversation History Search](https://developers.openai.com/codex/cli/features) | Searches all local sessions with case-insensitive content matching and result previews | Session resume picker | `0.134.0` | May 2026 |
| [Cross-Session Memory](https://developers.openai.com/codex/memories) | Stores persistent thread summaries as memory across sessions with TUI commands to view, update, and delete entries | `/m_update`, `/m_drop` | `0.97.0` | Feb 2026 |
| [Project-Aware Config Layering](https://developers.openai.com/codex/config-basic) | Loads repo-local `.codex/config.toml` and merges it with user and system configs for per-project settings | `.codex/config.toml` | `0.78.0` | Jan 2026 |
| [Automatic Context Compaction](https://developers.openai.com/codex/prompting) | Compacts the conversation context automatically when nearing token limits to keep long sessions alive | Automatic (configurable threshold) | `0.36.0` | Sep 2025 |
| [Session Resume](https://developers.openai.com/codex/cli/features) | Resumes previous sessions from an interactive picker or jumps directly to the most recent session | `codex resume` / `--resume` / `--continue` | `0.30.0` | Sep 2025 |
| [AGENTS.md Project Config](https://developers.openai.com/codex/guides/agents-md) | Reads `AGENTS.md` files from the project directory up to the git root for per-project agent instructions | `AGENTS.md` file | `0.24.0` | Aug 2025 |
| [/compact Command](https://developers.openai.com/codex/cli/slash-commands) | Manually compacts the current conversation context to free up token budget mid-session | `/compact` | `0.11.0` | Aug 2025 |

## Model & Input

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Indexed Web-Search Mode](https://developers.openai.com/codex/cli/features) | Adds a web-search mode that permits live searches while restricting direct page access to server-approved URLs only | `web_search = "indexed"` in config | `0.142.0` | Jun 2026 |
| Scheduled Time Reminders | Lets Codex receive scheduled UTC time reminders and query the current time directly, including via client-provided app-server clocks | App-server clock config | `0.142.0` | Jun 2026 |
| [Voice Input Transcription](https://developers.openai.com/codex/cli/features) | Dictates prompts via microphone by holding spacebar; speech is transcribed and sent directly to the model | Hold spacebar in TUI | `0.105.0` | Feb 2026 |
| JavaScript REPL | Provides a persistent JavaScript runtime with state surviving across turns and support for local module imports | `js_repl` in `config.toml` | `0.100.0` | Feb 2026 |
| Steer Mode (Mid-Turn Interrupt) | Interrupts a running model turn with `Ctrl+C` to redirect or refine the current task before the model completes it | `Ctrl+C` during turn | `0.98.0` | Feb 2026 |
| [Local Image Viewing (`view_image`)](https://developers.openai.com/codex/cli/features) | Lets Codex agentically inspect local image files and incorporate their visual content into reasoning and responses | Automatic tool | `0.26.0` | Aug 2025 |
| [Image Input (Paste & Drag-Drop)](https://developers.openai.com/codex/cli/features) | Attaches images to prompts by pasting from the clipboard or dragging image files onto the terminal | Paste / drag-drop | `0.24.0` | Aug 2025 |
| Long-Running Shell Commands | Maintains persistent shell processes with interactive stdin and streaming stdout via dedicated `exec_command` and `write_stdin` tools | Automatic tool | `0.24.0` | Aug 2025 |
| [Web Search](https://developers.openai.com/codex/cli/features) | Queries the web in real time during a session to access up-to-date information beyond the model's training data | `--search` flag | `0.24.0` | Aug 2025 |
| [Reasoning Effort Control](https://developers.openai.com/codex/cli/slash-commands) | Adjusts the model's reasoning effort level at runtime using a picker to trade off speed vs. depth mid-session | `/model` slash command | `0.23.0` | Aug 2025 |
| [Open-Weight Model Support](https://developers.openai.com/codex/models) | Enables use of open-weight OSS models from OpenAI (e.g., gpt-oss) as the active model in the CLI | `--oss` flag | `0.13.0` | Aug 2025 |

## Built-in Workflows

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [/usage Token Activity Views](https://developers.openai.com/codex/cli/slash-commands) | Shows daily, weekly, and cumulative account token activity and allows redeeming earned usage-limit reset credits | `/usage` | `0.140.0` | Jun 2026 |
| [/import External Agent Import](https://developers.openai.com/codex/cli/slash-commands) | Selectively imports setup, project configuration, and recent chats from Claude Code into the current Codex environment; expanded to migrate MCP servers, plugins, sessions, and memories from Claude Code and Cursor in `0.145.0` | `/import` | `0.140.0` | Jun 2026 |
| [/review Command](https://developers.openai.com/codex/cli/slash-commands) | Performs built-in code review against a specific commit, branch diff, or custom instructions without leaving the session | `/review` | `0.39.0` | Sep 2025 |

## Extensibility

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [MCP Tool Search](https://developers.openai.com/codex/mcp) | Lets the model search across available MCP tools instead of loading the full tool list into context, improving compatibility with large toolsets and older models/providers; enabled by default from `0.143.0` | Automatic (MCP config) | `0.142.2` | Jun 2026 |
| Plugin Catalog Sections & Turn Recommendations | Organizes remote plugins into OpenAI Curated, Workspace, and Shared sections; eligible turns can recommend and install relevant plugins automatically | `/plugins` | `0.142.0` | Jun 2026 |
| Executor Plugin MCP Activation | Activates stdio MCP servers from selected executor plugins on a per-thread basis; plugin discovery adds a created-by-me marketplace and auth-specific curated catalogs | Plugin config / `/plugins` | `0.141.0` | Jun 2026 |
| [MCP Apps (Resources & File Uploads)](https://developers.openai.com/codex/mcp) | Extends MCP servers to expose resources, accept file uploads, and return rich tool-call metadata to Codex | MCP server config | `0.119.0` | Apr 2026 |
| [Lifecycle Hooks Engine](https://developers.openai.com/codex/hooks) | Executes custom shell commands on `SessionStart`, `Stop`, and `userpromptsubmit` events for pre-execution prompt filtering and automation | `hooks` in `config.toml` | `0.114.0` | Mar 2026 |
| [Plugin System](https://developers.openai.com/codex/plugins) | Installs and manages plugins for skills, MCP servers, and app connectors from marketplace or local sources with authentication and version controls | `/plugins` | `0.110.0` | Mar 2026 |
| [Skills Support](https://developers.openai.com/codex/skills) | Injects reusable skill files from `~/.codex/prompts` or `.agents/skills` into sessions to guide agent behavior with named invocations | `$skill-name` / `/skills` | `0.65.0` | Dec 2025 |
| [`!<cmd>` Direct Shell Execution](https://developers.openai.com/codex/cli/features) | Executes shell commands directly from the TUI prompt, bypassing the model's planning step | `!<command>` in TUI | `0.52.0` | Oct 2025 |
| [MCP Streamable HTTP & OAuth](https://developers.openai.com/codex/mcp) | Connects to MCP servers over streamable HTTP with optional OAuth login, bearer tokens, and per-server environment targeting | `codex mcp add <url>` | `0.46.0` | Oct 2025 |
| Custom Prompt Files | Loads reusable named prompts with positional and named arguments from `~/.codex/prompts` for repeatable workflows | `$prompt-name` / `/prompts` | `0.26.0` | Aug 2025 |
| [MCP Client](https://developers.openai.com/codex/mcp) | Connects to external MCP servers to extend Codex with tools, resources, and capabilities from third-party services | `codex mcp` / `config.toml` | `0.9.0` | Jul 2025 |

## Platforms & Environments

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| System Proxy Support (PAC/WPAD) | Routes Codex authentication and Responses API traffic through macOS and Windows system proxies using PAC/WPAD auto-configuration, static proxy settings, and bypass rules; began as Windows-only opt-in auth support before covering both platforms and all traffic in `0.143.0` | `respect_system_proxy` config | `0.142.1` | Jun 2026 |
| [/app Desktop Handoff](https://developers.openai.com/codex/cli/slash-commands) | Hands off the current CLI thread into Codex Desktop on macOS and native Windows, opening directly into the Desktop app | `/app` | `0.138.0` | Jun 2026 |
| Remote-Control Pairing Management | Lets remote-control clients start pairing and list or revoke controller grants through app-server v2 RPCs | App-server v2 API | `0.137.0` | Jun 2026 |
| [/status Remote Connection Details](https://developers.openai.com/codex/remote-connections) | Shows remote connection details and server version when the TUI is connected over a remote transport | `/status` | `0.135.0` | May 2026 |
| [`codex doctor`](https://developers.openai.com/codex/cli/reference) | Runs comprehensive diagnostics covering runtime, auth, terminal, Git, network, and configuration for support troubleshooting | `codex doctor` | `0.131.0` | May 2026 |
| [Python SDK (`openai-codex`)](https://developers.openai.com/codex/sdk) | Official Python package with first-class authentication (API key, ChatGPT, device-code), concurrent turn routing, and sandbox presets | `pip install openai-codex` | `0.131.0` | May 2026 |
| [`codex remote-control`](https://developers.openai.com/codex/remote-connections) | Exposes a running Codex session to external interfaces and devices, adding a remote interaction surface via the local app-server | `codex remote-control` | `0.130.0` | May 2026 |
| Amazon Bedrock Integration | Connects to Amazon Bedrock as a built-in model provider with AWS SigV4 authentication and AWS credential profile support | `provider = "amazon-bedrock"` in config | `0.123.0` | Apr 2026 |
| Realtime Voice Sessions | Enables full WebRTC audio sessions with the model including voice selection and transcript output; extended to local audio file input and audio tool-call outputs via streaming realtime V3 in `0.145.0` | Realtime config | `0.119.0` | Apr 2026 |
| [App-Server Filesystem RPCs](https://developers.openai.com/codex/app-server) | Exposes file read, write, copy, directory operations, and path watching via the v2 app-server API for IDE-style integrations | App-server v2 API | `0.115.0` | Mar 2026 |
| [App-Server WebSocket Transport](https://developers.openai.com/codex/app-server) | Provides bidirectional WebSocket connectivity for the app-server protocol enabling persistent IDE and tooling integrations | App-server WebSocket endpoint | `0.100.0` | Feb 2026 |
| [Ctrl+G External Editor](https://developers.openai.com/codex/cli/features) | Opens the current TUI prompt in `$VISUAL`/`$EDITOR`, allows free-form editing, and syncs changes back on save | `Ctrl+G` | `0.78.0` | Jan 2026 |
| macOS DMG Distribution | Packages Codex as a macOS `.dmg` app bundle for direct installation outside of npm or Homebrew | GitHub Releases (macOS DMG) | `0.76.0` | Dec 2025 |
| [`codex exec-server`](https://developers.openai.com/codex/app-server) | Exposes a headless HTTP/WebSocket execution API for running Codex tasks from external tooling and CI pipelines | `codex exec-server` | `0.59.0` | Nov 2025 |
| [`codex cloud exec`](https://developers.openai.com/codex/cloud) | Runs tasks in cloud-hosted environments with remote branch support and diff/apply workflows | `codex cloud exec` | `0.44.0` | Oct 2025 |
| [TypeScript SDK (`@openai/codex-sdk`)](https://developers.openai.com/codex/sdk) | Provides a programmatic TypeScript API for embedding Codex in applications with image support, working directory, and AbortSignal | `npm install @openai/codex-sdk` | `0.42.0` | Sep 2025 |
| [`codex exec --output-schema`](https://developers.openai.com/codex/noninteractive) | Enforces a JSON Schema on `codex exec` output for structured pipeline automation and machine-readable results | `codex exec --output-schema <file>` | `0.41.0` | Sep 2025 |
| Android / Termux Support | Runs Codex CLI natively on Android devices via the Termux terminal environment | `npm install @openai/codex` on Termux | `0.29.0` | Sep 2025 |

## Security & Governance

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [`writes` App-Approval Mode](https://developers.openai.com/codex/permissions) | Adds an app-approval mode that lets declared read-only actions proceed automatically while still requiring explicit approval for write actions | App-approval config (`writes` mode) | `0.144.0` | Jul 2026 |
| Rollout Token Budgets | Configures token budgets that track usage across agent threads, provide remaining-budget reminders, and abort turns when exhausted | `token_budget` in config | `0.142.0` | Jun 2026 |
| Noise Relay Encrypted Remote Execution | Uses authenticated, end-to-end encrypted Noise relay channels for all remote executor connections | Automatic for remote executors | `0.141.0` | Jun 2026 |
| Managed Bedrock Auth & Encrypted Credential Storage | Adds managed Amazon Bedrock API-key authentication and encrypted local storage for CLI and MCP OAuth credentials | `bedrock` auth config | `0.140.0` | Jun 2026 |
| Enterprise Credit Limits & Cloud-Managed Config Bundles | Lets enterprise and EDU admins view monthly credit limits and apply cloud-managed configuration bundles to managed workspaces | Admin console / `requirements.toml` | `0.137.0` | Jun 2026 |
| [Windows Admin Sandbox Setup](https://developers.openai.com/codex/windows) | Provides `codex sandbox setup --elevated` for admin-provisioned Windows sandbox with dedicated low-privilege users, filesystem boundaries, and firewall rules | `codex sandbox setup --elevated` | `0.136.0` | Jun 2026 |
| [Permission Profiles](https://developers.openai.com/codex/permissions) | Defines named permission configurations that persist across TUI sessions, MCP operations, and shell escalation flows | `--profile <name>` | `0.124.0` | Apr 2026 |
| [Linux Sandbox](https://developers.openai.com/codex/concepts/sandboxing) | Isolates subprocess filesystem access on Linux using bubblewrap/Landlock with configurable read-only mount paths | Automatic on Linux | `0.81.0` | Jan 2026 |
| Enterprise MDM Config | Deploys Codex configuration to macOS fleets via MDM TOML payload, merged with repo and global config layers | macOS MDM profile | `0.78.0` | Jan 2026 |
| [`requirements.toml` Managed Settings](https://developers.openai.com/codex/agent-approvals-security) | Constrains permitted sandbox modes, network access, and security policies for managed or enterprise deployments | `/etc/codex/requirements.toml` | `0.76.0` | Dec 2025 |
| [ExecPolicy Command Whitelisting](https://developers.openai.com/codex/cli/reference) | Whitelists command prefixes in the TUI approval flow so subsequent similar commands run without re-prompting | TUI approval UI | `0.66.0` | Dec 2025 |
| [Windows Sandbox](https://developers.openai.com/codex/windows) | Restricts filesystem and network access for agent mode on native Windows, matching parity with macOS sandboxing | Automatic on Windows | `0.59.0` | Nov 2025 |
| [`--add-dir` Writable Roots](https://developers.openai.com/codex/cli/features) | Specifies additional working directories writable by Codex subprocesses beyond the default project root | `--add-dir <path>` | `0.48.0` | Oct 2025 |
| [/approvals Runtime Control](https://developers.openai.com/codex/agent-approvals-security) | Adjusts which command categories require explicit approval during a session without restarting | `/approvals` | `0.23.0` | Aug 2025 |
| [`--ask-for-approval on-request`](https://developers.openai.com/codex/agent-approvals-security) | Adds a balanced approval mode where the model itself decides whether a given command needs user confirmation | `--ask-for-approval on-request` | `0.16.0` | Aug 2025 |
| [Sandbox Configuration](https://developers.openai.com/codex/concepts/sandboxing) | Controls filesystem and network access sandboxing for all subprocess execution within a session | `--sandbox <mode>` | `0.3.0` | Jul 2025 |

## Other Improvements

Notable changes that fell below the threshold for the main tables:

- Session naming at creation (`/new`, `/clear`) and `/session rename` (`0.146.0`) - *incremental improvement*
- Thread pinning (`0.146.0`) - *convenience wrapper*
- Side conversation switching without closing (`0.146.0`) - *incremental improvement*
- Thread forking with paginated history and temporary forks (`0.146.0`) - *incremental improvement*
- Plugin workspace publishing and Amazon Bedrock / Claude Code marketplaces (`0.146.0`) - *distribution channel*
- App-server remote Code Mode hosts over WebSocket (experimental) (`0.146.0`) - *incremental improvement*
- Standalone web search for custom model providers (`0.146.0`) - *platform expansion*
- OpenAI-hosted release infrastructure with GitHub fallback (`0.146.0`) - *distribution channel*
- macOS helper executable signing and notarization (`0.146.0`) - *security infrastructure*
- Enterprise-plan recognition and admin controls for in-app updates (`0.146.0`) - *config knob*
- Improved dangerous-command detection and clearer rejection reasons (`0.144.5`) - *incremental improvement*
- Usage-limit reset credit type/expiration selection (`0.144.0`) - *incremental improvement*
- Interactive MCP tool authentication without experimental opt-in (`0.144.0`) - *preview→GA, nothing new*
- App-server runtime authentication provisioning and login redirects (`0.144.0`) - *incremental improvement*
- pnpm global install detection (`0.144.0`) - *convenience wrapper*
- Ultra reasoning concurrency usage warning (`0.144.0`) - *UI polish*
- ChatGPT-hosted MCP servers explicit session authentication (`0.143.0`) - *config knob*
- Remote plugin catalog default-on with npm marketplace sources and version indicators (`0.143.0`) - *distribution channel*
- `codex remote-control pair` manual pairing codes (`0.143.0`) - *convenience wrapper*
- Amazon Bedrock GPT-5.6 Sol/Terra/Luna models with max reasoning effort (`0.143.0`) - *incremental improvement*
- App-server environment inspection, descendant thread listing, and turn-level history forking (`0.143.0`) - *incremental improvement*
- Plugin dark-mode logo support (`0.142.2`) - *UI polish*
- Safety-buffering UI with server-provided visibility metadata (`0.142.2`) - *UI polish*
- PowerShell executable AST region approval requirement (`0.142.2`) - *incremental improvement*
- Remote plugin catalog featured-plugin rankings (`0.142.2`) - *incremental improvement*
- `/usage` credit redemption UI (`0.142.0`) - *incremental improvement*
- TUI input prompt auto-resolution timer (`0.141.0`) - *UI polish*
- Realtime speech append and startup context controls (`0.141.0`) - *incremental improvement*
- Cross-platform remote execution native cwd/shell preservation (`0.141.0`) - *incremental improvement*
- App-server child thread listing and agent import correlation (`0.141.0`) - *incremental improvement*
- Plugin automation `--json` flags for add/remove/marketplace commands (`0.138.0`) - *format/scripting flag*
- `/app` reasoning effort TUI fallback shortcuts (`0.138.0`) - *incremental improvement*
- Local image attachments expose file paths to model (`0.138.0`) - *incremental improvement*
- App-server account token usage read and v2 personal access tokens (`0.138.0`) - *incremental improvement*
- `codex doctor` editor/pager environment details (`0.139.0`) - *incremental improvement*
- Plugin marketplace `--json` with source field (`0.139.0`) - *format/scripting flag*
- Code mode standalone web search from JS tool calls (`0.139.0`) - *incremental improvement*
- `/goal` oversized text and image attachment preservation (`0.140.0`) - *incremental improvement*
- App-server MCP stdio mode (`codex app-server --stdio`) (`0.136.0`) - *convenience wrapper*
- Remote execution `CODEX_API_KEY` registration for approved hosts (`0.136.0`) - *security infrastructure*
- Standalone image generation extension (`0.136.0`) - *preview, feature-gated*
- F13-F24 keybindings and paste in TUI menus (`0.137.0`) - *power-user UX*
- Enterprise parallel web search in code mode (`0.137.0`) - *incremental improvement*
- Multi-agent v2 runtime thread controls and spawn defaults (`0.137.0`) - *incremental improvement*
- `codex plugin list --json` (`0.137.0`) - *format/scripting flag*
- `codex doctor` richer environment and thread diagnostics (`0.135.0`) - *incremental improvement*
- `/permissions` named profile display (`0.135.0`) - *incremental improvement*
- Vim mode text-object editing and interrupt binding (`0.135.0`) - *power-user UX*
- Python SDK `Sandbox` presets (`0.135.0`) - *convenience wrapper*
- `CODEX_NON_INTERACTIVE=1` install mode (`0.135.0`) - *config knob*
- Vim mode in TUI composer (`0.129.0`) - *power-user UX preference, not a new capability*
- `codex update` command (`0.128.0`) - *convenience wrapper for updating via the package manager*
- winget publishing (`0.113.0`) - *distribution channel expansion with no feature change*
- `/fast` service tier toggle (`0.110.0`) - *config knob for an existing model-provider option*
- Syntax highlighting in TUI (`0.105.0`) - *UI polish*
- Theme picker (`0.105.0`) - *UI preference knob*
- macOS binary notarization (`0.47.0`) - *security infrastructure, not a workflow feature*
- Ripgrep bundled in npm release (`0.41.0`) - *dependency packaging, not a capability addition*
- Rust CLI rewrite (`0.20.0`) - *purely internal implementation milestone with no new user-facing features*
- Append-to-terminal UI redesign (`0.11.0`) - *significant interaction change but no new capability*
- Streaming model responses (`0.8.0`) - *improvement to existing behavior, not a new capability*
- `codex exec --json` JSONL output (`0.8.0`) - *format flag on an existing command*
