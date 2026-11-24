# Architectural Decisions

This file records decisions accepted during product planning. Revisit them only when evidence or a concrete implementation constraint warrants it.

## ADR-001: Local-first npm CLI with browser UI
**Status:** Accepted

Traceforge is initially distributed as an npm CLI that starts a local browser-based workspace. It is not initially a conventional hosted SaaS product. Desktop packaging may be considered later.

## ADR-002: Persistent multi-repository workspace
**Status:** Accepted

The UI remains useful after the first repository is analysed. Users can add repositories, revisit existing analyses, rerun stages, and compare repositories from one persistent workspace.

## ADR-003: Hybrid execution fidelity
**Status:** Accepted

Reproduce real environments where feasible, and use controlled substitutes when external services or credentials are unavailable. Explicitly distinguish actual execution, simulation, partial execution, inference, and blocked/not-executable states.

## ADR-004: Hybrid Engineering Workspace
**Status:** Accepted

The interface combines an interactive graph with IDE-like Explorer, Inspector, and Console panels. It is not merely a dashboard and not a workflow authoring canvas.

## ADR-005: Graph is navigational, not an execution engine
**Status:** Accepted

Use a graph visualisation library such as @xyflow/react to display and navigate architecture and workflows. Workflow orchestration belongs to the backend engines.

## ADR-006: Modular engines over a UI-centric monolith
**Status:** Accepted

Separate acquisition, security, extraction, graph, environment, workflow, execution, evidence, intelligence, comparison, storage, API, and UI responsibilities behind stable contracts.

## ADR-007: Evidence-backed claims
**Status:** Accepted

Traceforge must distinguish repository-declared behaviour, reconstructed/inferred behaviour, runtime-observed behaviour, and simulated behaviour.

## ADR-008: SkillSpector as a security signal
**Status:** Accepted in principle; integration details unverified

NVIDIA SkillSpector should be evaluated as an early security assessment step. Exact official source, interface, score direction, and semantics must be verified before implementation. Its score is not a safety guarantee or an execution sandbox.

## ADR-009: Static analysis remains independently useful
**Status:** Accepted

A repository can still be inspected and visualised when execution is unavailable, denied, or unsupported.

## ADR-010: User annotations do not mutate analysed source
**Status:** Accepted

Layouts, labels, groups, and notes are stored as Traceforge workspace metadata.

## ADR-011: Agent/model neutrality
**Status:** Accepted

The product should be usable and understandable by developers working with Claude, Codex, OpenCode, and other coding agents. Do not couple the project specification to one coding agent.

## ADR-012: Implementation choices require validation
**Status:** Accepted

Node.js/TypeScript, React, Fastify, SQLite, Zod, and related tools are the proposed baseline, not unquestionable commitments. Validate with technical spikes before locking.
