# rs

Structured development workflow skills for Claude Code.

## Commands

| Command | Description |
|---------|-------------|
| `/rs:grill-me [idea]` | Systematic design interview before writing any code |
| `/rs:write-tech-spec [file]` | Generate a full tech spec from the conversation |
| `/rs:write-issue [file]` | Generate a concise issue ticket from the conversation |
| `/rs:tdd` | Strict TDD: failing tests → implement → review → commit |
| `/rs:show` | Show the recommended end-to-end workflow |

## Recommended workflow

```
/rs:grill-me [idea]          → interview & clarify
/rs:write-tech-spec name     → document decisions  →  saves docs/name.md
/clear                       → clean context
read docs/name.md            → reload spec
/rs:tdd                      → implement with tests
```
