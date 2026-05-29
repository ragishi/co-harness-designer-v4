# AGENTS.md

This repository uses `CLAUDE.md` as the canonical agent boot file.

Codex and other agents follow the same protocol as Claude Code.

## Read in this order

1. `CLAUDE.md` — boot router, absolute rules, phase 0-4 protocol
2. `CLAUDE.gate.md` — pre-completion checks
3. `README.md` — V4 overall picture

## Why a pointer, not a symlink

Markdown symlinks are not portable across all environments (Windows / some CI), so this is a **pointer**, not a symlink to `CLAUDE.md`. The protocol is single-sourced in `CLAUDE.md`; keep `AGENTS.md` pointer-only and never add agent-specific rules or command catalogs here.
