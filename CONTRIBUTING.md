# Contributing to Awesome Claude Code Agents

Thanks for your interest in contributing! This project thrives on community agents built from real-world experience.

## Adding a New Agent

### 1. Create the agent file

Place your agent in `agents/your-agent-name.md`. Use the [template](templates/basic-agent.md) as a starting point.

### 2. Follow the format

Every agent must have:

- **YAML frontmatter** with `name`, `description`, `tools`, and `model`
- **Clear system prompt** with project context, patterns, and constraints
- **Concrete code examples** — not generic advice

### 3. Quality standards

- **Scoped tools.** Don't give `Write, Edit, Bash` to a review-only agent.
- **Under 500 lines.** Anthropic recommends keeping agents concise. If yours is longer, split context into a skill + agent combo.
- **Tested.** Try the agent on a real project before submitting.
- **Opinionated.** Agents that enforce specific patterns outperform generic ones.

### 4. Open a PR

Include in your PR description:

- What stack/framework the agent targets
- What problem it solves
- 2-3 example prompts showing how to use it

## Naming Conventions

- Use kebab-case: `nest-architect.md`, `security-reviewer.md`
- Be specific: `react-query-architect` > `frontend-helper`
- Include the framework if stack-specific: `fastify-architect`, `django-architect`

## What Makes a Great Agent

| ✅ Great | ❌ Weak |
|----------|---------|
| Enforces specific file structure | "Follow best practices" |
| Shows exact code patterns | "Write clean code" |
| Flags violations with severity | "This might be an issue" |
| Scoped to one responsibility | "Handles everything" |
| Includes migration guides | Only covers greenfield |

## Questions?

Open an [issue](https://github.com/pshenok/awesome-claude-code-agents/issues) — happy to help.
