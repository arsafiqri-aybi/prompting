# Agent Guidance

When working in this repository:

- Treat `SKILL.md` as the canonical active runtime behavior.
- Use `references/` for concise operational guidance.
- Use `knowledge/README.md` as the retrieval map for deeper knowledge and load only what the task needs.
- Preserve the canonical identity `Prompting` / `prompting`.
- Do not turn the knowledge base into one giant runtime prompt.
- Recheck time-sensitive platform claims before relying on them.
- Run `python scripts/audit_skill.py . --portable` and `python scripts/test_audit_skill.py` after structural or tooling changes.
- Do not claim model switching, host installation, external actions, or automatic trigger behavior without observable evidence.
- Do not add secrets, credentials, private memory, or unrelated project state to this repository.
