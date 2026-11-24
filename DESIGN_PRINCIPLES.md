# Design Principles

1. **Evidence before interpretation.** Every extracted fact and important relationship should point to source or runtime evidence.
2. **Declared is not observed.** Instructions describe intended behaviour; they do not prove execution.
3. **Simulation is not execution.** Simulated services, mocked tools, and inferred paths must be labelled.
4. **Safe by default.** Untrusted repository content is data until an explicit, policy-controlled execution step.
5. **Fail open for understanding, fail closed for execution.** Missing dependencies should not prevent static inspection; uncertainty should restrict risky execution.
6. **Repository-agnostic core.** Do not assume every repository uses one agent framework or naming convention.
7. **Progressive fidelity.** Start with reliable structural extraction, then deepen semantic and runtime understanding.
8. **Persistent workspace.** Analyses are durable, addressable, and revisitable.
9. **Incremental, reproducible analysis.** Track revisions, hashes, tool versions, and stage outputs.
10. **Explain uncertainty.** Unknown, ambiguous, unsupported, and not detected are valid outcomes.
11. **Navigation over decoration.** Visuals must help users move between architecture, workflow, source, and evidence.
12. **No destructive surprises.** Analysis must not modify source repositories; annotations and layouts belong to Traceforge's workspace.
