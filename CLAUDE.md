# Coding Assistants Docs — Agent Context

This repo tracks significant user-facing features across popular coding agents. It is not a blog — only workflow-changing additions qualify.

## Covered agents

Claude Code · OpenAI Codex · GitHub Copilot · Cursor · Gemini CLI · Windsurf · OpenCode

## Output files

One Markdown doc per agent in `docs/<assistant>-features.md`. Tables are date-descending within each category. An **Other Improvements** section at the end logs named changes that fell below the table bar (audit trail so re-runs don't re-evaluate them).

## Updating docs

Use the `/update-ca-features` skill (`.claude/skills/update-ca-features/SKILL.md`). It handles changelog fetching, triage, categorisation, and writing the output file. Read the skill before doing any update work — it is the authoritative spec.

## Triage rules (summary — full rules in SKILL.md Step 4)

Three outcomes per changelog entry:
- **A — table row**: adds a capability users could not do before
- **B — Other Improvements bullet**: named real change, below the table bar; one reason phrase from the fixed vocabulary
- **C — drop**: bug fixes, perf, refactors, typos — never recorded

## Seven categories (summary — full rules in SKILL.md Step 5)

Applied in tie-breaker order. Security & Governance is always last in the file.

1. Agentic & Multi-Agent
2. Context & Memory
3. Model & Input
4. Built-in Workflows
5. Extensibility
6. Platforms & Environments
7. Security & Governance

## Key conventions

- Preview→GA of the same feature collapses to one row, dated at first ship, `(GA Mmm YYYY)` noted in title.
- Multiple individual model releases collapse to one Other Improvements bullet.
- Never invent or guess URLs — leave title as plain text if no confirmed URL exists.
- Version column: backtick-wrapped (e.g. `` `2.1.154` ``). Date column: `Mon YYYY`.
