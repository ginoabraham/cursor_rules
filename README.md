# cursor_rules

A shareable collection of opinionated, enterprise-grade [Cursor](https://cursor.com) rules for the languages and frameworks I work with most. Each rule captures architecture, security, testing, and tooling standards so the AI agent writes code that is production-ready by default.

## Available rules

| Rule | Applies to | Highlights |
| ---- | ---------- | ---------- |
| [`python.mdc`](.cursor/rules/python.mdc) | `**/*.py`, `**/pyproject.toml` | Python 3.14+, Clean Architecture/DDD, FastAPI, Pydantic v2, SQLAlchemy 2.0 + asyncpg, strict typing, zero-copyleft licensing |

More rules for other technologies will be added over time.

## Usage

Copy the rule files you want into your project's `.cursor/rules/` directory:

```bash
mkdir -p .cursor/rules
curl -fsSL https://raw.githubusercontent.com/ginoabraham/cursor_rules/main/.cursor/rules/python.mdc \
  -o .cursor/rules/python.mdc
```

Cursor picks up the rule automatically. Rules with `globs` are attached when matching files are in context; rules with `alwaysApply: true` are included in every session.

If a rule conflicts with an existing project's conventions, the rules instruct the agent to follow the project and flag the conflict.

## Contributing

Each rule lives in `.cursor/rules/<technology>.mdc` with YAML frontmatter (`description`, `globs`, `alwaysApply`). Keep rules focused on one technology, actionable, and backed by a concrete example.
