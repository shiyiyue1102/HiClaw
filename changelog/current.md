# Changelog (Unreleased)

Record image-affecting changes to `manager/`, `worker/`, `openclaw-base/` here before the next release.

---

- fix(manager): clean orphaned session write locks before starting OpenClaw to prevent "session file locked (timeout)" after SIGKILL or crash
- fix(worker): Remote->Local sync pulls Manager-managed files only (allowlist) to avoid overwriting Worker-generated content (e.g. .openclaw sessions, memory)
- fix(copaw): align sync ownership with OpenClaw worker (AGENTS.md/SOUL.md Worker-managed, push but never pull; allowlist for Remote->Local)
- fix(manager): switch Matrix room preset from `private_chat` back to `trusted_private_chat` so Workers are auto-joined without needing to accept invites; use `power_level_content_override` to keep Workers at power level 0
- feat(manager): add `setup-github-mcp.sh` script to mcp-server-management skill for runtime GitHub PAT configuration via chat; update SKILL.md with usage instructions

