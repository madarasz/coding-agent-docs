# OpenAI Codex Features (Apr 2025 – May 2026)

Significant user-facing features added to OpenAI Codex since its public availability.
**Last updated:** Jun 2026 · Source: [GitHub Releases](https://github.com/openai/codex/releases)

## Agentic & Multi-Agent

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Goals Workflow | Tracks persistent goals with dedicated storage and progress across turns; supports create, pause, resume, and clear; enabled by default from v0.133.0 | `/goal` | `0.128.0` | Apr 2026 |
| `/side` Conversations | Opens a quick-question side conversation without interrupting or losing context from the active session thread | `/side` | `0.122.0` | Apr 2026 |
| Thread Forking | Branches an active conversation into a new sub-agent thread while keeping the parent session intact | App-server API | `0.107.0` | Mar 2026 |
| Multi-Agent Workflows | Spawns and coordinates sub-agent conversations programmatically with messaging, control, and path-based inter-agent communication | `spawn_agent` tool | `0.79.0` | Jan 2026 |
| Parallel Tool Calls | Executes multiple model-requested tool calls simultaneously in a single turn for faster multi-step operations | Automatic | `0.59.0` | Nov 2025 |
| Session Resume | Resumes previous sessions from an interactive picker or jumps directly to the most recent session | `codex resume` / `--resume` / `--continue` | `0.30.0` | Sep 2025 |
| Long-Running Shell Commands | Maintains persistent shell processes with interactive stdin and streaming stdout via dedicated `exec_command` and `write_stdin` tools | Automatic tool | `0.24.0` | Aug 2025 |

## Context & Memory

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Conversation History Search | Searches all local sessions with case-insensitive content matching and result previews | Session resume picker | `0.134.0` | May 2026 |
| Cross-Session Memory | Stores persistent thread summaries as memory across sessions with TUI commands to view, update, and delete entries | `/m_update`, `/m_drop` | `0.97.0` | Feb 2026 |
| Project-Aware Config Layering | Loads repo-local `.codex/config.toml` and merges it with user and system configs for per-project settings | `.codex/config.toml` | `0.78.0` | Jan 2026 |
| Automatic Context Compaction | Compacts the conversation context automatically when nearing token limits to keep long sessions alive | Automatic (configurable threshold) | `0.36.0` | Sep 2025 |
| `/compact` Command | Manually compacts the current conversation context to free up token budget mid-session | `/compact` | `0.11.0` | Aug 2025 |

## Model Capabilities

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Voice Input Transcription | Dictates prompts via microphone by holding spacebar; speech is transcribed and sent directly to the model | Hold spacebar in TUI | `0.105.0` | Feb 2026 |
| JavaScript REPL | Provides a persistent JavaScript runtime with state surviving across turns and support for local module imports | `js_repl` in `config.toml` | `0.100.0` | Feb 2026 |
| Steer Mode (Mid-Turn Interrupt) | Interrupts a running model turn with `Ctrl+C` to redirect or refine the current task before the model completes it | `Ctrl+C` during turn | `0.98.0` | Feb 2026 |
| `/review` Command | Performs built-in code review against a specific commit, branch diff, or custom instructions without leaving the session | `/review` | `0.39.0` | Sep 2025 |
| Reasoning Effort Control | Adjusts the model's reasoning effort level at runtime using a picker to trade off speed vs. depth mid-session | `/model` slash command | `0.23.0` | Aug 2025 |
| Local Image Viewing (`view_image`) | Lets Codex agentically inspect local image files and incorporate their visual content into reasoning and responses | Automatic tool | `0.26.0` | Aug 2025 |
| Image Input (Paste & Drag-Drop) | Attaches images to prompts by pasting from the clipboard or dragging image files onto the terminal | Paste / drag-drop | `0.24.0` | Aug 2025 |
| Web Search | Queries the web in real time during a session to access up-to-date information beyond the model's training data | `--search` flag | `0.24.0` | Aug 2025 |
| Open-Weight Model Support | Enables use of open-weight OSS models from OpenAI (e.g., gpt-oss) as the active model in the CLI | `--oss` flag | `0.13.0` | Aug 2025 |

## Extensibility & Control

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Permission Profiles | Defines named permission configurations that persist across TUI sessions, MCP operations, and shell escalation flows | `--profile <name>` | `0.124.0` | Apr 2026 |
| MCP Apps (Resources & File Uploads) | Extends MCP servers to expose resources, accept file uploads, and return rich tool-call metadata to Codex | MCP server config | `0.119.0` | Apr 2026 |
| Plugin System | Installs and manages plugins for skills, MCP servers, and app connectors from marketplace or local sources with authentication and version controls | `/plugins` | `0.110.0` | Mar 2026 |
| Lifecycle Hooks Engine | Executes custom shell commands on `SessionStart`, `Stop`, and `userpromptsubmit` events for pre-execution prompt filtering and automation | `hooks` in `config.toml` | `0.114.0` | Mar 2026 |
| Enterprise MDM Config | Deploys Codex configuration to macOS fleets via MDM TOML payload, merged with repo and global config layers | macOS MDM profile | `0.78.0` | Jan 2026 |
| `requirements.toml` Managed Settings | Constrains permitted sandbox modes, network access, and security policies for managed or enterprise deployments | `/etc/codex/requirements.toml` | `0.76.0` | Dec 2025 |
| ExecPolicy Command Whitelisting | Whitelists command prefixes in the TUI approval flow so subsequent similar commands run without re-prompting | TUI approval UI | `0.66.0` | Dec 2025 |
| Skills Support | Injects reusable skill files from `~/.codex/prompts` or `.agents/skills` into sessions to guide agent behavior with named invocations | `$skill-name` / `/skills` | `0.65.0` | Dec 2025 |
| MCP Streamable HTTP & OAuth | Connects to MCP servers over streamable HTTP with optional OAuth login, bearer tokens, and per-server environment targeting | `codex mcp add <url>` | `0.46.0` | Oct 2025 |
| `!<cmd>` Direct Shell Execution | Executes shell commands directly from the TUI prompt, bypassing the model's planning step | `!<command>` in TUI | `0.52.0` | Oct 2025 |
| `--add-dir` Writable Roots | Specifies additional working directories writable by Codex subprocesses beyond the default project root | `--add-dir <path>` | `0.48.0` | Oct 2025 |
| `/approvals` Runtime Control | Adjusts which command categories require explicit approval during a session without restarting | `/approvals` | `0.23.0` | Aug 2025 |
| AGENTS.md Project Config | Reads `AGENTS.md` files from the project directory up to the git root for per-project agent instructions | `AGENTS.md` file | `0.24.0` | Aug 2025 |
| Custom Prompt Files | Loads reusable named prompts with positional and named arguments from `~/.codex/prompts` for repeatable workflows | `$prompt-name` / `/prompts` | `0.26.0` | Aug 2025 |
| `--ask-for-approval on-request` | Adds a balanced approval mode where the model itself decides whether a given command needs user confirmation | `--ask-for-approval on-request` | `0.16.0` | Aug 2025 |
| MCP Client | Connects to external MCP servers to extend Codex with tools, resources, and capabilities from third-party services | `codex mcp` / `config.toml` | `0.9.0` | Jul 2025 |
| Sandbox Configuration | Controls filesystem and network access sandboxing for all subprocess execution within a session | `--sandbox <mode>` | `0.3.0` | Jul 2025 |

## Platforms & Environments

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| `codex doctor` | Runs comprehensive diagnostics covering runtime, auth, terminal, Git, network, and configuration for support troubleshooting | `codex doctor` | `0.131.0` | May 2026 |
| Python SDK (`openai-codex`) | Official Python package with first-class authentication (API key, ChatGPT, device-code), concurrent turn routing, and sandbox presets | `pip install openai-codex` | `0.131.0` | May 2026 |
| `codex remote-control` | Exposes a running Codex session to external interfaces and devices, adding a remote interaction surface via the local app-server | `codex remote-control` | `0.130.0` | May 2026 |
| Amazon Bedrock Integration | Connects to Amazon Bedrock as a built-in model provider with AWS SigV4 authentication and AWS credential profile support | `provider = "amazon-bedrock"` in config | `0.123.0` | Apr 2026 |
| Realtime Voice Sessions | Enables full WebRTC audio sessions with the model including voice selection and transcript output | Realtime config | `0.119.0` | Apr 2026 |
| App-Server Filesystem RPCs | Exposes file read, write, copy, directory operations, and path watching via the v2 app-server API for IDE-style integrations | App-server v2 API | `0.115.0` | Mar 2026 |
| App-Server WebSocket Transport | Provides bidirectional WebSocket connectivity for the app-server protocol enabling persistent IDE and tooling integrations | App-server WebSocket endpoint | `0.100.0` | Feb 2026 |
| Linux Sandbox | Isolates subprocess filesystem access on Linux using bubblewrap/Landlock with configurable read-only mount paths | Automatic on Linux | `0.81.0` | Jan 2026 |
| Ctrl+G External Editor | Opens the current TUI prompt in `$VISUAL`/`$EDITOR`, allows free-form editing, and syncs changes back on save | `Ctrl+G` | `0.78.0` | Jan 2026 |
| macOS DMG Distribution | Packages Codex as a macOS `.dmg` app bundle for direct installation outside of npm or Homebrew | GitHub Releases (macOS DMG) | `0.76.0` | Dec 2025 |
| Windows Sandbox | Restricts filesystem and network access for agent mode on native Windows, matching parity with macOS sandboxing | Automatic on Windows | `0.59.0` | Nov 2025 |
| `codex exec-server` | Exposes a headless HTTP/WebSocket execution API for running Codex tasks from external tooling and CI pipelines | `codex exec-server` | `0.59.0` | Nov 2025 |
| `codex cloud exec` | Runs tasks in cloud-hosted environments with remote branch support and diff/apply workflows | `codex cloud exec` | `0.44.0` | Oct 2025 |
| TypeScript SDK (`@openai/codex-sdk`) | Provides a programmatic TypeScript API for embedding Codex in applications with image support, working directory, and AbortSignal | `npm install @openai/codex-sdk` | `0.42.0` | Sep 2025 |
| `codex exec --output-schema` | Enforces a JSON Schema on `codex exec` output for structured pipeline automation and machine-readable results | `codex exec --output-schema <file>` | `0.41.0` | Sep 2025 |
| Android / Termux Support | Runs Codex CLI natively on Android devices via the Termux terminal environment | `npm install @openai/codex` on Termux | `0.29.0` | Sep 2025 |

## Other Improvements

Notable changes that fell below the threshold for the main tables:

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
