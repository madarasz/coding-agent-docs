# Claude Code Features (Mar 2025 – May 2026)

Significant user-facing features added to Claude Code since its public availability.
**Last updated:** Jun 2026 · Source: [CHANGELOG.md](https://raw.githubusercontent.com/anthropics/claude-code/refs/heads/main/CHANGELOG.md)

## Agentic & Multi-Agent

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Dynamic Workflows](https://code.claude.com/docs/en/agent-view) | Orchestrate tens-to-hundreds of parallel background agents automatically for large, complex tasks. | Ask Claude "create a workflow"; `/workflows` | `2.1.154` | May 2026 |
| [Agent View](https://code.claude.com/docs/en/agent-view) | Unified dashboard listing every Claude Code session (running, blocked, done) with dispatch, peek, and attach from one screen. | `claude agents` | `2.1.139` | May 2026 |
| `/goal` Command | Set a completion condition and Claude keeps working autonomously across turns until it is met. | `/goal <condition>` | `2.1.139` | May 2026 |
| Pinned Background Sessions | Pin a background session so it stays alive when idle and restarts automatically on CLI updates. | `Ctrl+T` in `claude agents` | `2.1.147` | May 2026 |
| Background Session Resume | Background sessions started with `--bg` appear in the `/resume` picker alongside interactive sessions. | `/resume` | `2.1.144` | May 2026 |
| Monitor Tool | Stream events from long-running background scripts; each stdout line becomes a notification to the main agent. | `Monitor` tool | `2.1.98` | Apr 2026 |
| Agent Teams | Multiple Claude Code sessions collaborate as a team, sending messages to each other via tmux panes (experimental). | `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1` | `2.1.32` | Feb 2026 |
| [Git Worktree Isolation](https://code.claude.com/docs/en/worktrees) | Start a session in an isolated git worktree so parallel sessions can modify files without conflicts. | `claude --worktree` / `-w` | `2.1.49` | Feb 2026 |
| Task Management with Dependencies | Task management system with dependency tracking across multi-step work via `TaskCreate`, `TaskUpdate`, `TaskList`, and `TaskGet` tools. | `TaskCreate` / `TaskUpdate` tools | `2.1.16` | Jan 2026 |
| Async Agents with Messaging | Background agents and bash commands run asynchronously and wake the main agent when done. | `Task` tool; `Ctrl+B` | `2.0.64` | Dec 2025 |
| [Background Agents](https://code.claude.com/docs/en/agent-view) | Sessions run in the background without a terminal attached, continuing after the terminal is closed. | `claude --bg`; `/bg` | `2.0.60` | Dec 2025 |
| Background Bash Commands | Run any bash command in the background so Claude can keep working while the command executes. | `Ctrl+B` while a command runs | `1.0.71` | Aug 2025 |
| Task/Todo List | Claude creates and tracks a visible structured task list for multi-step work within a session. | Automatic | `0.2.93` | May 2025 |

## Context & Memory

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Session Recap](https://code.claude.com/docs/en/session-recap) | Provides a context summary when returning to a session after being away; also manually invocable. | `/recap`; automatic on return | `2.1.122` | Apr 2026 |
| `/resume` from PR URL | Paste a pull request URL into the `/resume` search box to find the session that created that PR. | `/resume <PR-URL>` | `2.1.108` | Apr 2026 |
| [Auto-Memory](https://code.claude.com/docs/en/memory) | Claude automatically saves useful context to a persistent memory file and recalls it across sessions. | Automatic; `/memory` to manage | `2.1.32` | Feb 2026 |
| [Named Sessions](https://code.claude.com/docs/en/cli-reference) | Sessions can be named and resumed by name from the CLI or picker. | `/rename <name>`; `claude --resume <name>` | `2.0.64` | Dec 2025 |
| [`.claude/rules/` Directory](https://code.claude.com/docs/en/memory) | Per-project contextual rules loaded from Markdown files, with optional `paths:` frontmatter for file-scoped rules. | `.claude/rules/*.md` | `2.0.64` | Dec 2025 |
| [CLAUDE.md File Imports](https://code.claude.com/docs/en/memory) | CLAUDE.md files can import additional context files with `@path/to/file.md` directives. | `@path/to/file.md` in CLAUDE.md | `0.2.107` | May 2025 |
| [Session Resume](https://code.claude.com/docs/en/cli-reference) | Resume previous conversations from where they left off across restarts. | `claude --continue` / `--resume` | `0.2.93` | Apr 2025 |
| [Auto-Compaction](https://code.claude.com/docs/en/memory) | Automatic context summarization enables infinite conversation length when the context window fills. | Automatic; toggle via `/config` | `0.2.47` | Mar 2025 |

## Model Capabilities

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| `/code-review` | Structured code review with optional automatic fix application. | `/code-review` or `/code-review --fix` | `2.1.147` | May 2026 |
| [/ultrareview](https://code.claude.com/docs/en/commands) | Runs comprehensive code review in the cloud using parallel multi-agent analysis. | `/ultrareview`; `claude ultrareview` | `2.1.111` | Apr 2026 |
| `/effort` Command | Interactive slider to set the model's effort level (speed vs. intelligence). | `/effort`; `--effort` flag | `2.1.76` | Mar 2026 |
| [Fast Mode (Opus 4.6)](https://code.claude.com/docs/en/fast-mode) | Opt-in fast mode for Claude Opus 4.6 at 2× cost for approximately 2.5× speed using the 1M context window. | `/fast`; toggle in `/model` | `2.1.36` | Feb 2026 |
| Model Customization for Subagents | Custom agents can specify which model they use via the `model:` field in their frontmatter. | `model:` in `.claude/agents/*.md` | `1.0.64` | Jul 2025 |
| PDF Reading | Claude reads PDF files up to 100 pages or 20 MB with page-range selection. | `@file.pdf` or `Read` tool with `pages` param | `1.0.58` | Jul 2025 |
| Real-Time Steering | Send messages to Claude while it is working to redirect or correct it mid-task. | Type in the prompt while Claude responds | `0.2.108` | May 2025 |
| Web Search | Claude searches the web to answer questions requiring current or real-time information. | Automatic when needed | `0.2.105` | May 2025 |
| Multimodal Input (Images) | Paste or drag-and-drop images directly into the prompt for Claude to analyze. | `Ctrl+V`; drag-and-drop; `@image.png` | `0.2.59` | Apr 2025 |
| Web Fetch | Claude fetches and reads the content of URLs pasted into the prompt. | Paste URL; `WebFetch` tool | `0.2.53` | Mar 2025 |
| [Thinking Mode](https://www.anthropic.com/news/claude-3-7-sonnet) | Extended thinking with configurable depth triggered by "think", "think harder", or "ultrathink" in the prompt. | `think` / `ultrathink` in prompt; Alt+T | `0.2.44` | Mar 2025 |

## Extensibility & Control

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Plugin Auto-Load](https://code.claude.com/docs/en/plugins) | Plugins placed in `.claude/skills/` directories load automatically without marketplace registration. | `.claude/skills/`; `claude plugin init` | `2.1.157` | May 2026 |
| [MessageDisplay Hook](https://code.claude.com/docs/en/hooks) | Hooks can transform or hide assistant message text as it is displayed to the user. | `MessageDisplay` in settings | `2.1.152` | May 2026 |
| Skills `disallowed-tools` Frontmatter | Skills can restrict which tools are available while the skill is active. | `disallowed-tools:` in SKILL.md frontmatter | `2.1.152` | May 2026 |
| Hook `continueOnBlock` | PostToolUse hooks can feed their rejection reason back to Claude and let the turn continue instead of stopping. | `continueOnBlock: true` in PostToolUse hook | `2.1.139` | May 2026 |
| [PostToolUse Output Replacement](https://code.claude.com/docs/en/hooks) | PostToolUse hooks can replace tool output for any tool before Claude sees it. | `hookSpecificOutput.updatedToolOutput` | `2.1.121` | Apr 2026 |
| [MCP Tool-Type Hooks](https://code.claude.com/docs/en/hooks) | Hooks can invoke MCP tools directly as their action. | `type: "mcp_tool"` in hooks config | `2.1.118` | Apr 2026 |
| Auto Mode | Permission mode using AI safety classification to approve or deny tool use without per-action prompts. | `--permission-mode auto`; `Shift+Tab` cycle | `2.1.111` | Apr 2026 |
| [Plugin Background Monitors](https://code.claude.com/docs/en/plugins) | Plugins can arm background monitoring scripts that run automatically at session start. | `monitors:` in `plugin.json` | `2.1.105` | Apr 2026 |
| [PreCompact Hook](https://code.claude.com/docs/en/hooks) | Hooks can block conversation compaction by exiting with code 2 or returning a block decision. | `PreCompact` hook event in settings | `2.1.105` | Apr 2026 |
| [Subprocess Sandboxing](https://code.claude.com/docs/en/sandboxing) | Bash tool processes run in isolated PID namespaces on Linux with per-session script invocation limits. | `CLAUDE_CODE_SUBPROCESS_ENV_SCRUB=1`; `sandbox` settings | `2.1.98` | Apr 2026 |
| PermissionDenied Hook | Fires after auto mode classifier denials; return `{retry: true}` to let Claude retry the denied action. | `PermissionDenied` hook event in settings | `2.1.89` | Mar 2026 |
| Hook Conditional `if` Field | Hooks can use permission rule syntax in an `if` field to filter exactly which commands trigger them. | `if: "Bash(git *)"` in hook config | `2.1.85` | Mar 2026 |
| Managed Settings Drop-in Directory | Enterprise policy fragments in `managed-settings.d/` are merged alphabetically at startup. | `managed-settings.d/` directory | `2.1.83` | Mar 2026 |
| [Channels Research Preview](https://code.claude.com/docs/en/channels) | MCP servers can push messages into your active session to trigger external event-driven workflows. | `--channels` flag | `2.1.80` | Mar 2026 |
| MCP Elicitation | MCP servers can request structured input from the user mid-task via an interactive dialog. | Automatic (server-triggered); `Elicitation` hook to intercept | `2.1.76` | Mar 2026 |
| `/loop` Recurring Prompt Scheduling | Run a prompt or slash command on a recurring interval within a session. | `/loop 5m <prompt>`; `CronCreate` tool | `2.1.71` | Mar 2026 |
| [HTTP Hooks](https://code.claude.com/docs/en/hooks) | Hooks can POST JSON to a URL and receive a JSON response instead of running a shell command. | `type: "http"` in hooks config | `2.1.63` | Mar 2026 |
| `isolation: worktree` in Agent Definitions | Agent definitions can run in isolated git worktrees declaratively, without the `--worktree` CLI flag. | `isolation: worktree` in agent frontmatter | `2.1.50` | Feb 2026 |
| WorktreeCreate / WorktreeRemove Hooks | Hook events for custom VCS setup and teardown when agent worktree isolation creates or removes worktrees. | `WorktreeCreate` / `WorktreeRemove` hook events | `2.1.50` | Feb 2026 |
| ConfigChange Hook | Fires when configuration files change during a session, enabling security auditing and blocking. | `ConfigChange` hook event in settings | `2.1.49` | Feb 2026 |
| [Customizable Keyboard Shortcuts](https://code.claude.com/docs/en/keybindings) | Configure keybindings per context, create chord sequences, and rebind any action. | `/keybindings`; `~/.claude/keybindings.json` | `2.1.18` | Jan 2026 |
| MCP Tool Search (Auto-Defer) | MCP tools are automatically deferred and discovered on demand when tool descriptions exceed 10% of the context window. | Automatic; configure with `auto:N` in settings | `2.1.7` | Jan 2026 |
| `context: fork` in Skills | Skills can run in a forked sub-agent context so they don't affect the main conversation's tool set or context. | `context: fork` in SKILL.md frontmatter | `2.1.0` | Jan 2026 |
| MCP `list_changed` Notifications | MCP servers can dynamically update available tools, prompts, and resources without requiring reconnection. | Automatic | `2.1.0` | Jan 2026 |
| MCP Wildcard Permissions | Allow or deny all tools from an MCP server at once using wildcard patterns. | `mcp__server__*` in permissions | `2.0.70` | Dec 2025 |
| Enterprise Managed Settings | Admins deploy policy settings via `managed-settings.json`, macOS plist, or Windows Registry. | `managed-settings.json` | `2.0.68` | Dec 2025 |
| [PermissionRequest Hook](https://code.claude.com/docs/en/hooks) | Auto-approve or deny tool permissions programmatically with custom logic. | `hooks.PermissionRequest` in settings | `2.0.45` | Nov 2025 |
| [Plugin System with Marketplaces](https://code.claude.com/docs/en/plugins) | Install, manage, and share plugins from Git-based marketplaces or local directories. | `/plugin install`; `--plugin-dir` | `2.0.41` | Nov 2025 |
| Output Styles (Plugin System) | Plugins can ship custom response formatting styles applied globally. | Via plugin install | `2.0.41` | Nov 2025 |
| Dynamic MCP Headers | Per-request custom headers for MCP servers supplied via a script. | `headersHelper` in MCP server config | `1.0.119` | Sep 2025 |
| Custom Agents | Define specialized agents with custom system prompts, tool restrictions, and models in `.claude/agents/`. | `.claude/agents/*.md`; `@<agent-name>` | `1.0.60` | Jul 2025 |
| OpenTelemetry Integration | Emit tool decisions, session metrics, LLM request spans, and active time to any OTLP endpoint. | `OTEL_EXPORTER_OTLP_ENDPOINT` env var | `1.0.39` | Jul 2025 |
| [Hooks System](https://code.claude.com/docs/en/hooks) | Full lifecycle hook system: PreToolUse, PostToolUse, SessionStart, SessionEnd, Stop, SubagentStop, and more. | `hooks` key in `.claude/settings.json` | `1.0.38` | Jun 2025 |
| MCP OAuth | Remote MCP servers support full OAuth authentication flows including step-up authorization. | Automatic on connection; `claude mcp add --client-id` | `1.0.27` | Jun 2025 |
| SlashCommand Tool | Claude can invoke custom slash commands programmatically during a session. | Automatic (Claude uses it) | `1.0.23` | Jun 2025 |
| Dynamic API Key Refresh | Dynamically generated API keys via `apiKeyHelper` are automatically refreshed with a configurable TTL. | `apiKeyHelper` in settings | `0.2.74` | Apr 2025 |
| Project Settings | Shared project-wide permission rules and settings committed with the repository. | `.claude/settings.json` | `0.2.67` | Apr 2025 |
| [MCP Project Scope](https://www.anthropic.com/news/model-context-protocol) | MCP server configurations can be committed to the repository in `.mcp.json` and shared with teammates. | `claude mcp add --scope project` | `0.2.50` | Mar 2025 |
| [MCP Support](https://code.claude.com/docs/en/mcp) | Connect external tools, data sources, and APIs via the Model Context Protocol. | `claude mcp add`; `--mcp-config` | `0.2.32` | Mar 2025 |
| [Custom Slash Commands](https://code.claude.com/docs/en/skills) | Markdown files in `.claude/commands/` directories appear as custom slash commands. | `.claude/commands/*.md`; `/<name>` | `0.2.31` | Mar 2025 |

## Platforms & Environments

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Auto Mode on Bedrock/Vertex/Foundry | Auto mode is available on Amazon Bedrock, Vertex AI, and Azure Foundry for Opus 4.7/4.8. | `CLAUDE_CODE_ENABLE_AUTO_MODE=1` | `2.1.158` | May 2026 |
| Native Binary | Claude Code ships as a native compiled binary instead of Node.js, improving performance and startup time. | Automatic in new installs | `2.1.113` | Apr 2026 |
| Push Notifications (Mobile) | Claude sends push notifications to your phone when tasks complete or need attention, via Remote Control. | Enable in `/config` | `2.1.110` | Apr 2026 |
| Amazon Bedrock Mantle | Use Claude Code against Claude models hosted via Amazon Bedrock powered by Mantle. | `CLAUDE_CODE_USE_MANTLE=1` | `2.1.94` | Apr 2026 |
| PowerShell Tool (Windows) | Claude executes PowerShell commands on Windows as a first-class tool alongside Bash. | Automatic on Windows; `CLAUDE_CODE_USE_POWERSHELL_TOOL=1` | `2.1.84` | Mar 2026 |
| [Remote Control](https://code.claude.com/docs/en/remote-control) | Bridge a local CLI session to claude.ai/code to continue from a browser or mobile device. | `claude remote-control`; `/remote-control` | `2.1.51` | Feb 2026 |
| [claude.ai MCP Connectors](https://code.claude.com/docs/en/mcp) | Use cloud service connectors (Slack, Gmail, etc.) from claude.ai directly in Claude Code sessions. | Automatic when logged into claude.ai | `2.1.46` | Feb 2026 |
| LSP Tool | Code intelligence features including go-to-definition, find references, and hover documentation. | LSP server configured in settings | `2.0.74` | Dec 2025 |
| [Claude in Chrome](https://code.claude.com/docs/en/chrome) | Control a connected Chrome browser directly from Claude Code via the Claude Chrome extension. | Chrome extension at claude.ai/chrome; `/chrome` | `2.0.72` | Dec 2025 |
| [Desktop App](https://claude.com/download) | Native desktop application for macOS and Windows with integrated session management. | [claude.com/download](https://claude.com/download) | `2.0.51` | Nov 2025 |
| [Microsoft Azure AI Foundry](https://code.claude.com/docs/en/azure-ai-foundry) | Use Claude Code with Claude models hosted on Microsoft Azure AI Foundry. | Azure env vars; setup wizard | `2.0.45` | Nov 2025 |
| [VS Code Extension](https://code.claude.com/docs/en/) | Full VS Code extension with session tabs, plan previews, IDE diff integration, and sidebar. | VS Code marketplace | `2.0.0` | Sep 2025 |
| [Streaming SDK Output](https://code.claude.com/docs/en/agent-sdk/overview) | The Claude Code SDK streams partial messages in real-time via `--include-partial-messages`. | `--include-partial-messages` | `1.0.109` | Sep 2025 |
| Native Windows Support | Claude Code runs natively on Windows without requiring WSL (requires Git for Windows or PowerShell). | `claude install` on Windows | `1.0.51` | Jul 2025 |
| [Claude Agent SDK](https://code.claude.com/docs/en/agent-sdk/overview) | TypeScript and Python SDKs for programmatic access to Claude Code features and sessions. | `@anthropic-ai/claude-code`; `pip install claude-code-sdk` | `1.0.23` | Jun 2025 |
| Streaming Print Mode | `--print` mode with real-time JSON output enables scripting and CI integration. | `claude -p --output-format=stream-json` | `0.2.66` | Apr 2025 |
| Import MCP Servers from Claude Desktop | Import MCP server configurations from Claude Desktop with a single command. | `claude mcp add-from-claude-desktop` | `0.2.36` | Mar 2025 |

## Other Improvements

Notable changes that fell below the threshold for the main tables:

- `claude plugin init` Scaffolding (`2.1.157`) - *convenience tooling for plugin authors, not a new workflow capability*
- `/reload-skills` Command (`2.1.152`) - *DX convenience for skill/plugin development*
- Vim NORMAL Mode History Search with `/` (`2.1.152`) - *incremental improvement to existing vim mode*
- `/usage` Per-Category Breakdown (`2.1.149`) - *improvement to existing /usage command*
- GFM Task List Checkboxes in Markdown Output (`2.1.149`) - *rendering improvement to existing output*
- Plugin Dependency Enforcement in `claude plugin disable` (`2.1.143`) - *improvement to existing plugin management*
- `worktree.bgIsolation: "none"` Setting (`2.1.143`) - *config knob for existing worktree feature*
- `claude agents --json` Scripting Output (`2.1.145`) - *scripting alias exposing existing agent list*
- Status Line JSON: GitHub Repo and PR Info (`2.1.145`) - *improvement to existing status line feature*
- "Summarize Up to Here" in Rewind Menu (`2.1.141`) - *enhancement to existing rewind feature*
- `terminalSequence` Field in Hook JSON Output (`2.1.141`) - *improvement to existing hooks for desktop notifications*
- `/tui` Display Mode Toggle Command (`2.1.110`) - *convenience command for an existing display setting*
- `/team-onboarding` Command (`2.1.101`) - *team-specific DX tool, not a general coding workflow*
- Interactive Vertex AI Setup Wizard (`2.1.98`) - *improvement to existing provider onboarding*
- Interactive Bedrock Setup Wizard (`2.1.92`) - *improvement to existing provider onboarding*
- `/powerup` Interactive Feature Lessons (`2.1.90`) - *onboarding tutorial feature*
- `CwdChanged` and `FileChanged` Hook Events (`2.1.83`) - *improvement to hooks system for reactive env management*
- Transcript Search in Transcript Mode (`2.1.83`) - *UI navigation improvement*
- Agent `initialPrompt` Frontmatter (`2.1.83`) - *improvement to agent authoring, not a new capability class*
- `--bare` Flag for Headless Sessions (`2.1.81`) - *optimization flag for scripted SDK usage*
- `StopFailure` Hook Event (`2.1.78`) - *improvement to existing hooks system*
- `${CLAUDE_PLUGIN_DATA}` Variable for Plugin Persistent State (`2.1.78`) - *improvement to existing plugin system*
- Opus 4.6 1M Context Window by Default for Max/Team/Enterprise (`2.1.75`) - *capacity improvement, model-level change*
- `/color` Command for Session Prompt Bar (`2.1.75`) - *UI customization*
- `ExitWorktree` Tool (`2.1.72`) - *completion of the EnterWorktree/ExitWorktree pair, not a new paradigm*
- CLAUDE.md HTML Comments Hidden from Claude (`2.1.72`) - *behavior change to existing CLAUDE.md feature*
- Skill Hot-Reload (`2.1.0`) - *DX friction reduction, not a new capability*
