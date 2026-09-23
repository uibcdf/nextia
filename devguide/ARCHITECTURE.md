# Nextia Architecture

## Mission

Represent and execute structured scientific discovery while preserving scientific history, provenance, contradiction, failure, and human authority.

## Two core responsibilities

```text
Nextia
├── DiscoveryProject
│      persistent state / graph / history
│
└── DiscoveryEngine
       deterministic action / orchestration
```

### DiscoveryProject

Owns persistent project state and relationships among framing, reasoning, execution context, outputs, design space, and governance objects.

Objects should be independently identifiable and related by stable references.

### DiscoveryEngine

Operates on DiscoveryProjects. It validates prerequisites, invokes Praxis Capabilities/Protocols, instantiates Runs, records status/results/provenance, manages Campaign execution, and enforces configured approval gates.

## Graph-shaped science

Nextia must not require a single hypothesis-first sequence. Valid scientific paths may start from Questions, Observations, Evidence, Campaigns, or other project objects.

## Historical integrity

Scientifically meaningful previous states are not silently overwritten. Contradiction, rejection, supersession, and failure are information.

## Boundaries

Nextia owns Discovery context, not external molecular knowledge (Sabueso), reusable methodology (Praxis), modeling APIs (MolSysSuite), or open-ended AI reasoning (MOLI Agent).
