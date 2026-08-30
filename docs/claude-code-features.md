# Claude Code Features (Mar 2025 – Aug 2026)

Significant user-facing features added to Claude Code since its public availability.
**Last updated:** Aug 30, 2026 · Source: [CHANGELOG.md](https://raw.githubusercontent.com/anthropics/claude-code/refs/heads/main/CHANGELOG.md)

## Agentic & Multi-Agent

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Cross-Session Messaging | Interactive Claude Code sessions on your machines can message each other directly via SendMessage, using ListAgents or an `@`-mention to find and reach a specific session. | `SendMessage`/`ListAgents` tools; `@<session>` in prompt | `2.1.224` | Aug 2026 |
| [`/fork` Background Session Copy](https://code.claude.com/docs/en/commands) | Copies the current conversation into a new independent background session that runs as its own row in agent view while you keep working; `/subtask` remains for delegating a side task to a subagent that reports back into the conversation. | `/fork [prompt]` | `2.1.212` | Jul 2026 |
| Nested Sub-Agent Spawning | Sub-agents can now spawn their own sub-agents up to 5 levels deep, enabling hierarchical multi-agent workflows. | Automatic (sub-agent uses Agent tool) | `2.1.172` | Jun 2026 |
| Parallel Tool Call Independence | A failed Bash command in a parallel tool call batch no longer cancels the other calls in the same batch; each tool returns its own result independently. | Automatic | `2.1.161` | Jun 2026 |
| [Dynamic Workflows](https://code.claude.com/docs/en/agent-view) | Orchestrate tens-to-hundreds of parallel background agents automatically for large, complex tasks. | Ask Claude "create a workflow"; `/workflows` | `2.1.154` | May 2026 |
| [Agent View](https://code.claude.com/docs/en/agent-view) | Unified dashboard listing every Claude Code session (running, blocked, done) with dispatch, peek, and attach from one screen. | `claude agents` | `2.1.139` | May 2026 |
| `/goal` Command | Set a completion condition and Claude keeps working autonomously across turns until it is met. | `/goal <condition>` | `2.1.139` | May 2026 |
| Pinned Background Sessions | Pin a background session so it stays alive when idle and restarts automatically on CLI updates. | `Ctrl+T` in `claude agents` | `2.1.147` | May 2026 |
| Background Session Resume | Background sessions started with `--bg` appear in the `/resume` picker alongside interactive sessions. | `/resume` | `2.1.144` | May 2026 |
| Monitor Tool | Stream events from long-running background scripts; each stdout line becomes a notification to the main agent. | `Monitor` tool | `2.1.98` | Apr 2026 |
| Agent Teams | Multiple Claude Code sessions collaborate as a team, sending messages to each other via tmux panes (experimental). | `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1` | `2.1.32` | Feb 2026 |
| [Git Worktree Isolation](https://code.claude.com/docs/en/worktrees) | Start a session in an isolated git worktree so parallel sessions can modify files without conflicts. | `claude --worktree` / `-w` | `2.1.49` | Feb 2026 |
| Task Management with Dependencies | Task management system with dependency tracking across multi-step work via `TaskCreate`, `TaskUpdate`, `TaskList`, and `TaskGet` tools. | `TaskCreate` / `TaskUpdate` tools | `2.1.16` | Jan 2026 |
| Async Agents with Messaging (GA Jul 2026) | Background agents and bash commands run asynchronously and wake the main agent when done; subagents now run in the background by default rather than as a gradual rollout. | `Task` tool; `Ctrl+B` | `2.0.64` | Dec 2025 |
| [Background Agents](https://code.claude.com/docs/en/agent-view) | Sessions run in the background without a terminal attached, continuing after the terminal is closed. | `claude --bg`; `/bg` | `2.0.60` | Dec 2025 |
| Background Bash Commands | Run any bash command in the background so Claude can keep working while the command executes. | `Ctrl+B` while a command runs | `1.0.71` | Aug 2025 |
| Task/Todo List | Claude creates and tracks a visible structured task list for multi-step work within a session. | Automatic | `0.2.93` | May 2025 |

## Context & Memory

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| `/cd` Command | Move a session to a new working directory mid-session without breaking the prompt cache; loads the new directory's CLAUDE.md and makes the session resumable from the new path. | `/cd <path>` | `2.1.169` | Jun 2026 |
| [Session Recap](https://code.claude.com/docs/en/session-recap) | Provides a context summary when returning to a session after being away; also manually invocable. | `/recap`; automatic on return | `2.1.122` | Apr 2026 |
| `/resume` from PR URL | Paste a pull request URL into the `/resume` search box to find the session that created that PR. | `/resume <PR-URL>` | `2.1.108` | Apr 2026 |
| [Auto-Memory](https://code.claude.com/docs/en/memory) | Claude automatically saves useful context to a persistent memory file and recalls it across sessions. | Automatic; `/memory` to manage | `2.1.32` | Feb 2026 |
| [Named Sessions](https://code.claude.com/docs/en/cli-reference) | Sessions can be named and resumed by name from the CLI or picker. | `/rename <name>`; `claude --resume <name>` | `2.0.64` | Dec 2025 |
| [`.claude/rules/` Directory](https://code.claude.com/docs/en/memory) | Per-project contextual rules loaded from Markdown files, with optional `paths:` frontmatter for file-scoped rules. | `.claude/rules/*.md` | `2.0.64` | Dec 2025 |
| [CLAUDE.md File Imports](https://code.claude.com/docs/en/memory) | CLAUDE.md files can import additional context files with `@path/to/file.md` directives. | `@path/to/file.md` in CLAUDE.md | `0.2.107` | May 2025 |
| [Session Resume](https://code.claude.com/docs/en/cli-reference) | Resume previous conversations from where they left off across restarts. | `claude --continue` / `--resume` | `0.2.93` | Apr 2025 |
| [Auto-Compaction](https://code.claude.com/docs/en/memory) | Automatic context summarization enables infinite conversation length when the context window fills. | Automatic; toggle via `/config` | `0.2.47` | Mar 2025 |

## Model & Input

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| `/effort` Command | Interactive slider to set the model's effort level (speed vs. intelligence). | `/effort`; `--effort` flag | `2.1.76` | Mar 2026 |
| [Fast Mode (Opus 4.6)](https://code.claude.com/docs/en/fast-mode) | Opt-in fast mode for Claude Opus 4.6 at 2× cost for approximately 2.5× speed using the 1M context window. | `/fast`; toggle in `/model` | `2.1.36` | Feb 2026 |
| PDF Reading | Claude reads PDF files up to 100 pages or 20 MB with page-range selection. | `@file.pdf` or `Read` tool with `pages` param | `1.0.58` | Jul 2025 |
| Real-Time Steering | Send messages to Claude while it is working to redirect or correct it mid-task. | Type in the prompt while Claude responds | `0.2.108` | May 2025 |
| Web Search | Claude searches the web to answer questions requiring current or real-time information. | Automatic when needed | `0.2.105` | May 2025 |
| Multimodal Input (Images) | Paste or drag-and-drop images directly into the prompt for Claude to analyze. | `Ctrl+V`; drag-and-drop; `@image.png` | `0.2.59` | Apr 2025 |
| Web Fetch | Claude fetches and reads the content of URLs pasted into the prompt. | Paste URL; `WebFetch` tool | `0.2.53` | Mar 2025 |
| [Thinking Mode](https://www.anthropic.com/news/claude-3-7-sonnet) | Extended thinking with configurable depth triggered by "think", "think harder", or "ultrathink" in the prompt. | `think` / `ultrathink` in prompt; Alt+T | `0.2.44` | Mar 2025 |

## Built-in Workflows

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [`/doctor` Full Setup Checkup](https://code.claude.com/docs/en/commands) | Diagnoses install, settings, and provider setup issues and can apply fixes directly, not just report them. | `/doctor`; alias `/checkup` | `2.1.205` | Jul 2026 |
| [Auto-Commit, Push, and Draft PR for Background Agents](https://code.claude.com/docs/en/agent-view) | A background session that isolates its changes in a worktree now commits, pushes its branch, and opens a draft pull request when it finishes code work, instead of stopping to ask. | Automatic (background sessions with worktree isolation) | `2.1.198` | Jul 2026 |
| `!` Bash Command Auto-Reply | Running a `!` bash command now automatically prompts Claude to respond to the command's output, turning any shell command into an interactive Claude turn. | `!<command>` in prompt; disable with `"respondToBashCommands": false` | `2.1.186` | Jun 2026 |
| `/code-review` | Structured code review with optional automatic fix application. | `/code-review` or `/code-review --fix` | `2.1.147` | May 2026 |
| [/ultrareview](https://code.claude.com/docs/en/commands) | Runs comprehensive code review in the cloud using parallel multi-agent analysis. | `/ultrareview`; `claude ultrareview` | `2.1.111` | Apr 2026 |

## Extensibility

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| Post-Session Lifecycle Hook | Self-hosted runners expose a `post-session` hook that runs after the session ends and before the workspace is deleted, enabling log export and artifact snapshots. | `post-session` in runner config | `2.1.169` | Jun 2026 |
| Stop/SubagentStop `additionalContext` Output | Stop and SubagentStop hooks can return `hookSpecificOutput.additionalContext` to feed feedback back to Claude and continue the turn without triggering a hook error. | `hookSpecificOutput.additionalContext` in Stop/SubagentStop hook | `2.1.163` | Jun 2026 |
| [Plugin Auto-Load](https://code.claude.com/docs/en/plugins) | Plugins placed in `.claude/skills/` directories load automatically without marketplace registration. | `.claude/skills/`; `claude plugin init` | `2.1.157` | May 2026 |
| [MessageDisplay Hook](https://code.claude.com/docs/en/hooks) | Hooks can transform or hide assistant message text as it is displayed to the user. | `MessageDisplay` in settings | `2.1.152` | May 2026 |
| Skills `disallowed-tools` Frontmatter | Skills can restrict which tools are available while the skill is active. | `disallowed-tools:` in SKILL.md frontmatter | `2.1.152` | May 2026 |
| Hook `continueOnBlock` | PostToolUse hooks can feed their rejection reason back to Claude and let the turn continue instead of stopping. | `continueOnBlock: true` in PostToolUse hook | `2.1.139` | May 2026 |
| [PostToolUse Output Replacement](https://code.claude.com/docs/en/hooks) | PostToolUse hooks can replace tool output for any tool before Claude sees it. | `hookSpecificOutput.updatedToolOutput` | `2.1.121` | Apr 2026 |
| [MCP Tool-Type Hooks](https://code.claude.com/docs/en/hooks) | Hooks can invoke MCP tools directly as their action. | `type: "mcp_tool"` in hooks config | `2.1.118` | Apr 2026 |
| [Plugin Background Monitors](https://code.claude.com/docs/en/plugins) | Plugins can arm background monitoring scripts that run automatically at session start. | `monitors:` in `plugin.json` | `2.1.105` | Apr 2026 |
| [PreCompact Hook](https://code.claude.com/docs/en/hooks) | Hooks can block conversation compaction by exiting with code 2 or returning a block decision. | `PreCompact` hook event in settings | `2.1.105` | Apr 2026 |
| PermissionDenied Hook | Fires after auto mode classifier denials; return `{retry: true}` to let Claude retry the denied action. | `PermissionDenied` hook event in settings | `2.1.89` | Mar 2026 |
| Hook Conditional `if` Field | Hooks can use permission rule syntax in an `if` field to filter exactly which commands trigger them. | `if: "Bash(git *)"` in hook config | `2.1.85` | Mar 2026 |
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
| [PermissionRequest Hook](https://code.claude.com/docs/en/hooks) | Auto-approve or deny tool permissions programmatically with custom logic. | `hooks.PermissionRequest` in settings | `2.0.45` | Nov 2025 |
| [Plugin System with Marketplaces](https://code.claude.com/docs/en/plugins) | Install, manage, and share plugins from Git-based marketplaces or local directories. | `/plugin install`; `--plugin-dir` | `2.0.41` | Nov 2025 |
| Output Styles (Plugin System) | Plugins can ship custom response formatting styles applied globally. | Via plugin install | `2.0.41` | Nov 2025 |
| Dynamic MCP Headers | Per-request custom headers for MCP servers supplied via a script. | `headersHelper` in MCP server config | `1.0.119` | Sep 2025 |
| Model Customization for Subagents | Custom agents can specify which model they use via the `model:` field in their frontmatter. | `model:` in `.claude/agents/*.md` | `1.0.64` | Jul 2025 |
| Custom Agents | Define specialized agents with custom system prompts, tool restrictions, and models in `.claude/agents/`. | `.claude/agents/*.md`; `@<agent-name>` | `1.0.60` | Jul 2025 |
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
| GitLab Support | Claude Code adds GitLab as a supported git host: merge request URLs work with `--worktree` and the agents view, plugin marketplaces can install from gitlab.com repositories, and GitLab tokens get the same secret redaction as GitHub's. | GitLab remote in git config; `--worktree <MR-URL>` | `2.1.232` | Aug 2026 |
| Self-Hosted Environments | Register your own machines or containers as runners so Claude Code web, mobile, and desktop sessions can execute on them, available on Team and Enterprise plans. | `claude self-hosted-runner` | `2.1.224` | Aug 2026 |
| [Screen Reader Mode](https://code.claude.com/docs/en/cli-reference) | Opt-in plain-text rendering for screen reader users, replacing decorative borders and animations with flat, accessible output. | `claude --ax-screen-reader`; `axScreenReader` setting | `2.1.208` | Jul 2026 |
| [Claude Platform on AWS (Gateway)](https://code.claude.com/docs/en/claude-apps-gateway) | Route Claude Code through Claude Platform on AWS as a gateway upstream provider, alongside Bedrock, Vertex, and Foundry. | `provider: anthropicAws` in gateway config | `2.1.198` | Jul 2026 |
| `fallbackModel` Setting | Configure up to three fallback models tried in order when the primary model is overloaded or unavailable, applying to both interactive and `-p` sessions. | `fallbackModel` in settings; `--fallback-model` flag | `2.1.166` | Jun 2026 |
| Auto Mode on Bedrock/Vertex/Foundry (GA Jul 2026) | Auto mode is available on Amazon Bedrock, Vertex AI, and Azure Foundry for Opus 4.7/4.8, and no longer requires an opt-in on those platforms. | Automatic; disable via `disableAutoMode` in settings | `2.1.158` | May 2026 |
| Native Binary | Claude Code ships as a native compiled binary instead of Node.js, improving performance and startup time. | Automatic in new installs | `2.1.113` | Apr 2026 |
| Push Notifications (Mobile) | Claude sends push notifications to your phone when tasks complete or need attention, via Remote Control. | Enable in `/config` | `2.1.110` | Apr 2026 |
| Amazon Bedrock Mantle | Use Claude Code against Claude models hosted via Amazon Bedrock powered by Mantle. | `CLAUDE_CODE_USE_MANTLE=1` | `2.1.94` | Apr 2026 |
| PowerShell Tool (Windows) | Claude executes PowerShell commands on Windows as a first-class tool alongside Bash. | Automatic on Windows; `CLAUDE_CODE_USE_POWERSHELL_TOOL=1` | `2.1.84` | Mar 2026 |
| [Remote Control](https://code.claude.com/docs/en/remote-control) | Bridge a local CLI session to claude.ai/code to continue from a browser or mobile device. | `claude remote-control`; `/remote-control` | `2.1.51` | Feb 2026 |
| [claude.ai MCP Connectors](https://code.claude.com/docs/en/mcp) | Use cloud service connectors (Slack, Gmail, etc.) from claude.ai directly in Claude Code sessions. | Automatic when logged into claude.ai | `2.1.46` | Feb 2026 |
| LSP Tool | Code intelligence features including go-to-definition, find references, and hover documentation. | LSP server configured in settings | `2.0.74` | Dec 2025 |
| [Claude in Chrome (GA Jul 2026)](https://code.claude.com/docs/en/chrome) | Control a connected Chrome browser directly from Claude Code via the Claude Chrome extension. | Chrome extension at claude.ai/chrome; `/chrome` | `2.0.72` | Dec 2025 |
| [Desktop App](https://claude.com/download) | Native desktop application for macOS and Windows with integrated session management. | [claude.com/download](https://claude.com/download) | `2.0.51` | Nov 2025 |
| [Microsoft Azure AI Foundry](https://code.claude.com/docs/en/azure-ai-foundry) | Use Claude Code with Claude models hosted on Microsoft Azure AI Foundry. | Azure env vars; setup wizard | `2.0.45` | Nov 2025 |
| [VS Code Extension](https://code.claude.com/docs/en/) | Full VS Code extension with session tabs, plan previews, IDE diff integration, and sidebar. | VS Code marketplace | `2.0.0` | Sep 2025 |
| [Streaming SDK Output](https://code.claude.com/docs/en/agent-sdk/overview) | The Claude Code SDK streams partial messages in real-time via `--include-partial-messages`. | `--include-partial-messages` | `1.0.109` | Sep 2025 |
| Native Windows Support | Claude Code runs natively on Windows without requiring WSL (requires Git for Windows or PowerShell). | `claude install` on Windows | `1.0.51` | Jul 2025 |
| [Claude Agent SDK](https://code.claude.com/docs/en/agent-sdk/overview) | TypeScript and Python SDKs for programmatic access to Claude Code features and sessions. | `@anthropic-ai/claude-code`; `pip install claude-code-sdk` | `1.0.23` | Jun 2025 |
| Streaming Print Mode | `--print` mode with real-time JSON output enables scripting and CI integration. | `claude -p --output-format=stream-json` | `0.2.66` | Apr 2025 |
| Import MCP Servers from Claude Desktop | Import MCP server configurations from Claude Desktop with a single command. | `claude mcp add-from-claude-desktop` | `0.2.36` | Mar 2025 |

## Security & Governance

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [`--restricted` Flag](https://code.claude.com/docs/en/cli-reference) | Start Claude Code in a locked-down mode for shared or evaluation-harness machines: removes the built-in tools that run commands or code and `WebFetch` unless named individually, confines file tools to the working directory, refuses `bypassPermissions`, and ignores user/project/local settings files. | `claude --restricted`; `CLAUDE_CODE_RESTRICTED=1` | `2.1.248` | Aug 2026 |
| [EndConversation Tool](https://www.anthropic.com/research/end-subset-conversations) | Claude can end a session as a last resort with a highly abusive or jailbreak-attempting user, mirroring the safeguard already used on claude.ai. | Automatic (`EndConversation` tool) | `2.1.214` | Jul 2026 |
| [Org Default Models](https://code.claude.com/docs/en/model-config) | Admins set an organization- or role-wide default model from the console; it resolves for members who haven't picked one themselves and shows as "Org default" in the model picker. | Set in claude.ai admin console; shown in `/model` | `2.1.196` | Jun 2026 |
| [Sandbox Credential Protection](https://code.claude.com/docs/en/sandboxing) | The `sandbox.credentials` setting blocks sandboxed commands from reading specified credential files and unsets secret environment variables before each sandboxed command runs. | `sandbox.credentials.files`/`envVars` in settings | `2.1.187` | Jun 2026 |
| Org-Configured Model Restrictions | Admins can restrict which models are available via managed settings; the model picker, `--model`, `/model`, and `ANTHROPIC_MODEL` all enforce the allowlist with a clear "restricted by your organization" message. | `availableModels` in managed settings | `2.1.187` | Jun 2026 |
| `Tool(param:value)` Permission Rule Syntax | Deny and ask rules can match a tool call by any top-level input parameter value, e.g. `Agent(model:opus)` to block Opus subagents or `Bash(run_in_background:true)`. | `Tool(param:value)` in deny/ask rules | `2.1.178` | Jun 2026 |
| `enforceAvailableModels` Managed Setting | When enabled, the `availableModels` allowlist constrains the Default model resolution and prevents user or project settings from widening a managed model list. | `enforceAvailableModels: true` in managed settings | `2.1.175` | Jun 2026 |
| `requiredMinimumVersion` / `requiredMaximumVersion` | Managed settings that prevent Claude Code from starting if its version falls outside an admin-specified range, directing users to an approved version. | `requiredMinimumVersion`/`requiredMaximumVersion` in managed settings | `2.1.163` | Jun 2026 |
| `--safe-mode` Flag | Start Claude Code with all customizations (CLAUDE.md, plugins, skills, hooks, MCP servers) disabled for troubleshooting or security isolation. | `claude --safe-mode`; `CLAUDE_CODE_SAFE_MODE` env var | `2.1.169` | Jun 2026 |
| Shell Startup File & Build-Config Write Prompts | Claude Code prompts before writing to shell startup files (`.zshenv`, `.bashrc`, etc.) and `acceptEdits` mode prompts before writing build-tool config files that grant code execution (`.npmrc`, `.bazelrc`, `.pre-commit-config.yaml`, etc.). | Automatic | `2.1.160` | Jun 2026 |
| Auto Mode | Permission mode using AI safety classification to approve or deny tool use without per-action prompts. | `--permission-mode auto`; `Shift+Tab` cycle | `2.1.111` | Apr 2026 |
| [Subprocess Sandboxing](https://code.claude.com/docs/en/sandboxing) | Bash tool processes run in isolated PID namespaces on Linux with per-session script invocation limits. | `CLAUDE_CODE_SUBPROCESS_ENV_SCRUB=1`; `sandbox` settings | `2.1.98` | Apr 2026 |
| Managed Settings Drop-in Directory | Enterprise policy fragments in `managed-settings.d/` are merged alphabetically at startup. | `managed-settings.d/` directory | `2.1.83` | Mar 2026 |
| Enterprise Managed Settings | Admins deploy policy settings via `managed-settings.json`, macOS plist, or Windows Registry. | `managed-settings.json` | `2.0.68` | Dec 2025 |
| OpenTelemetry Integration | Emit tool decisions, session metrics, LLM request spans, and active time to any OTLP endpoint. | `OTEL_EXPORTER_OTLP_ENDPOINT` env var | `1.0.39` | Jul 2025 |

## Other Improvements

Notable changes that fell below the threshold for the main tables:

- `PreModelSwitch`/`PostModelSwitch` Hook Events (`2.1.251`) - *incremental improvement*
- `SessionStart` Resume Hooks Receive Session Staleness and Re-Cache Cost (`2.1.251`) - *incremental improvement*
- Live Streaming of Foreground Subagent Tool Calls to Remote Control (`2.1.251`) - *incremental improvement*
- Spend Limit Bar in `/usage` and `rate_limits.spend_limit` Status Line Field (`2.1.251`) - *config knob*
- Per-Session Prompt-Cache Line in `/cost` (`2.1.251`) - *incremental improvement*
- `experimental.cacheTtl` Agent Frontmatter Setting (`2.1.248`) - *config knob*
- `claude self-hosted-runner --client-label` Flag (`2.1.248`) - *config knob*
- Server-Managed Settings Load Diagnostics in `/doctor`/`/status` (`2.1.248`) - *incremental improvement*
- `/web-setup` Warning for Missing GitHub CLI `workflow` Scope (`2.1.248`) - *incremental improvement*
- `/usage-credits` for AWS-Marketplace-Billed and Self-Serve Enterprise (`2.1.248`) - *incremental improvement*
- Cross-Session Messaging on Bedrock/Vertex/Foundry and With Telemetry Disabled (`2.1.248`) - *platform expansion*
- `SendFeedback` Tool for Claude-Drafted Feedback Reports (`2.1.247`) - *convenience wrapper*
- `spinnerTipsOverride` Gains Cooldown/Priority Fields and `tipsFile` (`2.1.247`) - *config knob*
- Auto Mode Tip on Bash Permission Prompts (`2.1.247`) - *UI polish*
- `/claude-api cost-optimize` Subcommand (`2.1.247`) - *convenience wrapper*
- `/claude-api` Skill Admin API Coverage (`2.1.247`) - *incremental improvement*
- Startup Warning for Wildcard-Before-Subcommand Bash Allow Rules (`2.1.246`) - *incremental improvement*
- Auto Mode Tab in `/permissions` (`2.1.246`) - *incremental improvement*
- Turn Completion Time in Duration Line (`2.1.246`) - *UI polish*
- Loops Breakdown in `/usage` (`2.1.243`) - *incremental improvement*
- `modelPicker` Setting for Curated Model List (`2.1.243`) - *config knob*
- `promptCacheTtl`/`subagentPromptCacheTtl` Settings (`2.1.243`) - *config knob*
- `modelPricing` Managed Setting for Contracted Rates (`2.1.243`) - *config knob*
- Keyless Console Sign-In Option in `/login` (`2.1.243`) - *convenience wrapper*
- `/status` "Skipped Sources" Line for Managed Settings (`2.1.243`) - *incremental improvement*
- `managed` Marker for Org-Managed Connectors in `/mcp`/`/plugins` (`2.1.243`) - *incremental improvement*
- `/web-setup` Tip for Unconnected GitHub on claude.ai (`2.1.243`) - *UI polish*
- `/status` Line for Claude Code on the Web GitHub Connection (`2.1.243`) - *incremental improvement*
- Subagent Model and Effort Level Shown in `/tasks` (`2.1.243`) - *incremental improvement*
- `/goal` Check-In Backoff Schedule (`2.1.241`) - *incremental improvement*
- `/goal` Restores Active Goal on Session Resume (`2.1.241`) - *incremental improvement*
- `ListAgents` Surfaces Own Session Name and Live Teammates (`2.1.241`) - *incremental improvement*
- `keybindingFlavor: "readline"` Extended to Bash Word Navigation (`2.1.241`) - *power-user UX*
- Persistent Retry Mode Fails Immediately on Spend-Limit/Out-of-Credits Errors (`2.1.241`) - *incremental improvement*
- Claude in Chrome `/clear` Closes Session's Chrome Tab Group (`2.1.241`) - *incremental improvement*
- Windows Cross-Session Messaging Support (`2.1.241`) - *platform expansion*
- Bash Requests to Non-API Anthropic Hosts Routed Through Session's Network Proxy (`2.1.241`) - *security infrastructure*
- Data-Residency Cost Estimates Include US-Only-Inference Premium (`2.1.239`) - *incremental improvement*
- Fullscreen Renderer Offer Extended to Bedrock/Vertex/Foundry (`2.1.239`) - *platform expansion*
- `/claude-api upgrade` Python Migration Command (`2.1.239`) - *convenience wrapper*
- Cloud-Synced Plugins Shown as `name@synced` (`2.1.239`) - *incremental improvement*
- Alpine/musl Native Add-ons (Paste, Clipboard, Audio Capture) (`2.1.239`) - *platform expansion*
- `keybindingFlavor` Setting (`2.1.238`) - *power-user UX*
- Plugin Marketplace `headersHelper` for URL Marketplaces (`2.1.238`) - *incremental improvement*
- `claude self-hosted-runner --defer-shutdown-max-min` Flag (`2.1.238`) - *config knob*
- `claude self-hosted-runner --proxy-authorization-*` Flags (`2.1.238`) - *config knob*
- `claude mcp list`/`get` Show Disabled Servers Without Health Check (`2.1.238`) - *incremental improvement*
- Built-in "Concise" Output Style (`2.1.237`) - *convenience wrapper*
- [VSCode] Screen Reader Support for Transcript (`2.1.237`) - *platform expansion*
- `ANTHROPIC_DEFAULT_MODEL` Environment Variable (`2.1.236`) - *config knob*
- `notify_when_idle` for Cross-Session `SendMessage` (`2.1.236`) - *incremental improvement*
- macOS Sandbox Wildcard Read-Deny Precedence Hardening (`2.1.236`) - *security infrastructure*
- `spellcheck` Setting for Prompt Input (`2.1.235`) - *power-user UX*
- `CLAUDE_CODE_PROJECT_DIR_NAME` Environment Variable (`2.1.234`) - *config knob*
- `selection:clear` Keybinding Action (`2.1.234`) - *config knob*
- Auto-Continue Session at Usage-Limit Reset (`2.1.234`) - *incremental improvement*
- Windows NT-Namespace Path Rejection Hardening (`2.1.234`) - *security infrastructure*
- `forward_user_identity` Apps Gateway Setting (`2.1.233`) - *config knob*
- `CLAUDE_CODE_TOOL_MEMORY_LIMIT` Bash Memory Cgroup (`2.1.233`) - *config knob*
- `CLAUDE_CODE_WEBFETCH_CACHE_TTL_MS` Environment Variable (`2.1.233`) - *config knob*
- Task-Tracking Tools Disabled by Default on Newer Models (`2.1.233`) - *config knob*
- Subagent Forking and Background Spawn On by Default (`2.1.232`) - *incremental improvement*
- `@` Mention Syntax to Reach Another Session (`2.1.232`) - *convenience wrapper*
- `SendMessage` Delivers to Unambiguous Bare Session Name (`2.1.232`) - *incremental improvement*
- Interactive Sessions Auto-Dedupe Names (`2.1.232`) - *incremental improvement*
- `/config` Rows for Dialog Expiry and Cross-Session Message Handling (`2.1.232`) - *config knob*
- `additionalMarketplaces`/`allowedMarketplaces` Setting Aliases (`2.1.232`) - *config knob*
- Owner-Level `blockedMarketplaces` URL Entries (`2.1.232`) - *config knob*
- Gateway `desktop:` Overlay Accepts All Desktop Settings (`2.1.232`) - *incremental improvement*
- Fable 5 Advisor Access Restored (`2.1.232`) - *incremental improvement*
- Server-Supplied Hooks for Self-Hosted Runner Sessions (`2.1.229`) - *incremental improvement*
- Gateway Streaming SSE Keepalive Pings (`2.1.229`) - *incremental improvement*
- Plugin Marketplace `command` Sources (`2.1.229`) - *incremental improvement*
- `ListAgents` Marks Disconnected Remote Control Sessions Offline (`2.1.229`) - *incremental improvement*
- Hardened Claude.ai-Synced Skills (Sandboxing, Sanitized Descriptions) (`2.1.228`) - *security infrastructure*
- Write Tool Allows Overwrite Without Prior Read on Newer Models (`2.1.228`) - *incremental improvement*
- Gateway Spend-Limit Details in Usage Warning (`2.1.225`) - *config knob*
- Workspace Trust Prompt for `claude agents` (`2.1.225`) - *security infrastructure*
- `SendMessage` Reaches Remote Control Sessions by Name (`2.1.225`) - *incremental improvement*
- `archive` Plugin Source (Zip Install, SHA-256 Pinning) (`2.1.224`) - *incremental improvement*
- `crossSessionInbound`/`dialogExpiry` Settings (`2.1.224`) - *config knob*
- Sandbox Credential-Masking Options (JWT, AWS SigV4) (`2.1.224`) - *config knob*
- 200-Subagent Spawn Cap Removed (`2.1.224`) - *config knob*
- Owner-Wildcard Marketplace Entries (`2.1.223`) - *config knob*
- Restricted Subagent Model Fallback Warning (`2.1.223`) - *incremental improvement*
- `/teleport` Hint in Cloud Sessions (`2.1.223`) - *convenience wrapper*
- `/review` Aliased to `/code-review`; `/code-review ultra` Replaces `/ultrareview` (`2.1.223`) - *incremental improvement*
- [VSCode] Focus View for Tool-Activity Summaries (`2.1.221`) - *UI polish*
- Sandbox Credential File `mode: "mask"` (`2.1.221`) - *config knob*
- `claude plugin validate` Desktop Marketplace-Sync Warnings (`2.1.221`) - *incremental improvement*
- `prompt-audit` Subcommand for `claude-api` Skill (`2.1.221`) - *convenience wrapper*
- Background Sessions Open Draft PR Only When Warranted (`2.1.221`) - *incremental improvement*
- Emoji Autocomplete Accepts Alternate Shortcodes (`2.1.221`) - *convenience wrapper*
- `/fork` Sessions Create Their Own Worktree (`2.1.221`) - *incremental improvement*
- Claude in Chrome Closes Tabs It Opened (`2.1.221`) - *incremental improvement*
- Fast Mode Reports Mid-Session Usage-Credit Exhaustion (`2.1.221`) - *incremental improvement*
- `/status` Shows Session Kind (Interactive/Attached/Unattended) (`2.1.221`) - *format/scripting flag*
- Claude Opus 5 model release (`2.1.219`) - *Model releases (Claude Opus 5) — tracked separately*
- `sandbox.network.strictAllowlist` Setting (`2.1.219`) - *config knob*
- `DirectoryAdded` Hook Event (`2.1.219`) - *incremental improvement*
- `mcp_server_errors` in Headless Stream-JSON Init Event (`2.1.219`) - *format/scripting flag*
- `workflowSizeGuideline` Settings Key (`2.1.219`) - *config knob*
- Nested Subagent Forwarding in Stream-JSON Output (`2.1.219`) - *format/scripting flag*
- HTTP Status and Error Text in `claude mcp list`/`/mcp` (`2.1.219`) - *incremental improvement*
- Dynamic Workflows Default to Medium Size Guideline (`2.1.219`) - *config knob*
- Running-Workflow Status Line Shows Default Workflow Size (`2.1.219`) - *incremental improvement*
- Fast Mode Drops Opus 4.7, Applies to Opus 5 and 4.8 (`2.1.219`) - *incremental improvement*
- Nested Subagent Default Spawn Depth Raised to 3 (`2.1.219`) - *config knob*
- `/code-review` Runs as a Background Subagent by Default (`2.1.218`) - *incremental improvement*
- Screen-Reader Announcements for Deleted Text (`2.1.218`) - *incremental improvement*
- `/ultrareview` Error Feedback for Invalid Arguments (`2.1.218`) - *incremental improvement*
- Auto Mode Classifier Adjudicates dangerous-rm/background-&/Windows-Path Commands (`2.1.218`) - *incremental improvement*
- Trust Dialogs Name the Repository Root (`2.1.218`) - *UI polish*
- `/deep-research` Starts Only When Invoked Manually (`2.1.218`) - *incremental improvement*
- Plan Mode with Auto Delegates Non-Provably-Read-Only Bash Commands to the Auto Mode Classifier (`2.1.218`) - *incremental improvement*
- Fast Mode Change Announcement on Model Switch (`2.1.218`) - *UI polish*
- Server-Managed Settings: Benign Toggles Skip Approval Prompt (`2.1.218`) - *incremental improvement*
- Agent Names Reject `:` Character, Reserved for Plugin Namespacing (`2.1.218`) - *config knob*
- `context: fork` Skills Run in Background by Default (`2.1.218`) - *incremental improvement*
- Boolean Frontmatter Accepts yes/no/on/off/1/0 (`2.1.218`) - *format/scripting flag*
- Emoji Shortcode Autocomplete (`2.1.217`) - *convenience wrapper*
- Transcript Write Failure Warnings (`2.1.217`) - *incremental improvement*
- Clickable Footer PR Badge Hyperlinks (`2.1.217`) - *UI polish*
- Login-Expiry Warning Now 3 Days Before Expiry (`2.1.217`) - *config knob*
- Concurrent Subagent Cap, Default 20 (`2.1.217`) - *config knob*
- Subagents No Longer Spawn Nested Subagents by Default (`2.1.217`) - *config knob*
- `sandbox.filesystem.disabled` Setting (`2.1.216`) - *config knob*
- `/fork` Confirmation Shows Session Name and Attach ID (`2.1.216`) - *UI polish*
- `/ultrareview` Diff-Too-Large Error Detail (`2.1.216`) - *incremental improvement*
- `/code-review ultra` Empty-Diff Error Names Base Ref (`2.1.216`) - *incremental improvement*
- Spend Limit Adjustment Prompt Shows Server's Rejection Reason (`2.1.216`) - *incremental improvement*
- `/context` Warns When Conversation Exceeds Context Window (`2.1.216`) - *incremental improvement*
- Background Sessions Park `/mcp`/`/install-github-app` Needs-Input Requests in Agent View (`2.1.216`) - *incremental improvement*
- Manual-only invocation for `/verify` and `/code-review` skills (`2.1.215`) - *incremental improvement*
- Permission prompts for `docker` daemon-redirect flags (`2.1.214`) - *incremental improvement*
- Reasoning effort in `subagentStatusLine` payload (`2.1.214`) - *config knob*
- ISO `modified` timestamp in memory file frontmatter (`2.1.214`) - *config knob*
- OpenTelemetry `message.uuid`/`client_request_id`/`tool_source` attributes (`2.1.214`) - *format/scripting flag*
- `CLAUDE_CODE_OTEL_CONTENT_MAX_LENGTH` Setting (`2.1.214`) - *config knob*
- Periodic progress heartbeat for long-running tool calls (`2.1.214`) - *incremental improvement*
- `claude auto-mode reset` Command (`2.1.212`) - *convenience wrapper*
- Session-wide WebSearch call limit (`2.1.212`) - *config knob*
- Per-session subagent spawn cap (`2.1.212`) - *config knob*
- MCP tool calls over 2 minutes auto-background (`2.1.212`) - *incremental improvement*
- `/resume` picker in agent view resumes past sessions as background sessions (`2.1.212`) - *incremental improvement*
- `--forward-subagent-text` Flag (`2.1.211`) - *format/scripting flag*
- Live elapsed-time counter on tool summary line (`2.1.210`) - *UI polish*
- Startup warning for `Write`/`NotebookEdit`/`Glob` path-based permission rules (`2.1.210`) - *incremental improvement*
- `vimInsertModeRemaps` Setting (`2.1.208`) - *power-user UX*
- `CLAUDE_CODE_PROCESS_WRAPPER` corporate launcher wrapper (`2.1.208`) - *config knob*
- Mouse-click support for multi-select menus in fullscreen mode (`2.1.208`) - *UI polish*
- Bedrock/Vertex/Claude Platform on AWS default to Opus 4.8 (`2.1.207`) - *incremental improvement*
- `/cd` Directory Path Suggestions (`2.1.206`) - *incremental improvement*
- `/doctor` CLAUDE.md trimming check (`2.1.206`) - *incremental improvement to existing /doctor*
- `/commit-push-pr` auto-allows push to configured push remote (`2.1.206`) - *incremental improvement*
- Gateway `/login` support for Anthropic-operated public gateway endpoints (`2.1.206`) - *platform expansion*
- Auto mode rule blocking session transcript tampering (`2.1.205`) - *incremental improvement to existing Auto Mode*
- Agent view PR linking for edit/merge/comment/push actions (`2.1.205`) - *incremental improvement*
- Login-expiry warning (`2.1.203`) - *UI polish*
- Manual permission mode footer badge (`2.1.203`) - *UI polish*
- MCP `roots/list` working directories with `list_changed` notifications (`2.1.203`) - *incremental improvement to existing MCP support*
- "Dynamic workflow size" setting in `/config` (`2.1.202`) - *config knob*
- `workflow.run_id`/`workflow.name` OpenTelemetry attributes (`2.1.202`) - *format/scripting flag*
- `/code-review <level> <pr#>` effort-level parameter (`2.1.202`) - *config knob*
- `AskUserQuestion` no longer auto-continues by default; idle timeout via `/config` (`2.1.200`) - *config knob*
- Default permission mode renamed to "Manual" (`2.1.200`) - *incremental improvement*
- Stacked slash-skill invocations load up to 5 leading skills (`2.1.199`) - *incremental improvement*
- Automatic retry with backoff for transient rate-limit errors (`2.1.199`) - *incremental improvement*
- `CLAUDE_CODE_RETRY_WATCHDOG` raised default retry count (`2.1.199`) - *config knob*
- Background agent notifications (`agent_needs_input`/`agent_completed`) (`2.1.198`) - *incremental improvement to existing Notification hook*
- `/dataviz` bundled skill for chart/dashboard design (`2.1.198`) - *convenience wrapper*
- Explore agent inherits session model instead of haiku (`2.1.198`) - *incremental improvement*
- Subagents and compaction inherit session's extended thinking config (`2.1.198`) - *incremental improvement*
- Claude Sonnet 5 model release (`2.1.197`) - *Model releases (Claude Sonnet 5) — tracked separately*
- Readable default session names at start (`2.1.196`) - *incremental improvement*
- Clickable file attachments in chat (`2.1.196`) - *convenience wrapper*
- `CLAUDE_CODE_DISABLE_MOUSE_CLICKS` Setting (`2.1.195`) - *config knob*
- `autoMode.classifyAllShell` Setting (`2.1.193`) - *config knob*
- Auto-mode denial reasons in transcript, toast, and `/permissions` (`2.1.193`) - *incremental improvement*
- `claude_code.assistant_response` OpenTelemetry log event (`2.1.193`) - *format/scripting flag*
- Live file path autocomplete in bash mode (`2.1.193`) - *incremental improvement*
- Automatic memory-pressure reaping for idle background shell commands (`2.1.193`) - *incremental improvement*
- `/rewind` support for resuming from before `/clear` (`2.1.191`) - *incremental improvement*
- `claude mcp login/logout <name>` CLI commands (`2.1.186`) - *convenience wrapper*
- `respondToBashCommands: false` Setting (`2.1.186`) - *config knob*
- `attribution.sessionUrl` Setting (`2.1.183`) - *config knob*
- Auto mode destructive git command blocks (`2.1.183`) - *incremental improvement*
- `/config key=value` Inline Setting Syntax (`2.1.181`) - *config knob*
- `sandbox.allowAppleEvents` Setting (`2.1.181`) - *config knob*
- `CLAUDE_CLIENT_PRESENCE_FILE` Env Var (`2.1.181`) - *config knob*
- Agent Teams implicit team (TeamCreate/TeamDelete removed) (`2.1.178`) - *incremental improvement*
- Skills in nested `.claude/skills` directories load with directory-qualified names (`2.1.178`) - *incremental improvement*
- Session titles generated in conversation language (`2.1.176`) - *incremental improvement*
- `footerLinksRegexes` Setting (`2.1.176`) - *config knob*
- `wheelScrollAccelerationEnabled` Setting (`2.1.174`) - *config knob*
- VSCode: Usage attribution breakdown in `/usage` (`2.1.174`) - *incremental improvement*
- Marketplace plugin search bar in `/plugin` (`2.1.172`) - *UI polish*
- Bedrock reads AWS region from `~/.aws` config files (`2.1.172`) - *incremental improvement*
- Claude Fable 5 / Mythos 5 model release (`2.1.170`) - *Model releases (Fable 5, Mythos 5) — tracked separately*
- `disableBundledSkills` Setting (`2.1.169`) - *config knob*
- glob pattern support in deny rule tool-name position (`2.1.166`) - *incremental improvement*
- `/plugin list` Command (`2.1.163`) - *convenience wrapper*
- Skills `\$` escape syntax for literal `$` before digits (`2.1.163`) - *incremental improvement*
- Renamed Windsurf to Devin Desktop in IDE menus (`2.1.162`) - *incremental improvement*
- Remote Control footer pill indicator (`2.1.162`) - *UI polish*
- `claude agents --json` `waitingFor` field (`2.1.162`) - *format/scripting flag*
- `/effort` persists-as-default confirmation (`2.1.162`) - *UI polish*
- `OTEL_RESOURCE_ATTRIBUTES` labels on metric datapoints (`2.1.161`) - *incremental improvement*
- `claude agents` rows show done/total progress before detail (`2.1.161`) - *UI polish*
- Edit after grep no longer requires separate Read (`2.1.160`) - *incremental improvement*
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
