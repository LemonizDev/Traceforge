# Testing Strategy

## Principles
Test observable contracts. Use fixture repositories across agent ecosystems and ordinary software. Preserve malicious/malformed fixtures. Test provenance and status distinctions as first-class behaviour. Avoid real secrets and uncontrolled external services.

## Test layers
- **Unit:** parsers, path resolution, archive validation, graph algorithms, schemas, claim status, redaction, policy.
- **Contract:** adapters, storage, CLI/API, event schemas, execution backends, exports.
- **Integration:** acquisition→extraction, extraction→graph, workflow reconstruction, persistence, incremental reruns, comparison.
- **End-to-end:** CLI startup, local UI, adding multiple repos, reopening analyses, graph/source navigation, console events, comparisons.
- **Security:** archive traversal, symlink escape, path traversal, command injection, prompt injection, malicious Markdown, API auth/origin, secret leakage, resource exhaustion, process cleanup, network isolation.
- **Execution:** timeout, cancellation, child termination, network denial, read-only source, output capture, simulation labels, crash cleanup.

## Golden fixtures
Maintain documented fixtures for skills/instruction references; commands invoking scripts; agents/delegation; hooks/lifecycle; MCP; mixed ecosystems; broken references/cycles; contradictory instructions; malicious setup/archive paths; workflows with branches, failures, and external dependencies.

## Evidence correctness
- Declared claims cannot become observed without runtime evidence.
- Simulated events remain simulated.
- Every extracted edge has provenance.
- Not detected differs from confirmed absent.
- Comparisons disclose source revisions and analysis versions.

## Release gates
All tests pass; security-sensitive changes reviewed; migrations tested against prior schemas; exports validated; platform support claims match CI coverage.
