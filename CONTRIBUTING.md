# Contributing to Melogen Skills

## Skill Structure

Each skill lives in its own directory with this structure:

```
skill-name/
├── SKILL.md           # Skill definition (YAML frontmatter + instructions)
└── references/        # Supporting documentation
    └── *.md
```

## SKILL.md Format

```markdown
---
name: skill-name
description: Brief description for skill discovery
allowed-tools: Bash(melogen *), Bash(pip install melogenai)
triggers:
  - keyword1
  - keyword2
---

# Skill Title

Instructions for Claude on how to use this skill...
```

### Fields

| Field | Required | Description |
|-------|----------|-------------|
| `name` | Yes | Unique skill identifier |
| `description` | Yes | Brief description (shown in skill listings) |
| `allowed-tools` | Yes | Tool permissions needed |
| `triggers` | No | Keywords that activate this skill |

## Adding a New Skill

1. Create a new directory under the repo root
2. Write `SKILL.md` with YAML frontmatter
3. Add reference docs in `references/` if needed
4. Update the root `README.md` skill table
5. Submit a pull request

## Guidelines

- Keep skill instructions clear and actionable
- Include code examples in SKILL.md
- Reference docs should cover edge cases and advanced usage
- Test the skill manually before submitting
