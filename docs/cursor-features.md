# Cursor Features (Mar 2023 – Aug 2026)

Significant user-facing features added to Cursor since its public availability.
**Last updated:** Aug 9, 2026 · Source: [Cursor Changelog](https://cursor.com/changelog)

## Agentic & Multi-Agent

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Cloud Subagents (`/in-cloud`)](https://cursor.com/docs/background-agent) | Spins up isolated cloud VM subagents from within an agent session to run tasks in parallel without blocking local work. | `/in-cloud` in agent chat | `3.7` | Jun 2026 |
| [Development Environments for Cloud Agents](https://cursor.com/docs/cloud-agent/setup) | Defines a versioned, Dockerfile-based build (with build secrets and layer caching) that Cursor uses as the base image for every cloud agent run against a repo, replacing ad hoc environment setup. | Commit `Dockerfile`; Dashboard → Environments | `3.4` | May 2026 |
| [Multitask, Worktrees, and Multi-root Workspaces](https://cursor.com/docs/background-agent) | `/multitask` deploys async subagents for parallel execution; worktrees allow isolated background tasks across branches; multi-root workspaces let one agent session target multiple folders. | `/multitask`; worktree UI | `3.2` | Apr 2026 |
| [Cursor Automations](https://cursor.com/docs/automations) | Always-on cloud agents triggered by schedules, Slack messages/reactions, GitHub/GitLab events, Linear, PagerDuty, and webhooks; agents learn from past runs via memory tools. | Dashboard → Automations; `/automate` skill | N/A | Mar 2026 |
| [Self-hosted Cloud Agents](https://cursor.com/docs/background-agent) | Runs code and tool execution entirely within a customer's own network using isolated VMs, so no data leaves the organization's infrastructure. | Dashboard setting | N/A | Mar 2026 |
| [Long-running Agents](https://cursor.com/docs/background-agent) | Agents autonomously complete complex tasks over extended periods with upfront planning; available in research preview for Ultra, Teams, and Enterprise plans. | cursor.com/agents | N/A | Feb 2026 |
| [Bugbot Autofix](https://cursor.com/docs/bugbot) | Cloud agents running in isolated VMs generate and test fixes for Bugbot-identified PR bugs and push fix branches; over 35% of fixes are merged. | PR comment `@cursor`; auto-push option | N/A | Feb 2026 |
| [Multi-Agents (Parallel Agent Execution)](https://cursor.com/docs/background-agent) | Runs up to eight agents simultaneously in git worktrees locally or in the cloud, with an Agents Window for side-by-side management. | Agents Window (Cmd+Shift+A) | `2.0` | Oct 2025 |
| [Background Agents (Cloud Agents)](https://cursor.com/docs/background-agent) | Remote agents execute tasks in secure cloud environments in parallel with local work, producing PRs without occupying the local machine. | Cloud icon; Cmd/Ctrl+E | `0.50` | May 2025 |

## Context & Memory

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Side Chats & Conversation Search](https://cursor.com/changelog/side-chat) | Branches durable "side chat" threads off the main agent conversation for tangents and research without losing context, and locally indexes past agent transcripts so they can be searched by content. | `/side`, `/btw`, or + button in chat panel; Cmd+K to search transcripts | `3.11` | Jul 2026 |
| [Context Usage Breakdown](https://cursor.com/docs/context/rules) | Displays per-agent context usage statistics broken down by rules, skills, MCPs, and subagents to help diagnose and optimize setup. | Automatic; visible in agent chat | `3.3` | May 2026 |
| [Agent Planning / To-do Lists](https://cursor.com/docs/agent/plan-mode) | Agents create structured task checklists with dependencies before starting complex work; queued follow-up messages execute sequentially without waiting. | Automatic | `1.2` | Jul 2025 |
| [Memories (GA)](https://cursor.com/docs/context/rules) | Stores project-specific facts across conversations so agents recall prior decisions and preferences without re-stating them; reached GA with PR indexing support. | Automatic; Memories panel | `1.2` | Jul 2025 |
| [Memories (Preview)](https://cursor.com/docs/context/rules) | Preview release of persistent per-project memory that survives session boundaries. | Automatic | `1.0` | Jun 2025 |
| [`.cursor/rules` Project Rules](https://cursor.com/docs/context/rules) | Per-repository AI guidelines stored in `.cursor/rules` with automatic agent selection; supersedes `.cursorrules` flat file and adds nested directory support. | Auto-applied; Settings > Rules | `0.45` | Jan 2025 |
| [@Git Context](https://cursor.com/docs/context/rules) | Surfaces recent git history and diffs as context for agent reasoning about repository changes. | `@git` in chat | `0.12` | Oct 2023 |
| [Docs Management](https://cursor.com/docs/context/rules) | Users add, remove, and cite custom documentation URLs so agents can fetch and reference up-to-date external docs. | Settings > Features > Docs; paste URL in chat | `0.36` | Jul 2024 |
| [`@Web` Live Web Search](https://cursor.com/docs/context/rules) | Lets agents crawl the web in real time using a search engine and documentation-site crawler to answer questions with up-to-date information. | `@web` in chat | `0.24` | Jan 2024 |

## Model & Input

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Cursor Router](https://cursor.com/docs/cursor-router) | An intelligent model router, trained on real usage, classifies each agent request and routes it to the best-suited underlying model along a configurable cost/intelligence trade-off. | Auto mode → Intelligence/Balance/Cost | N/A | Jul 2026 |
| [Image Generation](https://cursor.com/docs/context/rules) | Creates images directly within agent chat sessions using supported image-generation models. | Natural language prompt in agent | `2.4` | Jan 2026 |
| [Voice Mode](https://cursor.com/docs/tab/overview) | Speech-to-text control of the agent via microphone with batch STT for higher quality; voice input remains available during agent runs for async change queuing. | Microphone icon | `2.0` | Oct 2025 |
| [Multi-model Selection per Agent](https://cursor.com/docs/context/rules) | Users pick different AI models per individual agent session, independent of the global default. | Model picker in agent chat | `1.4` | Aug 2025 |
| [PDF Parsing](https://cursor.com/docs/context/rules) | Parses PDF files attached via `@Link` or web search so agents can read document content. | `@Link` with PDF URL; drag-and-drop | `1.0` | Jun 2025 |
| [Max Mode (token-based pricing)](https://cursor.com/docs/context/rules) | Unlocks top-tier models (GPT-4, Claude, Gemini) at token-based pricing for tasks requiring maximum intelligence, separate from request-based pricing. | Model picker → Max toggle | `0.50` | May 2025 |
| [Image (Vision) Support in Chat](https://cursor.com/docs/context/rules) | Drag-and-drop images into the chat or Command-K bar for visual context in agent and edit requests. | Drag image into chat / Cmd+K bar | `0.17` | Nov 2023 |

## Built-in Workflows

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Cursor Security Review](https://cursor.com/docs/bugbot) | Two specialized agents — Security Reviewer (PR diff analysis for vulnerabilities, auth regressions, prompt injection) and Vulnerability Scanner (scheduled codebase audits) — report findings inline and to Slack. | Dashboard → Security; `/review` before push | N/A | Apr 2026 |
| [Debug Mode](https://cursor.com/docs/agent/plan-mode) | Instruments apps with runtime logs across stacks to help the agent identify root causes; includes a browser sidebar for simultaneous design and code inspection. | `/debug` in agent or CLI | `2.2` | Dec 2025 |
| [Bugbot PR Code Review](https://cursor.com/docs/bugbot) | Automated AI review of every pull request diff that leaves inline comments with explanations and fix suggestions; integrates with GitHub, GitLab, and Bitbucket. | Automatic on PR update; `/review` command | `1.0` | Jun 2025 |
| [AI Code Review in Editor](https://cursor.com/docs/bugbot) | Surfaces AI-identified bugs directly inside the editor alongside Bugbot integration, without leaving the coding environment. | Automatic; Review panel | `2.1` | Nov 2025 |
| [Plan Mode](https://cursor.com/docs/agent/plan-mode) | Generates a comprehensive implementation plan with clarifying questions and a structured checklist before writing any code; supports inline Mermaid diagrams. | Shift+Tab; `/plan`; `--mode=plan` (CLI) | `1.7` | Sep 2025 |
| [Multi-Agent Judging / Best-of-N](https://cursor.com/docs/background-agent) | Runs multiple parallel agent attempts and automatically evaluates them to recommend the best solution. | `/best-of-n` command | `2.2` | Dec 2025 |
| [Composer / Multi-file Editing (GA)](https://cursor.com/docs/agent/plan-mode) | Agentic multi-file editing interface now enabled by default; applies diffs across files, tracks checkpoints, and handles terminal commands. | Cmd/Ctrl+I | `0.40` | Aug 2024 |
| [Inline Edit (Command-K)](https://cursor.com/docs/cmdk/overview) | Inline prompt bar for editing code at the cursor position using AI; supports natural-language instructions, image context, and diff previews. | Cmd/Ctrl+K | `0.1` | Mar 2023 |
| [Instant Apply](https://cursor.com/docs/agent/plan-mode) | One-click application of AI-suggested code blocks from chat directly into the editor with an in-place diff preview. | Apply button on code block | `0.36` | Jul 2024 |

## Extensibility

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Cursor SDK (Public Beta)](https://cursor.com/docs/plugins) | TypeScript SDK for building custom agents using the same runtime, models, and VMs that power Cursor's desktop and cloud products, deployable locally or to the cloud. | `npm install @cursor/sdk` | N/A | Apr 2026 |
| [Plugins & Cursor Marketplace](https://cursor.com/docs/plugins) | Plugin bundles combining MCP servers, skills, subagents, rules, and hooks; a public Marketplace hosts first-party and partner plugins (AWS, Figma, Linear, Atlassian, Datadog, GitLab, etc.). | Marketplace UI; team marketplace for admins | `2.5` | Feb 2026 |
| [Subagents & Skills](https://cursor.com/docs/agent/subagents) | Custom subagents defined in Markdown files encapsulate specialized tasks; Skills (`SKILL.md`) provide domain-specific capabilities discovered dynamically by the agent. | Custom `.cursor/agents/`; `SKILL.md` files | `2.4` | Jan 2026 |
| [Hooks](https://cursor.com/docs/agent/hooks) | Custom scripts attached to agent loop lifecycle events (before/after tool calls, file edits, agent start/stop) to observe and control agent behavior. | `.cursor/hooks/`; project or user level | `1.7` | Sep 2025 |
| [MCP (Model Context Protocol) Support](https://cursor.com/docs/mcp) | Connects Cursor to external tools and data sources via MCP servers, supporting stdio, SSE, and HTTP transports, with one-click installation and OAuth authentication. | Settings > MCP; one-click install | `1.6` | Sep 2025 |
| [Custom Slash Commands](https://cursor.com/docs/context/rules) | Reusable prompt templates stored as slash commands and shareable across a team, invokable from agent chat. | `/` in chat; Settings > Commands | `1.6` | Sep 2025 |
| [MCP Apps (Interactive UIs)](https://cursor.com/docs/mcp) | MCP servers can render structured interactive UI components — charts, diagrams, whiteboards — inside agent chats. | Via connected MCP server | `2.6` | Mar 2026 |
| [Custom Agent Modes](https://cursor.com/docs/agent/plan-mode) | Users define custom agent operating modes with unique keybindings, tool permissions, and instructions, in addition to the built-in Agent, Ask, and Plan modes. | Settings > Custom Modes | `0.48` | Mar 2025 |

## Platforms & Environments

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Cursor Mobile App for iOS](https://cursor.com/blog/ios-mobile-app) | Native iOS app (public beta) for launching, monitoring, and remotely directing desktop and cloud agents from a phone, with voice input, model selection, and PR review/merge on the go. | Cursor app on the App Store | `3.9` | Jun 2026 |
| [Cursor in Jira](https://cursor.com/docs/background-agent) | Assigns Jira work items to Cursor or accepts `@Cursor` mentions in comments to trigger cloud agents that fix bugs, add features, and post PR links back in the issue. | Jira comment `@Cursor`; assign to Cursor | N/A | May 2026 |
| [Cursor in Microsoft Teams](https://cursor.com/docs/background-agent) | Allows users to mention `@Cursor` in Teams channels to delegate coding tasks to cloud agents, which select repos, read thread context, and create PRs. | Teams channel `@Cursor` | N/A | May 2026 |
| [Cursor CLI](https://cursor.com/docs/background-agent) | Standalone command-line agent with Plan, Ask, and Debug modes, cloud handoff, word-level diffs, MCP authentication, and session lifecycle hooks. | `cursor` CLI | N/A | Jan 2026 |
| [JetBrains IDE Integration](https://cursor.com/docs/background-agent) | Cursor's agent available inside IntelliJ IDEA, PyCharm, and WebStorm via the Agent Client Protocol, supporting frontier models from all major providers. | JetBrains plugin | N/A | Mar 2026 |
| [Background Agents in Slack](https://cursor.com/docs/background-agent) | Launches Background Agents by mentioning `@Cursor` in a Slack thread; agents read thread context and post PR links back to the channel. | Slack mention `@Cursor` | `1.1` | Jun 2025 |
| [Background Agents from Linear](https://cursor.com/docs/background-agent) | Triggers cloud agents directly from Linear issues to implement the described work and create a PR. | Linear issue → Assign to Cursor | `1.5` | Aug 2025 |
| [Jupyter Notebook Support](https://cursor.com/docs/background-agent) | Agents can read, edit, and execute multi-cell Jupyter Notebooks, with checkpoints, full-notebook Tab awareness, and MCP elicitation support. | Chat or agent targeting `.ipynb` files | `1.5` | Aug 2025 |
| [Remote SSH Support](https://cursor.com/docs/background-agent) | Connects Cursor to remote Linux and macOS machines over SSH, including support for multiple proxy jumps and Remote Tunnels. | Settings > Remote SSH | `0.35` | Jun 2024 |
| [Dev Container Support](https://cursor.com/docs/background-agent) | Opens and develops inside Docker-based development containers, aligning the Cursor environment with the project's container spec. | Reopen in Container | `0.22` | Jan 2024 |

## Security & Governance

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Enterprise Organizations (Multi-level Hierarchy)](https://cursor.com/docs/enterprise) | Org → Team → Group hierarchy with organization-level IDP management, usage analytics, CSV user imports, and automatic permission inheritance for new team members. | Enterprise dashboard | `3.9` | Jun 2026 |
| [Enterprise Model Controls & Spend Management](https://cursor.com/docs/enterprise) | Admins configure provider- and model-level blocklists, set soft spend limits with threshold alerts (50%/80%/100%), and filter usage analytics by user and surface. | Enterprise admin dashboard | N/A | May 2026 |
| [Cursor Security Review (Beta)](https://cursor.com/docs/bugbot) | Automated security agents review PR diffs and scan codebases on a schedule for vulnerabilities, authentication regressions, and prompt-injection risks; findings post to Slack. | Dashboard → Security Review | N/A | Apr 2026 |
| [Self-hosted Cloud Agent Infrastructure](https://cursor.com/docs/background-agent) | Code and tool execution runs entirely within the customer's own network with isolated VMs, keeping data inside the organization's security boundary. | Enterprise dashboard | N/A | Mar 2026 |
| [Enterprise Insights & Audit Logging](https://cursor.com/docs/enterprise) | Conversation analytics categorize agent work (bug fixes, refactoring, etc.); shared read-only transcripts with fork capability; audit logs for agent actions; billing groups with budget alerts. | Enterprise dashboard | N/A | Dec 2025 |
| [Linux Sandboxing](https://cursor.com/docs/enterprise) | Sandboxed terminal execution for agent commands on Linux (joins macOS GA support) to prevent unintended side effects outside the project directory. | Settings > Sandbox | N/A | Dec 2025 |
| [Sandboxed Terminals (macOS GA)](https://cursor.com/docs/enterprise) | Agents execute shell commands in a macOS sandbox by default, restricting file-system and network access to reduce blast radius of unintended commands. | Default-on (macOS); Settings > Sandbox | `2.0` | Oct 2025 |
| [Privacy Mode (Ghost Mode)](https://cursor.com/docs/enterprise) | Opt-in mode that prevents any code or prompts from being stored on Cursor's servers; all requests are zero-retention. | Settings > Privacy Mode | `0.32` | Apr 2024 |

## Other Improvements

Notable changes that fell below the threshold for the main tables:

- [Google Workspace Plugins](https://cursor.com/changelog/google-workspace-plugins) (agent access to Gmail, Google Drive, Calendar, Docs, Sheets, and Chat) (`Aug 2026`) - *incremental improvement* - content addition to the existing Plugins/Marketplace infrastructure
- Cursor on iPad (split-screen chats, richer diffs, inbox, full-PR review experience) (`Jul 2026`) - *platform expansion* - extends the existing Mobile App surface (previously iPhone-only) to iPad
- Cursor Start (₹649/month India-only plan bundling Grok 4.5, Composer, cloud agents, and mobile access) (`Jul 2026`) - *distribution channel* - new regional pricing/billing tier with no new capability
- Unified Remote Machines menu (combines local, team-pool, and remote workspace pickers with a multi-repo/multi-root toggle) (`Jul 2026`) — *UI polish* — consolidates existing environment-selection surfaces
- Admin usage analytics filterable by user and product surface (clients, Cloud Agents, Automations, Bugbot, Security Review) (`May 2026`) — *config knob* — extends existing Enterprise spend/usage controls
- Explore subagent model configuration (choose a specific model, inherit the parent's, disable Explore subagents, or set generic model aliases like `opus`) (`May 2026`) — *config knob* — tunes the existing Subagents primitive
- Improvements to Cursor in Slack (multi-repo environments, plan sharing, cross-channel messaging) (`Jul 2026`) — *incremental improvement* — enhances the existing Slack integration surface
- New agent-conversation hooks (`beforeSubmitPrompt`, `afterAgentResponse`, `afterAgentThought`, `stop`, `subagentStart`) (`3.11`) — *incremental improvement* — extends the existing Hooks primitive to conversation-level events
- MCPs and Organization Groups in Team Marketplaces (`3.10`) — *config knob* — admin distribution/access-control layer over the existing Marketplace
- Cursor SDK custom tools (`local.customTools`), permissions-driven auto-review classifier, and nested subagents (`Jun 2026`) — *incremental improvement* — extends the existing SDK primitive
- Bugbot speed/cost/accuracy improvements and `/review-bugbot`, `/review-security` subcommands (`Jun 2026`) — *incremental improvement* — performance and workflow refinements to the existing Bugbot/Security Review flow
- Customize Cursor page (`3.9`) — *UI polish* — unified settings page; individual primitives already tracked separately
- Canvas Design Mode multi-select & voice input (`3.7`) — *incremental improvement* — enhancement to existing Canvas and voice features
- Shared Canvases & `/loop` skill (`3.5`) — *convenience wrapper* — Canvas sharing and loop execution are wrappers on existing agent and canvas capabilities
- Canvases (interactive agent artifacts) (`Apr 2026`) — *incremental improvement* — canvas artifact output is a UI enhancement to the existing agent output surface
- Bugbot Effort Levels (`May 2026`) — *config knob* — tunes existing Bugbot review depth
- Bugbot Learned Rules & MCP Support (`Apr 2026`) — *incremental improvement* — improves existing Bugbot via feedback signals and additional context
- Full-screen Tabs and Compact Chats / Tiled Layout (`3.4`, `3.1`) — *UI polish* — layout variants for existing Agents Window
- Agent output verbosity levels: Compact, Balanced, Detailed (`3.4`) — *config knob* — tunes existing Agents Window output display
- Composer 2.5 model (`May 2026`) — *incremental improvement* — new version of existing Cursor-trained model
- Composer 2 model (`Mar 2026`) — *incremental improvement* — new version of existing Cursor-trained model
- Model releases (GPT-4.1, o3, o4-mini, Grok 3, Gemini 2.5, Claude 3.7, DeepSeek R1, Grok 4.5, etc.) — tracked separately
- Auto-review Run Mode (`3.6`) — *config knob* — tunes agent approval prompt frequency
- Build in Parallel (`3.3`) — *convenience wrapper* — wrapper over existing async subagent parallel execution
- Context Usage Breakdown in editor (`3.3`) — *UI polish* — surfacing of existing token data in a new view
- Team Marketplace (admin plugin distribution controls) (`May 2026`) — *config knob* — governance knob over existing Marketplace
- New Plugins on Cursor Marketplace (`Mar 2026`) — *incremental improvement* — content addition to existing Marketplace infrastructure
- CLI `/btw`, `/config`, `/statusline` commands (`Apr 2026`) — *convenience wrapper* — shortcuts to existing capabilities
- Tiled Layout and upgraded Voice Input (`3.1`) — *UI polish*
- Auto-model selection (`0.47`) — *config knob* — routing knob over existing model selection
- Sound notifications for chat completion (`0.48`) — *UI polish*
- `.cursorignore` file for indexing exclusion (`0.46`) — *config knob*
- Chat export to Markdown (`0.50`) — *format/scripting flag*
- Cursor Tab partial accepts (`0.34`) — *incremental improvement*
- Cursor Tab multi-file suggestions (`0.50`) — *incremental improvement*
- Instant Grep across all models (`2.1`) — *incremental improvement*
- Layout customization (four layouts + keyboard shortcuts) (`2.3`) — *UI polish*
- Pinned Chats (`2.2`) — *UI polish*
- PR summaries from Bugbot (`1.7`) — *convenience wrapper*
- Cursor Blame / AI attribution tracking (Enterprise) (`2.4`) — *config knob* — governance feature; falls inside existing Enterprise section
- Global MCP config `~/.cursor/mcp.json` (`0.47`) — *config knob*
- Process separation for extensions (`2.3`) — *security infrastructure*
- `.cursorrules` flat-file support (`0.32`) — *config knob* — precursor to the `.cursor/rules` directory; superseded
- AI Linter (scan on save) (`0.27`) — *convenience wrapper* — built on existing lint-error context
- Interpreter Mode Beta (`0.17`) — *preview→GA, nothing new* — superseded by Agent terminal and sandboxed terminal
- Copilot++ / Tab ghost-text autocomplete launch (`0.15`) — *incremental improvement* — initial release of Tab as ghost text; core Tab feature
