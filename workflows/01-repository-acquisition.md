# Workflow 01: Repository Acquisition and Identification

## Goal
Acquire a repository as data, establish its identity and revision, and create a safe source snapshot.

## Inputs
GitHub URL, Git URL, local directory, or ZIP archive; optional display name and workspace destination.

## Steps
1. Validate input shape and provider.
2. Acquire using the appropriate adapter without running repository-controlled code.
3. For Git sources, record canonical origin, commit SHA, branch/tag when known, and dirty state if local.
4. For ZIP/local sources, compute a stable snapshot digest and record provenance.
5. Apply archive/path traversal, symlink, file-count, file-size, and decompression limits.
6. Inventory files, directories, file types, and likely ecosystems.
7. Detect candidate instruction/agent ecosystem markers without assuming a single framework.
8. Register repository and revision in the persistent workspace.
9. Emit acquisition manifest and progress events.

## Outputs
Repository profile, immutable source snapshot, revision identity, file inventory, preliminary ecosystem classification, acquisition log.

## Failure handling
Invalid input, inaccessible remote, authentication required, unsupported archive, resource limit exceeded, or incomplete local snapshot. Preserve partial diagnostics; do not execute code to recover.

## Evidence
Origin, commit/digest, acquisition timestamp, file hashes, adapter/version, skipped files and reasons.

## Acceptance criteria
- Supports all four input types.
- Never invokes install scripts or repository commands during acquisition.
- Rejects archive traversal and unsafe paths.
- Reopening a repository resolves the correct snapshot and analysis history.
