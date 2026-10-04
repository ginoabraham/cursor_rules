# cursor_rules

A shareable collection of opinionated, enterprise-grade [Cursor](https://cursor.com) rules for the languages and frameworks I work with most. Each rule captures architecture, security, testing, and tooling standards so the AI agent writes code that is production-ready by default.

## Available rules

| Rule | Applies to | Highlights |
| ---- | ---------- | ---------- |
| [`python.mdc`](.cursor/rules/python.mdc) | `**/*.py`, `**/pyproject.toml` | Python 3.14+, Clean Architecture/DDD, Pydantic v2, strict typing, testing, zero-copyleft licensing |
| [`python-fastapi.mdc`](.cursor/rules/python-fastapi.mdc) | Picked by the agent for API and database work | FastAPI, SQLAlchemy 2.0 async, asyncpg, Alembic, RFC 9457 errors; extends `python.mdc` |

More rules for other technologies will be added over time.

## Usage

Copy the rule files you want into your project's `.cursor/rules/` directory:

```bash
mkdir -p .cursor/rules
for rule in python python-fastapi; do
  curl -fsSL "https://raw.githubusercontent.com/ginoabraham/cursor_rules/main/.cursor/rules/${rule}.mdc" \
    -o ".cursor/rules/${rule}.mdc"
done
```

Cursor picks up the rules automatically:

- Rules with `globs` are attached when matching files are in context.
- Rules with only a `description` are pulled in by the agent when the task matches the description.
- Rules with `alwaysApply: true` are included in every session.

If a rule conflicts with an existing project's conventions, the rules instruct the agent to follow the project and flag the conflict.

## Contributing

Each rule lives in `.cursor/rules/<technology>.mdc` with YAML frontmatter (`description`, `globs`, `alwaysApply`). Keep rules focused on one technology, actionable, and backed by a concrete example. Put framework-specific guidance in its own rule (for example `python-fastapi.mdc`) so the core language rule stays lean. Example code should pass the linters and type checkers the rule requires.
