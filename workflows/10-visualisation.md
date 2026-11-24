# Workflow 10: Interactive Visualisation

## Goal
Make repository architecture and behaviour explorable from one persistent workspace.

## Main areas
- Repository Explorer (left).
- Central Visual Workspace.
- Component Inspector (right).
- Execution Console (bottom).
- Intelligence overview.

## Visual modes
Architecture, Workflow, Dependencies, Agent Network, Instruction Map, Execution Trace.

## Interaction requirements
Search, filters, zoom/pan, expand/collapse, tabs, saved layouts, full-screen graph, panel resizing/hiding, source navigation, evidence navigation, annotations, and grouping.

## Behaviour
Selecting a graph node opens its inspector and source evidence. Selecting a source reference highlights the corresponding graph component. Graph nodes represent discovered data; they do not execute workflows.

## Acceptance criteria
- Every displayed node/edge can be inspected.
- Source navigation works bidirectionally.
- User layouts and annotations persist separately from analysis facts.
- Large graphs support filtering and progressive expansion.
