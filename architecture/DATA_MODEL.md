# Data Model

## Goals

The model must support many repositories, immutable source revisions, repeated analysis runs, typed component relationships, execution evidence, comparisons, and exports. It must preserve provenance and uncertainty.

## Core entities

- **Workspace**: local Traceforge data boundary and settings.
- **Repository**: logical repository identity, provider, canonical origin, display name.
- **RepositoryRevision**: immutable source identity such as commit SHA, archive digest, or local snapshot digest.
- **SourceFile**: path, content hash, detected format, size, and snapshot reference.
- **AnalysisRun**: revision, Traceforge version, adapter versions, start/end times, status, and configuration.
- **AnalysisStage**: named stage, status, inputs, outputs, timing, and errors.
- **Component**: typed discovered entity such as instruction, skill, command, agent, hook, script, MCP server/tool, config, template, dependency, or external service.
- **Relationship**: typed directed edge between components.
- **Evidence**: source span, parsed structure, runtime event, artifact, scanner finding, or user annotation.
- **Claim**: statement about intended, reconstructed, or observed behaviour.
- **Finding**: issue, anomaly, risk, or insight supported by evidence.
- **EnvironmentManifest**: runtimes, packages, tools, services, variables, platform assumptions, and missing prerequisites.
- **Workflow**: reconstructed process with triggers, steps, branches, and outputs.
- **ExecutionSession**: policy, environment, start/end, status, and execution backend.
- **ExecutionEvent**: normalized process, tool, filesystem, network-policy, or agent event.
- **Artifact**: output file or structured result created during execution.
- **Comparison**: selected repositories/runs and computed comparison results.
- **Annotation/Layout**: user-owned workspace metadata, never written into source snapshots.

## Provenance contract

Every extracted component and relationship should include, where available:
- Source repository and revision.
- Source file path and line/byte range.
- Content hash.
- Extraction adapter and version.
- Discovery method: explicit, parsed, inferred, runtime-observed, or user-annotated.
- Confidence or certainty classification.
- Analysis run identifier.

Runtime evidence additionally records execution session, event timestamp, environment, and event source.

## Relationship vocabulary

Initial vocabulary:
- contains
- references
- invokes
- delegates_to
- depends_on
- configures
- triggers
- guards
- produces
- consumes
- overrides
- extends
- conflicts_with
- observed_calls

Relationship types must be extensible and documented. Avoid inventing a direct edge when only a weak textual association exists; use a lower-confidence reference relation instead.

## Claim status

Claims should distinguish:
- declared: explicitly stated in repository content.
- reconstructed: inferred from connected instructions or code.
- observed: demonstrated by captured runtime evidence.
- simulated: demonstrated only under a substitute or mock.
- contradicted: evidence conflicts with the claim.
- unverified: insufficient evidence.
- blocked: verification could not proceed.

A claim can have multiple supporting and contradicting evidence records.

## Persistence

SQLite is the proposed initial metadata store. Larger source snapshots, logs, and artifacts may live in content-addressed files on disk, referenced from SQLite. Use migrations, transactions, integrity checks, and explicit retention controls.

Never use repository path alone as a global identity. The same repository can have multiple revisions and multiple analysis runs.
