# Comparing Coding Agents

Tracks the evolving capabilities of the **most popular** coding agents. Only significant workflow changes qualify: new capability classes, integration surfaces, extensibility primitives, and paradigm shifts.

## Capabilities

| Coding Agent | Last Updated |
|-----------|--------------|
| [Claude Code](docs/claude-code-features.md) | 2026.07.26 |
| [Codex](docs/codex-features.md) | 2026.07.26 |
| [GitHub Copilot](docs/copilot-features.md) | 2026.07.26 |
| [Cursor](docs/cursor-features.md) | 2026.07.26 |
| [Gemini CLI](docs/gemini-cli-features.md) | 2026.07.26 |
| [OpenCode](docs/opencode-features.md) | 2026.07.26 |

## Categories

Each feature doc uses these seven categories, in this order:

| Category | What it covers |
|----------|----------------|
| **Agentic & Multi-Agent** | Background agents, parallel task execution, multi-agent coordination, worktree isolation, autonomous goals |
| **Context & Memory** | Persistent memory, project instruction files, session resume/recap, named sessions, auto-compaction |
| **Model & Input** | Multimodal input (image, PDF, voice), web search, thinking/reasoning modes, speed knobs, model selection |
| **Built-in Workflows** | Code review, autofix, app modernization, plan mode, commit-message generation, next-edit suggestions |
| **Extensibility** | Hooks, plugins, MCP, custom agents, skills, slash-command authoring, SDK primitives |
| **Platforms & Environments** | Desktop/mobile apps, IDE integrations, cloud providers, OS support, remote control, CLI modes |
| **Security & Governance** | Sandboxing, permission modes, enterprise/managed settings, BYOK, data residency, content exclusion |

## Comparison

TODO:
- Instruction files, skills, agents, hooks, slash commands — where to put the files, how they are invoked, customization possibilities

## Refreshing Information

Coding agent capabilities are refreshed via the [/update-ca-features](.claude/skills/update-ca-features/SKILL.md) skill.
