# Maintenance

## Change workflow

1. Identify the observed failure, new requirement, or stale knowledge.
2. Change the smallest authoritative layer that addresses it: metadata, runtime, reference, knowledge, tooling, or evaluation.
3. Preserve unrelated behavior and repository identity.
4. Run static audit and regression tests.
5. When runtime or trigger behavior changes, run representative positive, negative, and edge cases in a fresh context when the host permits it.
6. Recheck current product documentation for platform-dependent claims.
7. Record material changes in Git history and, when useful, `CHANGELOG.md`.

## Naming

The canonical name is **Prompting** and the runtime identifier is `prompting`. Do not reintroduce the former name in active files.
