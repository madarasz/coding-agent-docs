# GitHub Copilot Features (Aug 2024 – Jul 2026)

Significant user-facing features added to GitHub Copilot since its public availability.
**Last updated:** Jul 26, 2026 · Source: [GitHub Copilot Changelog](https://github.blog/changelog/label/copilot/)

## Agentic & Multi-Agent

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Agent finder for GitHub Copilot](https://github.blog/changelog/2026-06-17-agent-finder-for-github-copilot-now-available) | Automatically discovers and ranks the most relevant AI tools and skills for a given task from available catalogs, loading them on demand | Copilot Chat / agent sessions | N/A | Jun 2026 |
| [Prompt scheduling in Copilot CLI](https://github.blog/changelog/2026-06-02-copilot-cli-improved-ui-rubber-duck-prompt-scheduling-and-voice-input) | `/every` and `/after` slash commands schedule prompts to run repeatedly or after a delay within the current CLI session | `/every <interval> <prompt>` / `/after <delay> <prompt>` | N/A | Jun 2026 |
| [Schedule and automate tasks with Copilot cloud agent](https://github.blog/changelog/2026-06-02-schedule-and-automate-tasks-with-copilot-cloud-agent) | Cloud agent can run automatically on a schedule or in response to repository events, automating tasks like issue triage, test fixes, and release note generation | Agent automation settings on github.com | N/A | Jun 2026 |
| [/chronicle session insights](https://github.blog/changelog/2026-06-02-gain-insights-across-your-agent-sessions-with-chronicle) | Synthesizes agent session history into standup summaries, personalized tips, and custom instructions across GitHub, VS Code, JetBrains, and other surfaces | `/chronicle` in Copilot CLI | N/A | Jun 2026 |
| [Copilot Chat agent session queries](https://github.blog/changelog/2026-06-10-copilot-chat-now-sees-your-agent-sessions) | Copilot Chat can search and query past cloud agent sessions and logs, enabling contextual follow-up questions and seamless session handoffs | Copilot Chat on github.com | N/A | Jun 2026 |
| [GitHub Agentic Workflows](https://github.blog/changelog/2026-06-11-github-agentic-workflows-is-now-in-public-preview) (public preview Jun 2026) | Framework enabling Copilot to execute reasoning-based automated tasks like issue triage and CI failure analysis inside GitHub Actions using natural-language Markdown definitions; first shipped as technical preview Feb 2026, public preview Jun 2026 | Agentic workflow YAML / Markdown definitions | N/A | Feb 2026 |
| [Agents tab in repository](https://github.blog/changelog/2026-01-26-introducing-the-agents-tab-in-your-repository) | New dedicated repository section for managing and monitoring all Copilot coding agent activity | Repository navigation bar | N/A | Jan 2026 |
| [Isolated Subagents for JetBrains, Eclipse, and Xcode](https://github.blog/changelog/2025-11-18-isolated-subagents-for-jetbrains-eclipse-and-xcode-now-in-public-preview) (public preview) | Compartmentalized sub-agent operations run in isolated contexts enabling safer parallel execution | IDE agent settings | N/A | Nov 2025 |
| [Mission control for coding agent](https://github.blog/changelog/2025-10-28-a-mission-control-to-assign-steer-and-track-copilot-coding-agent-tasks) | Unified dashboard on GitHub for assigning, steering, and tracking all active coding agent tasks | github.com/agents | N/A | Oct 2025 |
| [Copilot coding agent](https://github.blog/changelog/2025-09-25-copilot-coding-agent-is-now-generally-available) (GA Sep 2025) | Autonomous AI agent that creates branches, writes code, runs tests, and opens pull requests when assigned a GitHub issue; first shipped as public preview, GA Sep 2025, extended to Copilot Business | Issue assignment / `@copilot` mention | N/A | May 2025 |
| [Agents panel on github.com](https://github.blog/changelog/2025-08-19-agents-panel-launch-copilot-coding-agent-tasks-anywhere-on-github-com) | Universal task launcher for starting coding agent assignments from any page on github.com | github.com UI (agents button) | N/A | Aug 2025 |

## Context & Memory

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Semantic issue search in Copilot Chat](https://github.blog/changelog/2026-05-20-semantic-issue-search-in-copilot-chat) | Copilot Chat searches GitHub issues using natural language and surfaces contextually relevant results | Copilot Chat on github.com | N/A | May 2026 |
| [Cross-repository and cross-org code search for Copilot agents](https://github.blog/changelog/2026-05-06-github-copilot-in-visual-studio-code-april-releases/) | Copilot agents can semantically search any workspace and run grep-style queries across other GitHub repositories and organizations using the built-in `githubTextSearch` tool | Automatic (agent tool call in VS Code) | N/A | May 2026 |
| [Agentic memory](https://github.blog/changelog/2026-01-15-agentic-memory-for-github-copilot-is-in-public-preview) (public preview) | Coding agent retains context and information persistently across separate sessions | Automatic when memory is enabled | N/A | Jan 2026 |
| [Copilot Memory](https://github.blog/changelog/2025-12-19-copilot-memory-early-access-for-pro-and-pro) | Copilot learns and persists user preferences and working context across chat sessions; on by default for Pro+ (Mar 2026), extended to Business and Enterprise (Jun 2026), with deletion/scope controls and Copilot CLI support | Settings → Copilot → Memory | N/A | Dec 2025 |
| [AGENTS.md support](https://github.blog/changelog/2025-08-28-copilot-coding-agent-now-supports-agents-md-custom-instructions) | Coding agent reads per-repo `AGENTS.md` to apply custom behavior directives and tool configurations | `AGENTS.md` file in repository root | N/A | Aug 2025 |
| [copilot-instructions.md](https://github.blog/changelog/2025-08-06-copilot-code-review-copilot-instruction-md-support-is-now-generally-available) (GA) | Per-repository instruction file that shapes all Copilot responses and behavior for that codebase | `.github/copilot-instructions.md` | N/A | Aug 2025 |
| [Copilot Spaces](https://github.blog/changelog/2025-09-24-copilot-spaces-is-now-generally-available) (GA Sep 2025) | Persistent collaborative workspaces that bundle repositories, files, and conversation context for ongoing projects; extended to issues and PRs (Jun 2025), GA Sep 2025 | github.com/spaces | N/A | May 2025 |
| [Organization custom instructions](https://github.blog/changelog/2025-04-17-organization-custom-instructions-now-available) | Teams define org-wide instructions shaping Copilot behavior for all organization members | Org Settings → Copilot → Instructions | N/A | Apr 2025 |
| [Semantic code search indexing](https://github.blog/changelog/2025-03-12-instant-semantic-code-search-indexing-now-generally-available-for-github-copilot) (GA) | Copilot can semantically search the entire repository codebase for accurate cross-file context retrieval | Automatic (built into Copilot Chat) | N/A | Mar 2025 |
| [Personal custom instructions](https://github.blog/changelog/2025-03-06-personal-custom-instructions-for-copilot-are-now-generally-available-on-github-com) (GA) | Users define standing instructions that Copilot applies across all conversations on github.com | github.com Settings → Copilot → Instructions | N/A | Mar 2025 |
| [Custom repository instructions](https://github.blog/changelog/2025-01-21-custom-repository-instructions-are-now-available-for-copilot-on-github-com-public-preview) (public preview) | Per-repository guidance in GitHub settings controls how Copilot behaves within that codebase | github.com repository settings | N/A | Jan 2025 |

## Model & Input

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Larger context windows and configurable reasoning levels](https://github.blog/changelog/2026-06-04-larger-context-windows-and-configurable-reasoning-levels-for-github-copilot) | One-million-token context window and adjustable reasoning depth let developers balance analytical depth against speed for complex tasks | Model/reasoning settings in VS Code, Copilot CLI, Copilot app | N/A | Jun 2026 |
| [Voice input in Copilot CLI](https://github.blog/changelog/2026-06-02-copilot-cli-improved-ui-rubber-duck-prompt-scheduling-and-voice-input) | Hands-free voice dictation lets users hold the space bar to record prompts with local processing, adding a new input modality to Copilot CLI | Hold space bar in Copilot CLI | N/A | Jun 2026 |
| [Copilot CLI BYOK and local model support](https://github.blog/changelog/2026-04-07-copilot-cli-now-supports-byok-and-local-models) | Copilot CLI accepts a user-supplied API key and routes requests to locally hosted models | `copilot --byok` / local model config | N/A | Apr 2026 |
| [Browser tools for GitHub Copilot in VS Code](https://github.blog/changelog/2026-07-01-browser-tools-for-github-copilot-in-vs-code-are-generally-available/) (GA Jul 2026) | Copilot agents open, navigate, click, type, and screenshot live web pages in an isolated, opt-in browser tab to validate web apps end-to-end; public preview Apr 2026, GA Jul 2026 | VS Code → Copilot Chat → Share tab with agent | N/A | Apr 2026 |
| [Image support in agent sessions](https://github.blog/changelog/2026-03-05-add-images-to-agent-sessions) | Coding agent accepts screenshots and diagram images as context within task instructions | Image attachment in agent session | N/A | Mar 2026 |
| [Auto model selection](https://github.blog/changelog/2025-12-10-auto-model-selection-is-generally-available-in-github-copilot-in-visual-studio-code) (GA in VS Code) | Copilot automatically selects the optimal AI model for each task without requiring user configuration | Automatic in VS Code (enabled by default) | N/A | Dec 2025 |
| [Copilot SWE-model](https://github.blog/changelog/2025-09-22-copilot-swe-model-rolling-out-to-visual-studio-code-insiders) | Specialized software-engineering model with enhanced multi-file reasoning deployed as a coding agent backend | VS Code Insiders model selector | N/A | Sep 2025 |
| [Coding agent web browser](https://github.blog/changelog/2025-07-02-copilot-coding-agent-now-has-its-own-web-browser) | Coding agent can browse the internet to research APIs and documentation during task execution | Automatic during agent sessions | N/A | Jul 2025 |
| [Vision input in Copilot Chat](https://github.blog/changelog/2026-07-01-copilot-vision-is-generally-available/) (GA Jul 2026) | Copilot Chat accepts image and PDF uploads enabling screenshot-based debugging and visual context questions; public preview Apr 2025, GA Jul 2026 | Image/PDF attachment in Copilot Chat | N/A | Apr 2025 |
| [Web search in Copilot Chat](https://github.blog/changelog/2024-10-29-web-search-in-github-copilot-chat-now-available-for-copilot-individual) | Copilot Chat can search the web to augment answers with up-to-date documentation beyond training data; available in VS Code (Oct 2024) and on github.com (Feb 2025) | Copilot Chat web-search toggle | N/A | Oct 2024 |
| [Custom models for GitHub Copilot](https://github.blog/changelog/2024-08-27-custom-models-for-github-copilot-are-now-in-limited-public-beta) (limited beta) | Organizations fine-tune Copilot on private codebases to improve code suggestion relevance for their stack | Enterprise admin → Custom models | N/A | Aug 2024 |

## Built-in Workflows

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Copilot merge conflict resolution in GitHub Desktop](https://github.blog/changelog/2026-06-26-github-desktop-3-6-worktrees-and-deeper-copilot-integration/) | GitHub Desktop uses Copilot, running on the Copilot SDK, to detect and automatically resolve Git merge conflicts | GitHub Desktop → Resolve with Copilot | N/A | Jun 2026 |
| [Dedicated security review command in Copilot CLI](https://github.blog/changelog/2026-06-10-dedicated-security-review-command-now-available-in-copilot-cli) | Analyzes local code changes for high-confidence security vulnerabilities across 11 categories before committing, without requiring separate code scanning tools | `/security-review` in Copilot CLI | N/A | Jun 2026 |
| [Plan agent in Visual Studio](https://github.blog/changelog/2026-06-04-github-copilot-in-visual-studio-may-update) | Copilot collaborates on an implementation plan in Visual Studio before writing any code, allowing users to review and refine the approach upfront | Visual Studio → Copilot → Plan agent | N/A | Jun 2026 |
| [Copilot code review for Azure Repos](https://github.blog/changelog/2026-06-02-github-copilot-code-review-for-azure-repos-is-now-in-technical-preview) (technical preview) | AI-powered pull request review with inline code comments now available within Azure DevOps workflows | Azure Repos PR → Request Copilot review | N/A | Jun 2026 |
| [One-click fixes for failing Actions with Copilot cloud agent](https://github.blog/changelog/2026-05-18-one-click-fixes-for-failing-actions-with-copilot-cloud-agent) | Cloud agent diagnoses and proposes code fixes for failing GitHub Actions workflow runs | Actions UI / Copilot cloud agent | N/A | May 2026 |
| [Plan mode in JetBrains, Eclipse, and Xcode](https://github.blog/changelog/2025-11-18-plan-mode-in-github-copilot-now-in-public-preview-in-jetbrains-eclipse-and-xcode) (public preview) | Copilot presents and awaits approval of its implementation plan before writing any code | IDE agent panel / plan mode toggle | N/A | Nov 2025 |
| [Copilot app modernization for Java and .NET](https://github.blog/changelog/2025-09-23-github-copilot-app-modernization-is-now-generally-available-for-java-and-net) (GA) | Copilot analyzes and autonomously modernizes legacy Java and .NET codebases through agentic refactoring workflows | Copilot modernization panel | N/A | Sep 2025 |
| [GitHub Spark](https://github.blog/changelog/2025-07-23-github-spark-in-public-preview-for-copilot-pro-subscribers) (public preview) | No-code AI app builder that generates functional web applications with data and logic from natural language prompts | github.com/spark | N/A | Jul 2025 |
| [GitHub Desktop commit message generation](https://github.blog/changelog/2025-06-24-github-desktop-3-5-github-copilot-commit-message-generation-now-generally-available) (GA) | AI-generated commit message suggestions in GitHub Desktop | GitHub Desktop (commit message field) | N/A | Jun 2025 |
| [Copilot code review](https://github.blog/changelog/2025-04-04-copilot-code-review-now-generally-available) (GA Apr 2025) | AI-powered code review that automatically reviews pull requests and provides actionable inline feedback; migrated to an agentic multi-file backend (Mar 2026) | Auto-trigger on PRs / manual review button | N/A | Apr 2025 |
| [Next Edit Suggestions (NES)](https://github.blog/changelog/2025-02-06-next-edit-suggestions-agent-mode-and-prompts-files-for-github-copilot-in-vs-code-january-release-v0-24) (public preview) | Copilot predicts and suggests the next code edit the developer is likely to make based on recent changes | VS Code inline ghost text (NES mode) | N/A | Feb 2025 |
| [Copilot Autofix for CodeQL](https://github.blog/changelog/2024-08-14-copilot-autofix-for-codeql-code-scanning-alerts-is-now-generally-available) (GA) | Copilot automatically generates fix suggestions for CodeQL security alerts on public repos at no extra cost | GitHub Code Scanning / PR security alerts | N/A | Aug 2024 |

## Extensibility

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Agent Apps](https://github.blog/changelog/2026-06-02-extend-github-with-agent-apps) | Third-party AI agents from partners can be installed as standard GitHub Apps and assigned to issues, mentioned in PRs, or invoked through the Agents UI | github.com Agents UI / issue assignment | N/A | Jun 2026 |
| [Agent Skills](https://github.blog/changelog/2025-12-18-github-copilot-now-supports-agent-skills) | Package and reuse custom agent capabilities as shareable skill modules attachable to any Copilot agent | Agent skill configuration / settings UI | N/A | Dec 2025 |
| [Custom agents for GitHub Copilot](https://github.blog/changelog/2025-10-28-custom-agents-for-github-copilot) | Define specialized Copilot agent variants with custom tools, instructions, and behavior profiles | Agent configuration UI on github.com | N/A | Oct 2025 |
| [GitHub MCP Registry](https://github.blog/changelog/2025-09-16-github-mcp-registry-the-fastest-way-to-discover-ai-tools) | Centralized discovery directory for MCP servers enabling one-click installation of community-built tools | github.com/mcp | N/A | Sep 2025 |
| [MCP support GA across IDEs](https://github.blog/changelog/2025-08-14-model-context-protocol-mcp-support-for-jetbrains-eclipse-and-xcode-is-now-generally-available) (VS Code, JetBrains, Eclipse, Xcode) | Model Context Protocol integration enables Copilot agent to invoke external tools and data sources from all major IDEs | Agent mode in IDE + MCP server config | N/A | Aug 2025 |
| [Coding agent remote MCP server support](https://github.blog/changelog/2025-07-09-copilot-coding-agent-now-supports-remote-mcp-servers) | Coding agent can connect to and use external remote MCP servers as tool providers | `mcp` config in agent settings | N/A | Jul 2025 |
| [GitHub MCP Server](https://github.blog/changelog/2025-09-04-remote-github-mcp-server-is-now-generally-available) (GA Sep 2025) | Hosted MCP server exposing GitHub APIs as callable tools for any MCP-compatible AI client; first shipped as public preview (Apr 2025) | `npx @modelcontextprotocol/server-github` | N/A | Apr 2025 |
| [Copilot Extensions with skillsets](https://github.blog/changelog/2024-11-19-build-copilot-extensions-faster-with-skillsets) | Build Copilot extensions using lightweight REST-based skill definitions without writing a full LLM agent | Extension builder (skillset YAML) | N/A | Nov 2024 |
| [GitHub Copilot Extensions](https://github.blog/changelog/2025-02-19-announcing-the-general-availability-of-github-copilot-extensions) (GA Feb 2025) | Third-party extensions framework for integrating external tools and services into Copilot Chat; public beta Sep 2024, GA Feb 2025 | `@ext-name` mention in Copilot Chat | N/A | Sep 2024 |

## Platforms & Environments

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [Copilot CLI in JetBrains IDEs](https://github.blog/changelog/2026-06-02-introducing-copilot-cli-and-agentic-capabilities-enhancements-in-jetbrains-ides) | Copilot CLI integrated into JetBrains IDEs with an agent picker, `/remote`, `/chronicle`, and Cloud Coding Agent access from a unified sessions view | JetBrains Copilot plugin → CLI tab | N/A | Jun 2026 |
| [VS Code Agents window](https://github.blog/changelog/2026-06-03-github-copilot-in-visual-studio-code-may-releases) | Multi-project agent-first workflow hub in VS Code with remote session support and cross-repo task management | VS Code → Copilot → Agents | N/A | Jun 2026 |
| [GitHub Copilot in JetBrains AI Assistant](https://github.blog/changelog/2026-06-30-copilot-agent-is-now-available-in-jetbrains-ai-assistant/) | GitHub Copilot becomes a selectable agent option inside JetBrains' own AI Assistant agent picker, alongside JetBrains' native agent | JetBrains AI Assistant → agent picker → Copilot | N/A | Jun 2026 |
| [GitHub Copilot app](https://github.blog/changelog/2026-06-17-github-copilot-app-generally-available) (GA Jun 2026) | Standalone Copilot desktop application for agent-driven development with parallel sessions, scheduled automations, MCP server support, and collaborative canvases; technical preview May 2026, GA Jun 2026 | Technical preview download → GA | N/A | May 2026 |
| [GitHub Copilot for Eclipse open source](https://github.blog/changelog/2026-05-21-github-copilot-for-eclipse-is-open-source) | Eclipse IDE Copilot plugin released as open-source software enabling community contributions and forks | Eclipse Marketplace / GitHub repo | N/A | May 2026 |
| [Start Copilot cloud agent via REST API](https://github.blog/changelog/2026-05-13-start-copilot-cloud-agent-tasks-via-the-rest-api) | Programmatic task initiation for cloud agent via the GitHub REST API | `POST /repos/{owner}/{repo}/copilot/tasks` | N/A | May 2026 |
| [Remote control for Copilot CLI sessions](https://github.blog/changelog/2026-05-18-remote-control-for-copilot-cli-sessions-now-generally-available-on-mobile-web-and-vs-code) (GA) | Control active Copilot CLI sessions from GitHub Mobile, github.com, and VS Code instead of the originating terminal | GitHub Mobile / github.com / VS Code | N/A | May 2026 |
| [View and manage agent sessions from issues and projects](https://github.blog/changelog/2026-04-23-view-and-manage-agent-sessions-from-issues-and-projects) | Agent session activity is surfaced and controllable directly within GitHub issues and project boards | Issues/Projects sidebar | N/A | Apr 2026 |
| [Copilot SDK](https://github.blog/changelog/2026-06-02-copilot-sdk-is-now-generally-available) (GA Jun 2026) | Developer SDK for building integrations and tools that extend and automate Copilot capabilities; six languages including Rust and Java, stable API surface; public preview Apr 2026, GA Jun 2026 | `npm install @github/copilot-sdk` | N/A | Apr 2026 |
| [Copilot coding agent for Jira](https://github.blog/changelog/2026-06-25-github-copilot-for-jira-is-now-generally-available/) (GA Jun 2026) | Coding agent receives and implements Jira work items and delivers completed code changes to GitHub, with model selection, Confluence context via MCP, and custom agents; public preview Mar 2026, GA Jun 2026 | Jira GitHub integration | N/A | Mar 2026 |
| [Copilot in Zed editor](https://github.blog/changelog/2026-02-19-github-copilot-support-in-zed-generally-available) (GA) | Copilot code completion and chat in the Zed open-source editor reaches general availability | Zed settings → Extensions → Copilot | N/A | Feb 2026 |
| [GitHub Mobile Live Notifications](https://github.blog/changelog/2026-02-26-github-mobile-track-coding-agent-progress-in-real-time-with-live-notifications) | Real-time push notifications for coding agent task progress and completion on iOS and Android | GitHub Mobile app | N/A | Feb 2026 |
| [GitHub Copilot supports OpenCode](https://github.blog/changelog/2026-01-16-github-copilot-now-supports-opencode) | Copilot integration available in the OpenCode terminal-based AI coding assistant | `opencode` CLI | N/A | Jan 2026 |
| [Eclipse coding agent](https://github.blog/changelog/2025-11-18-github-copilot-coding-agent-for-eclipse-now-in-public-preview) (public preview) | Full Copilot coding agent support for Eclipse IDE with autonomous code writing and PR creation | Eclipse IDE agent panel | N/A | Nov 2025 |
| [Copilot coding agent in Slack](https://github.blog/changelog/2025-10-28-work-with-copilot-coding-agent-in-slack) | Assign and track coding agent tasks directly from Slack without leaving the messaging app | Slack GitHub app / @github mention | N/A | Oct 2025 |
| [GitHub Copilot for Linear](https://github.blog/changelog/2025-10-28-github-copilot-for-linear-available-in-public-preview) (public preview) | Coding agent receives and implements work items from the Linear issue tracker | Linear GitHub integration | N/A | Oct 2025 |
| [Copilot coding agent in Microsoft Teams](https://github.blog/changelog/2025-09-19-work-with-copilot-coding-agent-in-microsoft-teams) | Assign and track coding agent tasks from Microsoft Teams without visiting github.com | Teams GitHub app | N/A | Sep 2025 |
| [Assign Azure Boards work items to coding agent](https://github.blog/changelog/2025-09-18-assign-azure-boards-work-items-to-copilot-coding-agent-in-public-preview) | Coding agent accepts Azure DevOps work items and delivers code changes to GitHub | Azure Boards GitHub integration | N/A | Sep 2025 |
| [Start and track coding agent from GitHub CLI](https://github.blog/changelog/2025-09-26-kick-off-and-track-copilot-coding-agent-sessions-from-the-github-cli) | Initiate and monitor coding agent sessions via `gh copilot` command-line interface | `gh copilot agent` | N/A | Sep 2025 |
| [Start and track coding agent from GitHub Mobile](https://github.blog/changelog/2025-09-24-start-and-track-copilot-coding-agent-tasks-in-github-mobile) | Launch and monitor coding agent tasks from the GitHub iOS and Android app | GitHub Mobile app | N/A | Sep 2025 |
| [GitHub Copilot CLI](https://github.blog/changelog/2026-02-25-github-copilot-cli-is-now-generally-available) (GA Feb 2026) | Command-line Copilot assistant for shell command explanation, suggestion, and fix; public preview Sep 2025, GA Feb 2026 | `gh copilot` | N/A | Sep 2025 |
| [Agent mode in JetBrains, Eclipse, and Xcode](https://github.blog/changelog/2025-07-16-agent-mode-for-jetbrains-eclipse-and-xcode-is-now-generally-available) (GA) | Copilot multi-step agentic editing mode reaches general availability in JetBrains IDEs, Eclipse, and Xcode | IDE Copilot panel → Agent mode | N/A | Jul 2025 |
| [Agent mode in Visual Studio with MCP](https://github.blog/changelog/2025-06-17-visual-studio-17-14-june-release) (GA) | Copilot agent mode with Model Context Protocol tool support reaches general availability in Visual Studio | Visual Studio → Copilot agent mode | N/A | Jun 2025 |
| [GitHub Copilot for Eclipse](https://github.blog/changelog/2025-04-16-github-copilot-chat-for-eclipse-is-now-generally-available) (GA) | Copilot code completion (Mar 2025) and Chat (Apr 2025) for Eclipse IDE reach general availability | Eclipse Copilot plugin | N/A | Apr 2025 |
| [Copilot Language Server SDK](https://github.blog/changelog/2025-02-10-copilot-language-server-sdk-is-now-available) | Developer toolkit for building IDE integrations and editor plugins that embed Copilot capabilities | NPM package (Language Server SDK) | N/A | Feb 2025 |
| [Xcode code completion](https://github.blog/changelog/2025-02-14-code-completion-in-github-copilot-for-xcode-is-now-generally-available) (GA) | GitHub Copilot code completion for Xcode IDE reaches general availability | Xcode Copilot extension | N/A | Feb 2025 |
| [Copilot free for mobile and CLI](https://github.blog/changelog/2025-02-12-github-copilot-chat-and-github-copilot-extension-now-available-for-free-on-github-mobile-and-github-cli) | GitHub Mobile and CLI access extended to Copilot Free tier users | GitHub Mobile app / `gh copilot` (free) | N/A | Feb 2025 |
| [GitHub Copilot Free tier](https://github.blog/changelog/2024-12-18-announcing-github-copilot-free) | Free-of-charge tier giving all GitHub users access to AI code completions and chat with monthly limits | github.com → Sign up for Copilot | N/A | Dec 2024 |
| [GitHub Copilot for Windows Terminal](https://github.blog/changelog/2024-10-29-github-copilot-is-now-available-in-windows-terminal) | Copilot Chat integration in Windows Terminal for command explanation and shell assistance | Windows Terminal settings | N/A | Oct 2024 |

## Security & Governance

| Title | Description | Invocation | Version | Date |
|-------|-------------|------------|---------|------|
| [MCP server trust validation in Visual Studio](https://github.blog/changelog/2026-07-14-github-copilot-in-visual-studio-june-update/) | Visual Studio compares each MCP server's configuration and tool/prompt fingerprint against a trusted baseline at startup and shows a trust dialog when it changes | Visual Studio → Tools → Options → Copilot → Show trust dialog | N/A | Jul 2026 |
| [Deploy managed Copilot settings via MDM in VS Code and CLI](https://github.blog/changelog/2026-07-08-deploy-managed-copilot-settings-via-mdm-in-vs-code-and-cli/) | Enterprise admins push Copilot settings to VS Code and Copilot CLI through native device management (Windows registry, macOS managed preferences) or a file-based `managed-settings.json`, independent of GitHub sign-in | Windows/macOS MDM policy or `managed-settings.json` file | N/A | Jul 2026 |
| [Copilot agent session streaming](https://github.blog/changelog/2026-07-02-copilot-agent-session-streaming-is-now-in-public-preview/) (public preview) | Enterprise owners stream or retrieve Copilot agent session records—prompts, responses, and tool calls—across CLI, IDEs, and cloud agents via a streaming endpoint, REST API, or Microsoft Purview | Enterprise Settings → Copilot → Session streaming | N/A | Jul 2026 |
| [GitHub Copilot app BYOK](https://github.blog/changelog/2026-06-23-github-copilot-app-support-for-byok) | Copilot app users can supply their own API keys to route agent sessions through OpenAI, Azure OpenAI, Anthropic, Ollama, or LM Studio instead of GitHub's hosted models | Copilot app → Model settings → BYOK | N/A | Jun 2026 |
| [Cloud and local sandboxes for GitHub Copilot](https://github.blog/changelog/2026-06-02-cloud-and-local-sandboxes-for-github-copilot-now-in-public-preview) (public preview) | Copilot can run inside secure, isolated sandboxes both locally and in cloud-hosted infrastructure with controlled filesystem, network, and system access | Copilot sandbox settings | N/A | Jun 2026 |
| [Security validation for third-party coding agents](https://github.blog/changelog/2026-06-09-security-validation-for-third-party-coding-agents) | CodeQL scanning, dependency advisory checks, and secret detection are automatically applied to code generated by third-party AI coding agents (Claude, OpenAI Codex, etc.) | Automatic in repositories with code scanning enabled | N/A | Jun 2026 |
| [Enterprise bypass permission controls](https://github.blog/changelog/2026-06-17-enterprise-managed-settings-now-support-bypass-permission-controls) | Enterprise admins can enforce `disableBypassPermissionsMode` to require explicit user approval for all Copilot CLI and VS Code commands, preventing automatic permission skipping | Enterprise managed settings | N/A | Jun 2026 |
| [Enterprise managed-settings.json](https://github.blog/changelog/2026-07-01-enterprise-managed-settings-json-is-generally-available/) (GA Jul 2026) | Enterprise admins define AI governance standards, extensibility flows, and curated plugin packages for Copilot CLI and VS Code via a `managed-settings.json` file in a `.github-private` repo; public preview May 2026 (plugins only), GA Jul 2026 (full settings scope) | `.github-private/.github/copilot/settings.json` | N/A | May 2026 |
| [Target Copilot models to organizations with model rules](https://github.blog/changelog/2026-05-26-target-copilot-models-to-organizations-with-model-rules) | Admins create rules directing specific AI models to designated teams or organizations | Org Settings → Copilot → Model rules | N/A | May 2026 |
| [Data residency (US + EU) and FedRAMP-authorized models](https://github.blog/changelog/2026-04-13-copilot-data-residency-in-us-eu-and-fedramp-compliance-now-available) | Enterprise deployments pin data residency to US or EU regions and access FedRAMP-authorized model variants | Enterprise Settings → Compliance | N/A | Apr 2026 |
| [Enterprise AI controls and agent control plane](https://github.blog/changelog/2026-02-26-enterprise-ai-controls-agent-control-plane-now-generally-available) (GA) | Enterprise-wide policy framework and control plane for governing all Copilot AI and agent activity | Enterprise admin console | N/A | Feb 2026 |
| [Budget tracking for GitHub AI tools](https://github.blog/changelog/2025-11-03-control-ai-spending-with-budget-tracking-for-github-ai-tools) | Organizations set and monitor spending budgets across all Copilot AI features and premium requests | Org Settings → Billing → AI budget | N/A | Nov 2025 |
| [Enterprise bring your own key (BYOK)](https://github.blog/changelog/2025-11-20-enterprise-bring-your-own-key-byok-for-github-copilot-is-now-in-public-preview) (public preview) | Organizations supply their own encryption keys to independently manage Copilot data security | Enterprise Settings → Encryption keys | N/A | Nov 2025 |
| [Delegate AI controls management](https://github.blog/changelog/2025-11-03-delegate-ai-controls-management-to-members-of-your-enterprise) | Enterprise admins delegate Copilot policy management rights to designated organization members | Enterprise Settings → AI controls | N/A | Nov 2025 |
| [MCP registry and allowlist controls](https://github.blog/changelog/2025-11-18-internal-mcp-registry-and-allowlist-controls-for-vs-code-stable-in-public-preview) (public preview) | Admins define allowed MCP server registries and block unauthorized servers for all IDE users | IDE settings → MCP allowlist | N/A | Nov 2025 |
| [Copilot content exclusion](https://github.blog/changelog/2024-11-12-content-exclusion-ga) (GA in IDEs) | Admins exclude specific files, folders, or repositories from Copilot code suggestions organization-wide | Org/Enterprise admin → Content exclusion | N/A | Nov 2024 |
| [Security campaigns with Copilot Autofix](https://github.blog/changelog/2024-10-29-security-campaigns-with-copilot-autofix-are-now-in-public-preview) | Enterprise campaigns batch and automatically fix code scanning alerts at scale across repositories | GitHub Advanced Security → Security campaigns | N/A | Oct 2024 |

## Other Improvements

Notable changes that fell below the threshold for the main tables:

- Model releases (GPT-5.x, GPT-5.6, GPT-4.1, Claude Opus/Sonnet/Fable 4.x–5.x, Gemini 3 Pro/Flash, Gemini 2.5 Pro, Grok Code Fast 1, Raptor mini, MAI-Code-1-Flash, Kimi K2.7 Code) (`N/A`) - *individual model releases; tracked separately*
- Repository-level Copilot usage metrics GA via REST API (`N/A`) - *metrics API addition*
- C++ modernization agent GA in Visual Studio (`N/A`) - *platform expansion* of existing app modernization workflow
- Real-time Copilot usage tracking and proactive limit alerts in Visual Studio (`N/A`) - *incremental improvement*
- Long-distance Next Edit Suggestions in Visual Studio (`N/A`) - *incremental improvement*
- GitHub Copilot app available to all Copilot plans (`N/A`) - *platform expansion*
- Improved accuracy and coverage in Copilot usage metrics reports (`N/A`) - *incremental improvement*
- Copilot CLI auto model selection routes by task (`N/A`) - *platform expansion* of existing auto model selection feature
- Enterprise-managed settings support `strictKnownMarketplaces` (`N/A`) - *config knob*
- Copilot CLI: New terminal interface GA (`N/A`) - *UI polish / incremental improvement*
- Auto mode in Copilot Chat for all users (`N/A`) - *incremental improvement* (GA rollout of existing auto model selection)
- Agentic workflows no longer need a personal access token (`N/A`) - *incremental improvement*
- Copilot Memory for Business and Enterprise (`N/A`) - *platform expansion* of existing memory feature
- Agent tasks REST API for Copilot Pro/Pro+/Max (`N/A`) - *platform expansion* of existing enterprise-only cloud agent REST API
- Enterprise-managed plugins in VS Code (`N/A`) - *platform expansion* of May 2026 Copilot CLI feature
- Copilot CLI BYOK enterprise models (`N/A`) - *platform expansion* of existing BYOK capability
- Fix with Copilot for failing Actions in Pro/Pro+/Max (`N/A`) - *platform expansion* of existing cloud agent fix feature
- Copilot code review: AGENTS.md support and UI improvements (`N/A`) - *config knob / incremental improvement*
- Copilot code review: New configurations and controls (`N/A`) - *config knob*
- Shape Copilot code review around your team (`N/A`) - *config knob*
- Copilot Chat brings richer context to pull requests (`N/A`) - *incremental improvement*
- Copilot-authored PRs now included in author searches (`N/A`) - *incremental improvement*
- Generated release notes credit Copilot pull requests (`N/A`) - *incremental improvement*
- New features and Claude as agent provider in JetBrains IDEs (`N/A`) - *incremental improvement*
- Changes to model selection for Free and Student plans (`N/A`) - *config knob*
- Evaluation models in auto for individual plans (`N/A`) - *incremental improvement*
- GitHub Copilot in Eclipse: BYOK, skills, and chat updates (`N/A`) - *platform expansion*
- AI credits consumed per user in Copilot usage metrics API (`N/A`) - *incremental improvement*
- Copilot usage metrics GA (`N/A`) - *metrics/analytics feature; no new coding workflow*
- Team-level Copilot usage metrics via API (`N/A`) - *metrics API addition*
- Copilot code review in JetBrains and Visual Studio (`N/A`) - *platform expansion of existing code review feature*
- Auto model selection GA in JetBrains IDEs (`N/A`) - *platform expansion of existing auto-selection feature*
- Copilot-generated commit messages on github.com GA (`N/A`) - *convenience wrapper for existing desktop/VS Code capability*
- Copilot coding agent PR grouping (`N/A`) - *incremental improvement to existing agent PR behavior*
- Configure internet access for coding agent (`N/A`) - *config knob for existing agent web-browsing feature*
- GitHub Copilot Pro+ tier announcement (`N/A`) - *pricing tier change, not a new capability class*
- Copilot code review path-scoped custom instructions (`N/A`) - *config knob for existing code review feature*
- JetBrains Copilot support for Free plan GA (`N/A`) - *platform expansion; access tier expansion, not a capability class*
- Copilot CLI no longer needs a personal access token in GitHub Actions (`N/A`) - *convenience wrapper*
- BYOK for GitHub Copilot in VS Code extended to air-gapped environments (`N/A`) - *platform expansion*
- BYOK for GitHub Copilot in JetBrains expanded (`N/A`) - *platform expansion*
- Security review command (`/security-review`) extended to the GitHub Copilot app (`N/A`) - *platform expansion*
- Usage-based billing rolled out to all Copilot plans, with user-level spending budgets (`N/A`) - *billing model change, not a new capability class*
- Copilot code review: grouped suggestions and severity labels (`N/A`) - *incremental improvement*
- Copilot code review comment types added to usage metrics API (`N/A`) - *incremental improvement*
- MCP OAuth credential management in VS Code (preregistered client IDs, secret storage) (`N/A`) - *config knob*
- Cost visibility for delegated subagent work in VS Code (`N/A`) - *incremental improvement*
- Marketplace model discovery unified into a single picker in VS Code (`N/A`) - *convenience wrapper*
- New Copilot usage metrics impact dashboard for admins (`N/A`) - *incremental improvement*
- Copilot CLI: new sandbox flags and repository-level settings (`N/A`) - *config knob*
- Built-in debugger skill for Copilot CLI sessions (`N/A`) - *incremental improvement*
- Attach Git commits as context in Copilot Chat in Visual Studio (`N/A`) - *convenience wrapper*
- Skills panel in Visual Studio Copilot chat for browsing workspace agent skills (`N/A`) - *platform expansion*
