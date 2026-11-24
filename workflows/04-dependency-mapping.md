# Workflow 04: Instruction and Dependency Mapping

## Goal
Construct an evidence-backed graph connecting discovered components.

## Steps
1. Convert explicit references and declarations into typed edges.
2. Resolve paths and identifiers against the component inventory.
3. Detect invocation, delegation, dependency, trigger, configuration, and output relationships.
4. Use static code analysis for supported languages to discover additional relationships.
5. Mark inferred edges separately from explicit references.
6. Attach evidence, confidence, source spans, and discovery method.
7. Detect cycles, orphan components, high fan-in/fan-out, and unresolved edges.
8. Generate graph projections for architecture, instructions, dependencies, and agent network.

## Outputs
Versioned knowledge graph, unresolved edge list, graph metrics, graph query API.

## Acceptance criteria
- Every edge has a relationship type and provenance.
- Weak textual associations are not presented as proven invocation.
- Graphs can be regenerated from structured data.
