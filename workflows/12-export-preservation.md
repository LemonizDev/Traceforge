# Workflow 12: Reports, Export, and Knowledge Preservation

**Goal:** Make results durable, portable, and useful outside the UI.

**Export types:** repository overview/detail reports; architecture, workflow, and dependency diagrams; machine-readable graph data; security findings and scanner metadata; environment/dependency manifests; execution logs/events/artifacts; comparisons; evidence/provenance bundles.

**Steps**
1. Select repository, revision, analysis run, and export scope.
2. Include tool versions, timestamps, policies, and provenance.
3. Redact secrets and sensitive environment values.
4. Export with stable identifiers and schema versions.
5. Validate integrity and report omitted data.
6. Preserve original analysis in workspace.

**Acceptance:** Exports are reproducible and self-describing; secret redaction is on by default; export does not mutate source or delete history.
