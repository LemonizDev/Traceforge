# Workflow 06: Workflow Discovery and Reconstruction

## Goal
Reconstruct how a user request or trigger moves through the repository's components.

## Steps
1. Identify entry points: user-facing commands, skill triggers, hooks, API endpoints, scheduled jobs, or documented invocation patterns.
2. Follow references, conditional instructions, delegation, scripts, tool declarations, and output handling.
3. Model sequence, branches, guards, retries, error paths, and termination where supported.
4. Connect workflow steps to graph components and source evidence.
5. Label uncertain transitions as inferred and unresolved.
6. Generate readable workflow summaries and graph projections.

## Outputs
Workflow catalogue, step graph, trigger map, unresolved transitions, source-linked explanations.

## Acceptance criteria
- Workflows connect multiple component types rather than listing isolated files.
- Conditional and error paths are represented when evidence exists.
- The reconstruction never claims runtime verification.
