# Product Vision

## The problem

Agentic repositories are difficult to understand from their file trees alone. A skill may reference another skill, a command may invoke an agent, an instruction file may define lifecycle behaviour, a hook may mutate execution, and a script may depend on tools that are never declared in the README.

Reading individual files gives fragments. Running an unfamiliar repository without understanding its trust boundaries is dangerous. Existing diagrams are often manually maintained and quickly become stale. Comparing two repositories requires repeated manual investigation.

## The vision

Traceforge turns an agentic repository into an explorable, evidence-backed model of how it is structured, what it says it does, what can be executed, and what execution demonstrates.

The user should be able to open a repository and answer:

- What is this system for?
- What are its major components?
- Which instructions govern which components?
- Which skills, commands, agents, hooks, scripts, and tools call or depend on one another?
- What workflow does a user request trigger?
- What environment and external services are required?
- What is safe to inspect, and what is unsafe or unverified to execute?
- Which behaviours have actually been observed?
- Where is the evidence in the source or execution trace?
- How does this repository compare with another system I have analysed?

## Product form

Traceforge is a local-first developer tool distributed through npm. A CLI manages repositories and starts a local web application. The interface is a persistent workspace, not a disposable report generated for one repository.

A user can analyse repository A, later add repository B, return to A, rerun a changed analysis stage, and compare A and B from the same workspace. Analysis data remains local by default.

## The central experience

The central experience is an interactive engineering workspace:

- Repository Explorer for files and discovered components.
- A central visual canvas for architecture, workflow, dependency, agent, instruction, and execution views.
- Component Inspector for source, references, relationships, findings, and evidence.
- Execution Console for logs, events, tool calls, errors, and generated artifacts.
- Intelligence overview for coverage, complexity, security findings, execution status, and insights.

The graph is navigational and explanatory. It is not a workflow editor and does not itself execute workflows.

## What makes Traceforge different

Traceforge must connect three distinct layers:

1. **Declared system:** what source files and metadata explicitly describe.
2. **Reconstructed system:** what Traceforge infers by resolving references, conditions, dependencies, and workflow structure.
3. **Observed system:** what controlled execution actually demonstrates.

These layers must never be silently conflated. Every meaningful claim should be traceable to source evidence, runtime evidence, or explicitly labelled inference.

## Long-term direction

Build a personal and team intelligence library of agentic systems. Over time, users should be able to discover reusable patterns, compare architectures, identify missing capabilities, and learn from systems they have already analysed.

The initial product remains local-first. Remote collaboration, hosted workspaces, and desktop packaging are possible future directions, not assumptions for the first release.
