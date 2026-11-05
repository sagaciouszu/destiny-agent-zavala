# Zavala - Agent

> **Version:** 0.1.1 | **Last updated:** 2026-11-05 | **Status:** Ready

> **Depends On:** AGENTS.md
> **Token Estimate:** ~379 tokens

Zavala is an independent Destiny character agent built on the shared
Destiny Agent Grimoire: one canonical SQLite archive, one verified quote
policy, many distinct personas.

## Quick start

```bash
./setup.sh                      # link or clone the grimoire and get the database
bash tests/master-audit.sh      # local suites + shared gates
```

## Deploy

- **OpenCode:** `lore/scripts/sync-live-agents.sh` installs `zavala.md`, keeps
  companions inert under `zavala/`, and generates a read-only `zavala-consult`
  subagent.
- **OpenClaw:** `lore/scripts/sync-live-agents.sh --openclaw` writes
  `~/.openclaw/workspace-zavala` and the series block.
- **Generic runtime:** point it at `AGENTS.md` and `INDEX.md`.

## Verification

| Suite | Command | Expected |
|---|---|---|
| Full agent audit | `bash tests/master-audit.sh` | all suites pass |
| Module completeness | `bash tests/module-test.sh` | 0 failed |
| Quote verification | `bash tests/quote-verify.sh` | 0 unverified |
| Database integrity | `bash lore/tests/test-db.sh` | 51 checks |
| File conformance | `python3 lore/tests/conformance.py` | PASS |

## Troubleshooting

- **`lore/` missing:** run `./setup.sh`.
- **Dangling `lore/` symlink:** `setup.sh` recreates it.
- **No canon:** verify `lore/db/grimoire.db` exists.
- **Quote fails verification:** do not use it; find the canonical line first.

## License

MIT. Destiny and all related property belong to Bungie.
