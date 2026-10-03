# Prompting

**A system for designing effective instructions, context, workflows, and interactions that help AI understand tasks clearly and produce more accurate, useful, and reliable results.**

Prompting is the canonical repository for the reusable runtime Skill and its supporting knowledge base. It covers problem formulation, instruction design, context engineering, examples and output formats, decomposition, research, retrieval, tools, multimodal work, model selection, evaluation, verification, iteration, orchestration, safety, and practical application.

## Repository structure

- `SKILL.md` — canonical runtime behavior.
- `references/` — concise operational references used selectively during execution.
- `knowledge/` — 22 deeper knowledge modules plus an index.
- `scripts/` — deterministic static audit tooling and regression tests.
- `evaluation/` — verification status and test boundaries.
- `docs/` — architecture and maintenance guidance.
- `agents/openai.yaml` — host-facing metadata.

## Runtime identifier

`prompting`

## Knowledge loading

Start with `SKILL.md`. Open `references/` when an operational decision needs more detail. Use `knowledge/README.md` as the retrieval map and load only the modules relevant to the current task. Full access does not mean loading the full knowledge base into every context.

## Design principle

Prompting should improve the path from user intent to usable output without forcing the user to write formal prompts or exposing unnecessary internal process. It should help select the right context, tools, evidence, structure, verification, and interaction strategy for the task at hand.
