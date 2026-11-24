# Traceforge
### See how agentic systems actually work.

Traceforge is a local-first developer tool for inspecting, understanding, executing, visualising, and comparing agentic repositories.

It is designed for systems whose behaviour is distributed across skills, instructions, commands, agents, hooks, scripts, MCP servers, configuration, dependencies, and runtime conventions. Rather than treating these files as isolated documents, Traceforge reconstructs how they relate and how the system is intended to operate.

> **Product status:** Vision and specification phase. This repository currently contains product and architecture specifications, not a working implementation.

## What Traceforge aims to do

- Ingest GitHub repositories, Git URLs, local directories, and ZIP archives.
- Inspect source safely before executing repository-provided code.
- Use NVIDIA SkillSpector as a security assessment input, with findings and score semantics made explicit.
- Extract instructions, skills, commands, agents, hooks, scripts, MCP definitions, references, dependencies, and configuration.
- Build an evidence-backed knowledge graph of components and relationships.
- Reconstruct setup environments and workflows using isolated execution.
- Distinguish declared behaviour, inferred behaviour, simulated behaviour, and observed runtime behaviour.
- Present the system in an interactive engineering workspace.
- Persist multiple analysed repositories in one local workspace and compare them.
- Export reports, graphs, manifests, evidence, and recommendations.

## Product shape

Traceforge is intended to ship as an **npm CLI that starts a local browser-based engineering workspace**. It is not initially a hosted SaaS product. The local workspace remains available while users add repositories, revisit prior analyses, rerun selected stages, and compare systems.

## Core principles

1. Evidence over confident-sounding guesses.
2. Safe inspection before execution.
3. Explicit boundaries between actual execution and simulation.
4. Preserve links back to original source and runtime evidence.
5. Treat repositories as systems, not collections of markdown files.
6. Keep analysis useful even when execution is impossible.
7. Make the workspace persistent and multi-repository.
8. Keep the core engine independent of the UI.

## Documentation map

- [Product vision](VISION.md)
- [Product requirements](PRODUCT_REQUIREMENTS.md)
- [Design principles](DESIGN_PRINCIPLES.md)
- [System architecture](architecture/SYSTEM_ARCHITECTURE.md)
- [Data model](architecture/DATA_MODEL.md)
- [Security architecture](architecture/SECURITY_ARCHITECTURE.md)
- [Agent architecture](architecture/AGENT_ARCHITECTURE.md)
- [Architectural decisions](decisions/ARCHITECTURAL_DECISIONS.md)
- [Implementation roadmap](implementation/IMPLEMENTATION_ROADMAP.md)
- [Testing strategy](implementation/TESTING_STRATEGY.md)
- [Workflows](workflows/)

## Development status

No implementation, execution capability, security guarantee, or integration should be considered available until it exists in code and is covered by tests. Specifications describe intended behaviour, not completed features.

## License

License selection is pending. Do not assume this project is open source under a particular license until a LICENSE file is added.
