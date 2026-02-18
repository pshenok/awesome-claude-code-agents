# 🤖 Awesome Claude Code Agents

Open-source collection of production-ready subagents for [Claude Code](https://code.claude.com). Drop a `.md` file into your project — get a specialized AI teammate.

## What are Claude Code Subagents?

Subagents are specialized AI assistants that run inside Claude Code with their own **isolated context window**, custom system prompt, and scoped tool access. Instead of explaining your stack every session, you give Claude a permanent expert it can delegate to.

```
You ──→ Claude Code ──→ 🏗️ nest-architect (designs modules, enforces patterns)
                    ──→ 🔒 security-reviewer (audits code for vulnerabilities)
                    ──→ 🧪 test-writer (generates test suites)
```

## Quick Start

**Install a single agent:**

```bash
# Project-level (only this repo)
mkdir -p .claude/agents
cp agents/nest-architect.md .claude/agents/

# Global (all your projects)
mkdir -p ~/.claude/agents
cp agents/nest-architect.md ~/.claude/agents/
```

**Use it:**

```
> /agents                              # see all available agents
> Use nest-architect to add a Product module
> Have the nest-architect review my PR
```

Claude will also auto-delegate when a task matches the agent's description.

## 📦 Available Agents

### Backend & Architecture

| Agent | Stack | Description |
|-------|-------|-------------|
| [nest-architect](agents/nest-architect.md) | NestJS, Prisma, Pino | Clean Architecture enforcer. Knows layers, patterns, entity scaffolding. Includes log4js→Pino migration guide. |

## Agent Anatomy

Every agent is a single Markdown file with YAML frontmatter:

```yaml
---
name: my-agent                    # unique identifier
description: >                    # WHEN Claude should use this agent
  Use when designing new modules,
  reviewing architecture, ...
tools: Read, Glob, Grep           # tool access (scope it down!)
model: sonnet                     # sonnet (fast) or opus (powerful)
---

You are a senior [role]...        # system prompt starts here

## Project Architecture
...

## Your Operating Rules
...
```

### Key Principles

- **One goal per agent.** "Security reviewer", not "universal helper".
- **Scope the tools.** Read-only agents get `Read, Glob, Grep`. Builders get `Write, Edit, Bash`.
- **Be opinionated.** Agents work best when they enforce specific patterns, not generic advice.
- **Include examples.** Show the exact code patterns, file structures, and naming conventions.
- **State weaknesses.** Add `"Be critical, don't be agreeable"` — LLMs default to politeness.

## How to Create Your Own

**Option 1: Let Claude generate it**

```
> /agents → Create New Agent → Generate with Claude
> "Create a security review agent that checks for OWASP Top 10 vulnerabilities"
```

**Option 2: Copy and adapt**

1. Pick an agent from this repo that's closest to your needs
2. Copy it to `.claude/agents/` or `~/.claude/agents/`
3. Edit the system prompt to match your project's stack and conventions

**Option 3: Build from your codebase**

Ask Claude Code to analyze your project and generate an agent:

```
> Analyze this codebase architecture and create a subagent that enforces
> our patterns. Save it to .claude/agents/my-architect.md
```

## Project Structure

```
awesome-claude-code-agents/
├── agents/                  # ready-to-use agent files
│   └── nest-architect.md
├── templates/               # starter templates
│   └── basic-agent.md
├── CONTRIBUTING.md
└── README.md
```

## Contributing

We welcome contributions! To add a new agent:

1. **Fork** this repo
2. Create your agent in `agents/your-agent-name.md`
3. Follow the [agent anatomy](#agent-anatomy) format
4. Include a real-world description of what stack/project it targets
5. Open a **Pull Request** with:
   - What the agent does
   - What stack it's built for
   - Example usage prompts

### Quality Checklist

- [ ] Agent has a clear, specific `description` field
- [ ] Tools are scoped to minimum required access
- [ ] System prompt includes concrete code patterns (not just generic advice)
- [ ] Tested in at least one real project
- [ ] File is under 500 lines (Anthropic recommendation)

## Resources

- [Claude Code Subagents Docs](https://code.claude.com/docs/en/sub-agents) — official documentation
- [Claude Code Agent Teams](https://code.claude.com/docs/en/agent-teams) — multi-agent orchestration
- [Claude Code Best Practices](https://www.anthropic.com/engineering/claude-code-best-practices) — Anthropic's engineering guide

## License

MIT — use these agents however you want, in personal or commercial projects.

---

**Built with Claude Code** ⚡ Contributions are welcome — let's build the best agent library together.
