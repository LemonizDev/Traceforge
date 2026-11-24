# Product Requirements

## 1. Product summary

Traceforge is an npm-distributed CLI and locally hosted browser workspace for deep inspection, controlled execution, visualisation, and comparison of agentic repositories.

## 2. Users and jobs

Primary users:
- Developers evaluating unfamiliar agentic repositories.
- Builders maintaining skill libraries, agent frameworks, and instruction-heavy projects.
- Engineers comparing their own systems with external implementations.
- Researchers investigating how agentic systems are assembled and behave.

Core jobs:
- Understand a repository without manually opening every file.
- Safely determine whether and how it can be executed.
- Reconstruct workflows and dependencies.
- Verify whether claimed behaviour is supported by runtime evidence.
- Revisit and compare prior analyses.

## 3. Functional requirements

### Repository workspace
- Accept GitHub URL, Git URL, local path, and ZIP archive.
- Identify repository identity, revision, ecosystem, structure, and detected component types.
- Maintain a persistent registry of multiple repositories.
- Support reopening, rescanning, stage-level reruns, removal, and comparison.
- Record source revision and analysis version so results are reproducible and freshness is visible.

### Security
- Perform static inspection before executing repository-controlled setup or scripts.
- Integrate NVIDIA SkillSpector where technically and legally feasible; validate the official tool, version, interface, score direction, and output schema before implementation.
- Present findings, severity, score interpretation, and limitations.
- Apply execution policy gates based on risk and user approval.
- Never represent a scanner score as a safety guarantee.
- Keep source acquisition and static reading distinct from code execution.

### Extraction and understanding
- Detect instruction files, skills, commands, agents, hooks, scripts, MCP servers/tools, references, templates, dependencies, and configuration.
- Support common formats including Markdown, JSON, YAML, TOML, shell, Python, JavaScript/TypeScript, and PowerShell.
- Resolve references recursively with cycle detection and depth/resource limits.
- Preserve exact source locations and content hashes.
- Record parser confidence and unresolved references.

### Knowledge graph
- Model components as typed nodes and relationships as typed edges.
- Support relationships such as contains, references, invokes, delegates-to, depends-on, configures, triggers, produces, and guards.
- Attach source evidence, confidence, and discovery method to relationships.
- Support multiple visual projections over the same underlying graph.

### Environment reconstruction
- Detect runtimes, package managers, dependencies, external services, environment variables, and platform assumptions.
- Produce an environment manifest and missing-prerequisite report.
- Reconstruct environments only in isolated, disposable execution contexts.
- Permit static-only analysis when execution is unavailable or denied.

### Workflow reconstruction and execution
- Reconstruct workflows from instructions, commands, references, scripts, and runtime conventions.
- Represent triggers, sequence, branches, conditions, delegation, error paths, and outputs where evidence supports them.
- Execute approved workflows in controlled environments.
- Capture logs, process events, tool calls, filesystem changes, network policy events, exit status, and artifacts.
- Label each step as executed, simulated, inferred, blocked, failed, or not executable.

### Evidence and intelligence
- Compare declared behaviour with reconstructed and observed behaviour.
- Detect broken references, dead or unreachable components, missing dependencies, contradictions, duplication, and unverified claims.
- Separate factual findings from recommendations and speculative hypotheses.
- Link every finding to supporting evidence and confidence.

### Visual workspace
- Provide Architecture, Workflow, Dependencies, Agent Network, Instruction Map, and Execution Trace views.
- Support search, filters, zoom, pan, expand/collapse, tabs, saved layouts, and full-screen graph.
- Support bidirectional navigation between graph nodes and source files.
- Allow annotations, grouping, and custom layouts without mutating the analysed repository.
- Provide resizable/hideable Explorer, Inspector, and Console panels.
- Support dark and light themes, with dark as the initial default.

### Comparison
- Compare any two or more repositories already in the workspace.
- Compare component inventories, capabilities, workflows, dependency patterns, security findings, execution coverage, and architecture.
- Distinguish absent capability from capability not detected.
- Show evidence and analysis-version differences.

### Export
- Export reports, graph data, diagrams, security summaries, execution traces, dependency/environment manifests, and comparisons.
- Preserve repository identity, revision, timestamps, tool versions, and evidence references.

## 4. Non-functional requirements

- Local-first data handling by default.
- Safe-by-default execution with explicit trust boundaries.
- Reproducible and versioned analysis.
- Incremental analysis where practical.
- Large-repository resource limits and cancellation.
- Clear progress and actionable errors.
- Core analysis APIs usable without the browser UI.
- Accessible navigation and readable graph layouts.
- No silent data loss when an analysis is interrupted.

## 5. Out of scope for initial release

- Hosted multi-tenant SaaS.
- Arbitrary execution on the host machine.
- A graph-based workflow authoring or automation editor.
- Guaranteeing that a repository is safe because a scanner score is favourable.
- Automatic modification of analysed repositories.
- Full semantic understanding of every possible agent framework.
- Guaranteed reproduction of external services requiring private credentials.

## 6. Success measures

- A user can ingest and identify a supported repository without manual restructuring.
- Detected components link back to precise source locations.
- References and relationships are inspectable and evidence-backed.
- Static analysis remains useful when execution is blocked.
- Execution status clearly distinguishes actual, simulated, and inferred steps.
- Users can retain multiple repository analyses and compare them later.
- Re-running analysis after a source change updates affected results without corrupting historical evidence.
