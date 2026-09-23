# Nextia

**Nextia is the Discovery Context component of the MOLI Platform.**

Nextia represents the persistent scientific state/history of investigations and provides deterministic execution/orchestration over that state. It is fully usable without an LLM.

The central separation is:

> **DiscoveryProject = state and history.**  
> **DiscoveryEngine = action and orchestration.**

## DiscoveryProject

A persistent, machine-readable, graph-shaped representation of an investigation, including framing, Questions, Hypotheses, Strategies, Campaigns, Runs/references, Artifacts, Results, Observations, Evidence, Candidates, Decisions, provenance, and history.

Scientific non-success is first-class: failed, partial, cancelled, incompatible, inconclusive, contradictory, rejected, and superseded states remain represented.

## DiscoveryEngine

A deterministic orchestration component that operates on DiscoveryProjects. It may validate prerequisites, request Praxis Capabilities, select/accept Protocols under explicit policy, instantiate Runs, register outputs/status/provenance, update graph relations, manage Campaign execution, and enforce approval gates.

DiscoveryEngine does not inherently invent hypotheses through opaque LLM reasoning or silently reinterpret Evidence.

## Status

This repository establishes the implementation home for Nextia. APIs, persistence technology, and event mechanisms are intentionally not frozen yet.

The normative conceptual definition is maintained in [MOLI Platform Architecture 1.0](https://github.com/uibcdf/moli/tree/main/architecture_1.0).
