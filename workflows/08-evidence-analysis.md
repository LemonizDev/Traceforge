# Workflow 08: Evidence and Behaviour Analysis

## Goal
Compare declared and reconstructed behaviour with runtime evidence.

## Steps
1. Normalize source and runtime evidence.
2. Extract repository claims about capabilities and behaviour.
3. Link claims to supporting workflow components and execution events.
4. Identify observed outputs, missing expected outputs, failures, and deviations.
5. Detect broken references, unreachable components, contradictory instructions, dead scripts, and missing dependencies.
6. Assign claim status: declared, reconstructed, observed, simulated, contradicted, unverified, or blocked.
7. Preserve both supporting and contradicting evidence.

## Outputs
Claim register, verification matrix, anomalies, evidence-linked findings.

## Acceptance criteria
- A documented feature is not marked observed without runtime evidence.
- Simulated evidence cannot satisfy an actual-execution claim.
- Every important finding can be traced to its evidence.
