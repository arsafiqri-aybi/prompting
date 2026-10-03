# Repository Architecture

Prompting is one capability repository containing runtime instructions, concise operational references, deeper knowledge, evaluation, and deterministic validation tooling.

```text
prompting/
├── SKILL.md
├── agents/openai.yaml
├── assets/
├── references/
├── knowledge/
├── scripts/
├── evaluation/
├── docs/
├── .github/workflows/
└── README.md
```

## Authority order

1. `SKILL.md` — active runtime procedure and decision policy.
2. `references/` — concise operational detail explicitly linked from runtime.
3. `knowledge/` — deeper concepts, evidence, methods, and examples.
4. Git history — provenance of repository changes.

Knowledge informs decisions but does not override the current user request, higher-priority instructions, host permissions, or current facts obtained from authoritative sources.

## Progressive disclosure

The repository is designed for full access with selective loading. Agents should not load all 22 knowledge modules by default. The knowledge index maps task needs to the smallest useful set of modules.
