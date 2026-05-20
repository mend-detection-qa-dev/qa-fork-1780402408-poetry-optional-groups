# poetry-optional-groups

Tests *Poetry 1.2+ optional dependency group* syntax: `[tool.poetry.group.<name>]` with `optional = true`.

## Why this matters

Existing repo `poetry_exclude-dev-dependencies` covers the *legacy* `[tool.poetry.dev-dependencies]`
table (Poetry <1.2 syntax). Poetry 1.2+ introduced named groups with `optional = true`, going through
a different lockfile parser path.

## Group layout

| Group | `optional` | Packages |
|---|---|---|
| (main) | false | `requests`, `click`, `pyyaml` |
| `dev` | true | `pytest`, `pytest-cov` |
| `test` | true | `hypothesis`, `faker` |

## Key assertions

- Only 3 direct deps (main group) in production tree
- `pytest`, `pytest-cov`, `hypothesis`, `faker` must *not* appear
