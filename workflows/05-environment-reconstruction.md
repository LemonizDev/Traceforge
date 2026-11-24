# Workflow 05: Environment Reconstruction

## Goal
Determine what is required to operate the repository without blindly running setup.

## Steps
1. Inspect manifests, lockfiles, runtime declarations, scripts, config, and documentation.
2. Detect OS, runtime, package manager, tools, services, environment variables, and network assumptions.
3. Distinguish declared dependencies from observed installed dependencies.
4. Produce a reproducible environment manifest.
5. Identify missing prerequisites and credential-dependent integrations.
6. Propose an isolated execution environment and explicit network/resource policy.
7. Prepare the environment only after policy approval.

## Outputs
Environment manifest, dependency tree, platform compatibility report, missing prerequisite list, setup plan, setup logs if approved.

## Acceptance criteria
- Environment requirements are inspectable before installation.
- Secrets are not copied into manifests or logs.
- Static analysis remains available when environment preparation is denied.
