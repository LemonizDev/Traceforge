# Workflow 03: Deep Repository Extraction

## Goal
Discover the components that make the repository function.

## Candidate component types
Instruction files (AGENTS.md, CLAUDE.md and ecosystem equivalents), skills, commands, prompts, agents/subagents, hooks, lifecycle events, scripts, MCP servers/tools, templates, references, configuration, package manifests, dependencies, external services, and documentation.

## Steps
1. Apply generic file discovery and ecosystem adapters.
2. Parse supported formats with deterministic parsers where possible.
3. Extract frontmatter, metadata, triggers, arguments, instructions, tool declarations, references, and execution hints.
4. Recursively resolve referenced files and local dependencies.
5. Detect cycles, missing references, ambiguous paths, and unsupported formats.
6. Record source spans, hashes, adapter versions, and confidence.
7. Retain unclassified files in the inventory.

## Outputs
Typed component inventory, source map, unresolved-reference report, extraction diagnostics.

## Acceptance criteria
- Components link to exact source locations.
- Extraction does not execute content.
- Cycles and repeated references are handled safely.
- Unknown conventions do not cause files to disappear.
