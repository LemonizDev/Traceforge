# Agent and Intelligence Architecture

## Purpose

Traceforge may use language models to interpret complex instructions, reconstruct workflows, summarize systems, and generate insights. Models are analysis assistants, not sources of truth and not execution authorities.

## Separation of responsibilities

- Deterministic parsers extract structured facts where possible.
- Static analyzers inspect code and configuration.
- Graph algorithms resolve paths, cycles, reachability, and dependency structure.
- Runtime instrumentation records observed behaviour.
- Models interpret ambiguous natural-language instructions and propose hypotheses.
- Evidence validation checks model-generated claims against source/runtime evidence.
- Policy engine independently gates execution.

## Model output contract

Model-generated outputs should be structured and schema-validated. Each claim should include:
- Claim text.
- Claim class: declared, reconstructed, recommendation, or hypothesis.
- Evidence references.
- Confidence with a defined meaning.
- Unresolved ambiguity.
- Model/provider and prompt/template version when relevant.

A model must be allowed to return unknown or insufficient evidence. Do not reward confident completion when the source is ambiguous.

## Prompt injection and untrusted content

Repository instructions are data being analysed, not instructions to Traceforge's own agent. Never concatenate untrusted repository content into a privileged system instruction. Delimit and label source content, restrict tool permissions, and prevent repository text from changing security policy, workspace scope, or credential handling.

Model analysis should not execute commands merely because repository content asks it to. Execution plans must pass through the deterministic policy and approval layer.

## Agent ecosystem adapters

Support ecosystem-specific adapters for instruction conventions, skills, commands, subagents, hooks, and MCP configurations. Each adapter declares:
- Supported ecosystem and versions.
- File discovery rules.
- Parsing capabilities.
- Invocation semantics understood.
- Unsupported constructs.
- Test fixtures and adapter version.

Generic fallback extraction should remain available for unknown ecosystems.

## Human control

Users can inspect evidence, correct labels, annotate nodes, and approve gated actions. Human annotations are stored separately from source facts and model inferences. Corrections should improve the current workspace without rewriting original evidence.
