# System Architecture

## Architectural shape

Traceforge is a modular TypeScript application with a CLI, local service, analysis engines, durable storage, and browser UI. The core engines must be usable programmatically and must not depend on React or browser state.

## Logical layers

1. **CLI**: command parsing, configuration, workspace selection, headless operation, and local server lifecycle.
2. **Workspace Manager**: repository registry, analysis sessions, lifecycle, history, and comparison coordination.
3. **Acquisition Engine**: clone/download/local discovery, revision identity, safe unpacking, and source inventory.
4. **Security Engine**: static risk checks, SkillSpector adapter, policy decisions, and execution gating.
5. **Extraction Engine**: format-aware parsing of instructions, skills, commands, agents, hooks, scripts, configs, and references.
6. **Knowledge Graph Engine**: typed nodes/edges, provenance, graph queries, and projections.
7. **Environment Engine**: runtime and dependency detection, manifests, and disposable environment preparation.
8. **Workflow Engine**: workflow reconstruction, planning, execution orchestration, and state transitions.
9. **Execution Engine**: isolated process/tool execution, resource limits, event capture, and artifact collection.
10. **Evidence Engine**: provenance, event normalization, claim verification, and confidence.
11. **Intelligence Engine**: structural insights, anomaly detection, summaries, and recommendations.
12. **Comparison Engine**: cross-repository alignment and difference analysis.
13. **Storage Engine**: SQLite-backed metadata and durable artifact/evidence storage.
14. **Local API Server**: authenticated local HTTP API and WebSocket event stream.
15. **Visual Workspace**: React UI, graph views, source navigation, inspectors, and console.

## Proposed technology baseline

Initial recommendation, subject to a technical spike:
- Node.js LTS and TypeScript.
- npm workspaces or a similarly simple monorepo setup.
- Commander.js for CLI.
- Fastify for local API.
- WebSockets for live events.
- SQLite for structured local metadata.
- Zod for runtime schema validation.
- React and TypeScript for UI.
- Tailwind CSS and shadcn/ui for interface primitives.
- @xyflow/react for graph rendering and navigation.
- Docker or another isolated backend as an execution option, not a requirement for static inspection.

Do not treat these choices as immutable. Validate ecosystem compatibility, security, maintenance, packaging, and Windows support before locking implementation.

## Data flow

Repository input → acquisition and immutable source snapshot → static security inspection → extraction → graph construction → environment analysis and workflow reconstruction → policy-gated execution → evidence analysis → intelligence and visual projections → exports/comparisons.

Static analysis must be independently useful. Execution is an optional, gated branch, not a prerequisite for understanding the repository.

## Runtime boundaries

- CLI and local API coordinate operations.
- Analysis jobs run as cancellable jobs with explicit states.
- UI receives progress and event updates but does not own analysis state.
- Engines communicate through versioned domain contracts.
- Persist stage outputs so interrupted work can resume safely.
- Keep source snapshots read-only.

## Suggested monorepo boundaries

```
packages/
  cli/
  core/
  workspace/
  acquisition/
  security/
  extraction/
  knowledge-graph/
  environment/
  workflow/
  execution/
  evidence/
  intelligence/
  comparison/
  storage/
  api/
  ui/
```

Package boundaries should be justified by independent responsibilities and testability, not created mechanically before implementation. Avoid premature micro-packaging.

## Local service security

Bind to loopback by default. Use a per-session secret or equivalent protection for state-changing API operations and WebSocket connections. Validate origins, reject unexpected host headers where relevant, and do not expose the service to a LAN unless the user explicitly configures it with clear warnings.

## Extensibility

Use adapters for repository providers, scanners, parsers, execution backends, and agent ecosystems. An adapter must declare supported versions, capabilities, limitations, and provenance. Unknown formats should be retained as unclassified files rather than silently discarded.
