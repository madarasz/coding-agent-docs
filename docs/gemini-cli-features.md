# Gemini CLI Features (Jun 2025 – Jun 2026)

Significant user-facing features added to Gemini CLI since its public availability.
**Last updated:** Jun 2026 · Source: [geminicli.com/docs/changelogs](https://www.geminicli.com/docs/changelogs)

## Agentic & Multi-Agent

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Git Worktree Support](https://www.geminicli.com/docs/cli/git-worktrees/) | Gives each Gemini session its own isolated copy of the codebase, enabling safe parallel work across branches. | `--worktree` flag | `0.36.0` | Apr 2026 |
| Chapters Narrative Flow | Groups agent tool-use interactions into intent-based chapters for structured session narrative and easier review. | Automatic | `0.38.0` | Apr 2026 |
| HTTP Authentication for A2A Remote Agents | Enables Gemini CLI to authenticate with and delegate tasks to remote agents over HTTP using the Agent-to-Agent protocol. | A2A config | `0.33.0` | Mar 2026 |
| Codebase Investigator Subagent | Built-in subagent that autonomously explores the workspace to resolve relevant information and context for the main agent. | Automatic | `0.12.0` | Nov 2025 |
| [Jules Extension — Remote Worker Delegation](https://www.geminicli.com/docs/extensions/) | Allows Gemini CLI to orchestrate Jules to spawn remote workers and delegate long-running or tedious tasks. | `/extensions install jules` | `0.11.0` | Oct 2025 |

## Context & Memory

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Session Export and Import | Exports the current session to a file and restores it in a future session via a CLI flag. | `--import-session <file>` | `0.43.0` | May 2026 |
| Four-Tier Memory Management | Introduces a structured memory architecture (project, user, workspace, and auto) managed via a prompt-driven flow. | `/memory` | `0.40.0` | Apr 2026 |
| [Context Compression Service](https://www.geminicli.com/docs/cli/auto-memory/) | Distills conversation history intelligently to free up context window space without losing key information. | Automatic | `0.38.0` | Apr 2026 |
| [/rewind Command](https://www.geminicli.com/docs/cli/checkpointing/) | Lets users navigate back through session history to an earlier point and continue from there. | `/rewind` | `0.27.0` | Feb 2026 |
| [Auto Memory](https://www.geminicli.com/docs/cli/auto-memory/) | Mines past sessions in the background, proposes durable memory updates and reusable Agent Skills, all requiring user approval before applying. | Settings toggle | `0.26.0` | Jan 2026 |
| Automatic Conversation Saving | Records every conversation to disk automatically so sessions can be reviewed or resumed later. | Automatic | `0.2.0` | Aug 2025 |
| @{path} Custom File Embedding | Embeds file or directory content directly into prompts using the `@{path}` shorthand syntax. | `@{path}` in prompt | `0.4.0` | Sep 2025 |

## Model & Input

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Real-time Voice Mode](https://www.geminicli.com/docs/get-started/gemini-3/) | Enables live two-way voice conversation with Gemini using cloud or local backends. | Settings toggle | `0.41.0` | May 2026 |
| [Experimental Browser Agent](https://www.geminicli.com/docs/tools/mcp-server/) | Allows Gemini CLI to control a browser with persistent sessions and dynamic tool discovery for web interaction tasks. | Automatic / extension | `0.31.0` | Feb 2026 |
| Multi-file Drag & Drop | Lets users drag and drop multiple files into the terminal, automatically expanding each as an `@path` reference. | Drag & drop in terminal | `0.20.0` | Dec 2025 |
| MCP Resource Support via @ | Enables discovery, viewing, and searching through MCP server resources using the `@` command prefix. | `@resource` | `0.21.0` | Dec 2025 |
| [Model Selection via /model](https://www.geminicli.com/docs/cli/cli-reference/) | Lets users explicitly choose the Gemini model for the current session with a slash command. | `/model` | `0.12.0` | Nov 2025 |
| Intelligent Model Routing | Automatically selects the best model for each task based on its complexity and resource requirements. | Automatic | `0.12.0` | Nov 2025 |

## Built-in Workflows

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Bundled Ripgrep for Offline Search | Ships ripgrep with the CLI so full-text codebase search works without a network connection. | `grep` tool / Automatic | `0.40.0` | Apr 2026 |
| [Plan Mode (GA Apr 2026)](https://www.geminicli.com/docs/cli/plan-mode/) | Provides a read-only planning environment where Gemini researches and designs solutions before touching any files, enabled by default. | `--approval-mode=plan` / `/plan` / `Shift+Tab` | `0.29.0` | Feb 2026 |
| Todo-list Task Planning | Breaks complex user requests into a managed todo checklist the model tracks and updates through execution. | Automatic | `0.15.0` | Nov 2025 |
| Interactive Shell Execution | Runs fully interactive commands (vim, rebase -i, nested gemini) directly inside the Gemini CLI terminal session. | `!` prefix / Automatic | `0.9.0` | Oct 2025 |
| [/security:analyze Built-in Workflow](https://www.geminicli.com/docs/reference/commands/) | Scans the workspace for security vulnerabilities via a built-in slash command. | `/security:analyze` | `0.4.0` | Sep 2025 |
| [/deploy Cloud Run Integration](https://www.geminicli.com/docs/reference/commands/) | Automates app deployment to Google Cloud Run directly from the CLI with a single slash command. | `/deploy` | `0.4.0` | Sep 2025 |
| [/chat share — Session Export](https://www.geminicli.com/docs/cli/tutorials/session-management/) | Converts the current conversation to a shareable Markdown or JSON file for documentation or handoff. | `/chat share <file.md>` | `0.6.0` | Sep 2025 |

## Extensibility

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [SDK Package and Custom Skills](https://www.geminicli.com/docs/cli/skills/) | Provides the initial SDK with dynamic system instructions, SessionContext for tool calls, and support for custom Agent Skills. | npm package / settings | `0.30.0` | Feb 2026 |
| [Agent Skills](https://www.geminicli.com/docs/cli/skills/) (GA Jan 2026) | Lets users and extensions package specialized expertise, procedural workflows, and resources into activatable skills the model can discover and invoke. | `/skills install`, extension | `0.24.0` | Jan 2026 |
| [MCP Server Support](https://www.geminicli.com/docs/tools/mcp-server/) | Integrates any Model Context Protocol server so Gemini CLI can use its tools and resources. | `mcpServers` in settings | `0.5.0` | Sep 2025 |
| [FastMCP Integration](https://www.geminicli.com/docs/tools/mcp-server/) | Lets users install and manage MCP servers through FastMCP with a single command. | `gemini mcp install` | `0.5.0` | Sep 2025 |
| [Extensions System](https://www.geminicli.com/docs/extensions/) | Packages prompts, MCP servers, custom commands, themes, hooks, subagents, and skills into shareable installable extensions. | `gemini extensions install` | `0.8.0` | Oct 2025 |
| [Hooks](https://www.geminicli.com/docs/hooks/) | Executes user-defined scripts at specific lifecycle events (SessionStart, BeforeTool, etc.) to customize and extend CLI behavior. | `hooks` in settings.json | `0.20.0` | Dec 2025 |
| [IDE Plugin Spec / ACP Protocol](https://www.geminicli.com/docs/ide-integration/) | Publishes the open Agent Client Protocol spec so any IDE can build a rich Gemini CLI integration with context awareness and in-editor diffing. | Published spec | `0.7.0` | Oct 2025 |

## Platforms & Environments

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Unified Auto Mode | Merges all specialized automation sub-modes into a single Auto mode for a consistent approval-mode experience. | `--approval-mode=auto` | `0.44.0` | May 2026 |
| Sublime Text and Emacs Client IDE Support | Adds native IDE integration support for Sublime Text and Emacs Client via the ACP protocol. | ACP config | `0.44.0` | May 2026 |
| [Headless / Non-interactive Mode](https://www.geminicli.com/docs/cli/headless/) | Runs Gemini CLI programmatically from scripts or CI with structured text or JSON output and no interactive UI. | `gemini "prompt"` / `--output-format json` | `0.5.0` | Sep 2025 |
| Streaming JSON Output | Streams real-time JSONL events when running headlessly, enabling pipeline integration with incremental output. | `--output-format stream-json` | `0.11.0` | Oct 2025 |
| [VS Code Companion Extension](https://www.geminicli.com/docs/ide-integration/) | Provides workspace context (recently accessed files, cursor position, text selection) and native diff viewing inside VS Code. | VS Code marketplace | `0.1.20` | Aug 2025 |
| [Zed IDE Integration](https://www.geminicli.com/docs/ide-integration/) | Enables Gemini CLI as an agent inside the Zed editor with full ACP context sharing. | Zed ACP settings | `0.19.0` | Nov 2025 |
| Gemini CLI in Google Colab | Runs Gemini CLI pre-installed in Colab notebooks, usable headlessly in cells or interactively. | `!gemini` in Colab cell | `0.22.0` | Dec 2025 |
| Positron IDE Support | Adds ACP-based Gemini CLI integration for the Positron IDE. | ACP config | `0.28.0` | Feb 2026 |

## Security & Governance

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Dynamic Sandbox Expansion with Linux/Windows Worktree | Extends the sandbox boundary dynamically when new worktrees are created on Linux and Windows. | Automatic | `0.37.0` | Apr 2026 |
| Native macOS Seatbelt and Windows Sandbox | Enforces OS-level native sandboxing (macOS Seatbelt, Windows App Container) around subagent tool execution. | Automatic | `0.36.0` | Apr 2026 |
| [Persistent Policy Approvals](https://www.geminicli.com/docs/reference/policy-engine/) | Saves context-aware "always allow" decisions for tool execution so users are not re-prompted for recurring safe actions. | `/policy` or approval dialog | `0.38.0` | Apr 2026 |
| Linux Bubblewrap / seccomp Sandboxing | Isolates process-spawning tools on Linux using bubblewrap and seccomp system-call filtering. | `SandboxManager` config | `0.35.0` | Mar 2026 |
| gVisor (runsc) and LXC Container Sandboxing | Adds gVisor kernel-intercept and experimental LXC container sandboxing as higher-isolation execution environments. | Settings / `--sandbox` | `0.34.0` | Mar 2026 |
| [Policy Engine with Project-level Policies and MCP Wildcards](https://www.geminicli.com/docs/reference/policy-engine/) | Extends the policy engine to support project-scoped policies, MCP server wildcard matching, and tool annotation conditions. | `--policy` / policies TOML | `0.31.0` | Feb 2026 |
| [SDK Policy / --policy Flag with Seatbelt Profiles](https://www.geminicli.com/docs/reference/policy-engine/) | Introduces the `--policy` user flag, strict seatbelt profiles, and deprecates `--allowed-tools` in favor of declarative policy files. | `--policy <file>` | `0.30.0` | Feb 2026 |
| [Admin MCP Server Allowlisting](https://www.geminicli.com/docs/reference/policy-engine/) | Lets administrators pre-approve specific MCP server configurations at the enterprise settings level. | Admin settings | `0.29.0` | Feb 2026 |
| [Persistent "Always Allow" Policies](https://www.geminicli.com/docs/reference/policy-engine/) | Saves granular "Always Allow" decisions for individual tool executions across sessions. | Approval dialog | `0.20.0` | Dec 2025 |
| [Policy Engine (experimental)](https://www.geminicli.com/docs/reference/policy-engine/) | Introduces fine-grained TOML-based tool call policies with allow/deny/ask_user decisions and priority tiers. | `policies/*.toml` | `0.18.0` | Nov 2025 |
| Workspace Trust / Folder Trust | Enforces that workspace settings and tool execution only apply in explicitly trusted folders, defaulting to untrusted. | `/trust` / settings | `0.3.0` | Sep 2025 |
| [--approval-mode Flag](https://www.geminicli.com/docs/cli/plan-mode/) | Gives users and CI systems a command-line parameter to set the tool-execution approval posture (auto, plan, default). | `--approval-mode` | `0.1.20` | Aug 2025 |
| Administrator-enforced Authentication Method | Lets system administrators mandate a specific authentication method, preventing users from switching to less secure options. | System admin settings | `0.5.0` | Sep 2025 |
| Secure .env Loading and Workspace Trust in Headless Mode | Enforces workspace trust checks before loading `.env` files in headless mode to prevent credential leakage. | Automatic | `0.41.0` | May 2026 |

## Other Improvements

Notable changes that fell below the threshold for the main tables:

- Gemini 3.5 Flash backend for Auto Mode (`0.47.0`) - *model releases (Gemini 3.5 Flash, Gemini 3.1 Pro, Gemini 3 Flash, Gemini 3, Gemma 4) — tracked separately*
- A2A Usage Metadata exposure (`0.45.0`) - *incremental improvement*
- agent-tui / tui-tester skills (`0.44.0`) - *power-user UX*
- Edit tool steering for surgical edits (`0.43.0`) - *incremental improvement*
- Adaptive token estimation (`0.43.0`) - *incremental improvement*
- Auto Memory Inbox flow (`0.42.0`) - *incremental improvement*
- Voice Mode wave animations and compliance warnings (`0.42.0`) - *UI polish*
- Advanced shell command validation and core tools allowlist (`0.41.0`) - *config knob*
- MCP resource tools (`0.40.0`) - *incremental improvement*
- Gemma local model setup via `gemini gemma` (`0.40.0`) - *convenience wrapper*
- /memory inbox command for skill review (`0.39.0`) - *incremental improvement*
- Plan Mode skill activation confirmation (`0.39.0`) - *config knob*
- Browser Agent persistent sessions and dynamic tool discovery (`0.37.0`) - *incremental improvement*
- Subagent JIT context injection (`0.36.0`) - *incremental improvement*
- Composer UX refresh (`0.36.0`) - *UI polish*
- Customizable keyboard shortcuts (`0.35.0`) - *power-user UX*
- Vim mode improvements (X, ~, r, f/F/t/T, yank/paste) (`0.35.0`) - *power-user UX*
- JIT Context Discovery for filesystem tools (`0.35.0`) - *incremental improvement*
- Plan Mode enabled by default (`0.34.0`) - *preview→GA, nothing new*
- Plan Mode research subagents, annotation, /plan copy (`0.33.0`) - *incremental improvement*
- Generalist agent enabled (`0.32.0`) - *incremental improvement*
- Model steering in workspace (`0.32.0`) - *config knob*
- Plan Mode external editor support (`0.32.0`) - *incremental improvement*
- Interactive shell autocompletion (`0.32.0`) - *convenience wrapper*
- Parallel extension loading (`0.32.0`) - *incremental improvement*
- Web Fetch experimental direct fetch and rate limiting (`0.31.0`) - *incremental improvement*
- Solarized themes (`0.30.0`) - *UI polish*
- Extension exploration UI (`0.29.0`) - *UI polish*
- Custom themes in extensions and auto theme switching (`0.28.0`) - *UI polish*
- Interactive / non-interactive OAuth consent flow (`0.28.0`) - *incremental improvement*
- Queued tool confirmations (`0.27.0`) - *UI polish*
- Linux clipboard image paste (Wayland / X11) (`0.27.0`) - *platform expansion*
- skill-creator skill enabled by default (`0.26.0`) - *incremental improvement*
- /rewind UI (Rewind Viewer component) (`0.26.0`) - *incremental improvement*
- pr-creator skill + /agents refresh (`0.25.0`) - *convenience wrapper*
- HX editor support (`0.25.0`) - *platform expansion*
- /skills install / uninstall commands (`0.24.0`) - *convenience wrapper*
- OSC 52 paste and Windows clipboard fixes (`0.24.0`) - *platform expansion*
- Gemini-wrapped usage visualizer (`0.23.0`) - *UI polish*
- Windows clipboard image paste via Alt+V (`0.23.0`) - *platform expansion*
- Terminal background color auto-detection (`0.23.0`) - *UI polish*
- /logout command (`0.23.0`) - *convenience wrapper*
- Conductor and Endor Labs extensions (`0.22.0`) - *distribution channel*
- Rill and Browserbase extensions (`0.21.0`) - *distribution channel*
- /stats quota information display (`0.21.0`) - *incremental improvement*
- Fuzzy setting search (`0.21.0`) - *UI polish*
- Auto-execute simple slash commands on Enter (`0.21.0`) - *convenience wrapper*
- Eleven Labs extension (`0.19.0`) - *distribution channel*
- Interactive shell Click-to-Focus (`0.19.0`) - *UI polish*
- Google Workspace, Redis, Anomalo extensions (`0.18.0`) - *distribution channel*
- Model display in chat history toggle (`0.18.0`) - *UI polish*
- Multi-extension uninstall (`0.18.0`) - *convenience wrapper*
- Data Commons extension (`0.16.0`) - *distribution channel*
- Extensions restart `/extensions restart` (`0.15.0`) - *convenience wrapper*
- Disable GitHub-hosted extensions (`0.15.0`) - *config knob*
- Sequential approval for multiple tool calls (`0.12.0`) - *UI polish*
- API key storage dialog (`0.12.0`) - *convenience wrapper*
- Markdown toggle (alt+m / ctrl+m) (`0.11.0`) - *UI polish*
- Non-interactive MCP slash commands (`0.11.0`) - *convenience wrapper*
- /memory list command (`0.9.0`) - *convenience wrapper*
- Install pre-release extensions (`--pre-release`) (`0.9.0`) - *format/scripting flag*
- Non-interactive `--allowed-tools` (`0.8.0`) - *format/scripting flag*
- Terminal title status (`showStatusInTitle`) (`0.8.0`) - *config knob*
- /chat share tool call rendering (`0.7.0`) - *incremental improvement*
- Custom slash commands in headless mode (`0.7.0`) - *format/scripting flag*
- Databases / BigQuery extension suite (`0.6.0`) - *distribution channel*
- Prompt search (ctrl+r) (`0.6.0`) - *UI polish*
- Input undo/redo (ctrl+z / ctrl+shift+z) (`0.6.0`) - *UI polish*
- JSON session summary (`--session-summary`) (`0.4.0`) - *format/scripting flag*
- MCP loading indicator (`0.4.0`) - *UI polish*
- Hugging Face, Monday.com, Data Commons extensions (`0.12.0`) - *distribution channel*
