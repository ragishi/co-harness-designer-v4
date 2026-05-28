# AGENTS.md

This repository uses `CLAUDE.md` as the canonical agent boot file.

Codex and other agents follow the same protocol as Claude Code.

## Read in this order

1. `CLAUDE.md` — boot router, absolute rules, phase 0-4 protocol
2. `CLAUDE.gate.md` — pre-completion checks
3. `README.md` — V4 overall picture

## Note on symlink

Some environments do not handle markdown symlinks well. This file is therefore a **pointer file**, not a symlink. The canonical content lives in `CLAUDE.md`. Do not edit `AGENTS.md` to add agent-specific content — keep the protocol single-sourced in `CLAUDE.md`.
