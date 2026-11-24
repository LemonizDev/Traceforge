# Workflow 07: Controlled Workflow Execution

## Goal
Execute selected workflows in a disposable, observable environment when policy permits.

## Preconditions
Completed acquisition and security inspection, explicit execution plan, compatible isolated backend, and required user approvals.

## Steps
1. Select a reconstructed workflow and define expected inputs/outputs.
2. Resolve execution policy and required approvals.
3. Prepare disposable environment with least privilege.
4. Apply network, filesystem, process, CPU, memory, and time limits.
5. Execute planned steps using safe process invocation.
6. Capture process output, tool events, filesystem changes, policy events, exit codes, and artifacts.
7. Tear down environment and verify cleanup.
8. Mark each step executed, simulated, partially executed, failed, blocked, or not executable.

## Outputs
Execution session, event stream, logs, artifacts, environment metadata, deviations, cleanup report.

## Acceptance criteria
- No execution occurs before policy gates pass.
- Actual and simulated events are distinguishable.
- Cancellation and timeout terminate child processes.
- Execution failure does not erase static analysis results.
