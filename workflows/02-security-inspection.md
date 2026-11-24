# Workflow 02: Security Inspection

## Goal
Assess repository risks before any side-effecting execution.

## Steps
1. Scan the immutable source snapshot using safe static inspection.
2. Detect executable setup hooks, install scripts, shell commands, network access, credential access, dynamic code loading, obfuscation, and suspicious configuration.
3. Invoke the validated SkillSpector adapter when available and supported.
4. Preserve raw scanner output; normalize findings into Traceforge's schema.
5. Present score scale/direction and tool version only when verified.
6. Combine scanner output with Traceforge findings without hiding disagreements.
7. Apply execution policy: static-only, restricted execution, approval required, or blocked.
8. Record user decisions and policy overrides.

## Outputs
Security report, scanner metadata, findings, policy decision, unresolved risks.

## Important constraints
A favourable score is not a guarantee. Scanner unavailable is not equivalent to clean. Source reading is not execution. Do not invent scores or silently reinterpret the vendor's scale.

## Acceptance criteria
- Security inspection occurs before repository setup scripts run.
- Raw and normalized findings are both retained.
- Every finding links to evidence.
- Policy decisions are explainable and auditable.
