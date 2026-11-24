# Security Architecture

## Security posture

Traceforge analyses untrusted code and instructions. A repository's README, setup scripts, package lifecycle scripts, hooks, MCP configuration, agent instructions, and dependencies may all cause side effects. Treat all repository-controlled content as untrusted.

A scanner score is one signal, not a permission slip.

## Required sequence

1. Acquire source without running repository code.
2. Store an immutable, read-only source snapshot.
3. Perform static inspection and scanner assessment.
4. Present findings, score semantics, limitations, and policy recommendation.
5. Decide which operations are permitted.
6. Prepare a disposable isolated environment.
7. Execute only approved operations with constrained resources and observable events.
8. Preserve logs, artifacts, and policy decisions.

## NVIDIA SkillSpector integration

SkillSpector is intended as a security assessment integration. Before implementation:
- Verify the official NVIDIA project and documentation.
- Confirm supported input types and version.
- Confirm installation and invocation requirements.
- Confirm exact score scale and whether higher or lower means safer.
- Confirm severity definitions and output schema.
- Establish licensing and redistribution constraints.
- Build fixture-based adapter tests.

Do not infer score direction from a number or an unofficial description. Store raw tool output and normalized findings separately. If unavailable, report scanner unavailable and continue with other safe static analysis; never fabricate a score.

## Isolation requirements

Execution must not occur directly on the user's host by default. The execution backend should provide:
- Disposable filesystem and working directory.
- Read-only source mount where feasible.
- Explicit writable output area.
- CPU, memory, process, and time limits.
- Network disabled by default, with narrowly scoped opt-in policies.
- No host home-directory, SSH, cloud credential, browser profile, or Docker socket access.
- No implicit access to environment secrets.
- Explicit handling of environment variables and secrets.
- Process-tree termination and cleanup.
- Captured stdout/stderr, exit codes, filesystem changes, and policy-relevant events.

Docker is one possible backend, not a complete security boundary by itself. Evaluate container hardening and platform differences. On unsupported platforms, disable execution or use a separately validated backend.

## Approval model

Separate low-risk read-only analysis from side-effecting operations. Require clear user approval for installing dependencies, running scripts, enabling network access, starting services, invoking external tools, or providing credentials. Approval should state what will run, where, with what permissions, and for how long.

High-risk findings should block execution unless the user deliberately overrides a documented policy. Some risks should be non-overridable.

## Local application security

- Bind API to loopback by default.
- Protect state-changing endpoints with a session token.
- Validate WebSocket origin and authentication.
- Avoid shell-string interpolation; use argument arrays and strict executable allowlists.
- Sanitize rendered Markdown and source previews.
- Prevent path traversal and symlink escape during archive extraction.
- Redact secrets in logs and exports.
- Keep credentials out of SQLite, snapshots, and generated reports by default.
- Apply safe archive size, nesting, file count, and decompression limits.

## Threat model

Threats include malicious setup scripts, prompt injection in repository instructions, dependency compromise, archive traversal, credential exfiltration, resource exhaustion, local API abuse, malicious output rendering, and misleading scanner results.

Traceforge must document residual risks. No security scan or container setup can guarantee that arbitrary code is harmless.
