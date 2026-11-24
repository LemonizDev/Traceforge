# Implementation Roadmap

Sequence work to reduce risk and validate assumptions. This is not a promise that every phase ships together.

## Phase 0: Validate foundations
- Verify SkillSpector official source, capabilities, score semantics, and licensing.
- Spike npm CLI packaging and local service security.
- Validate SQLite persistence/migrations.
- Test graph rendering with realistic repositories.
- Test execution isolation on supported OSes, especially Windows.
- Define adapter and evidence contracts.
**Exit:** key architectural risks are documented; no unresolved blocker is hidden behind assumptions.

## Phase 1: Workspace and acquisition
CLI bootstrap, configuration, persistent workspace, repository registry, GitHub/Git/local/ZIP acquisition, immutable snapshots, inventory, basic UI.

## Phase 2: Extraction and graph
Format parsers, initial ecosystem adapters, component/source model, reference resolution, graph construction, architecture/instruction/dependency views.

## Phase 3: Security and environment
Static checks, SkillSpector adapter if validated, findings UI, policy engine, environment detection/manifests, approval flows.

## Phase 4: Workflow reconstruction
Entry-point detection, workflow model, graph projections, evidence-linked reconstructed paths, uncertainty reporting.

## Phase 5: Controlled execution
Isolated backend, execution plans/approvals, event capture, artifact store, simulation adapter with explicit labels, cleanup and failure recovery.

## Phase 6: Intelligence and comparison
Claim/evidence verification, repository insights, recommendations, multi-repository comparison, historical run/revision comparison.

## Phase 7: Export and hardening
Reports, portable exports, incremental analysis, performance, accessibility, docs, packaging, security review, release automation.

## Release gates
A UI control does not mean a feature is complete. Every phase requires automated tests, acceptance criteria, error handling, and documentation. Execution/security require threat-model review.
