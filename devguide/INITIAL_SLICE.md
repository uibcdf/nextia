# Initial DiscoveryProject slice

**Status:** implementation design proposal for [Nextia #1](https://github.com/uibcdf/nextia/issues/1). The shared Praxis–Nextia boundary belongs to [MOLI #28](https://github.com/uibcdf/moli/issues/28); the Sabueso historical-reference guarantee belongs to [MOLI #3](https://github.com/uibcdf/moli/issues/3). This document does not freeze a public API, schema, or storage engine.

## Architectural job

Nextia owns **project-specific scientific meaning and continuity**. It must be useful to a scientist operating Python/Jupyter directly, with no LLM and no mandatory Praxis execution. `DiscoveryProject` is state/history; `DiscoveryEngine` is deterministic action/orchestration. The ProjectGraph is the authoritative scientific graph. The MOLI ProjectRecord/EventLedger records cross-platform provenance; Recorda may instrument Nextia mutations but cannot decide what they mean.

## First slice: persistent scientific graph

The first local implementation should support:

1. A project identity, Focus and Goal, and contextual references to studied entities. No target, Candidate, Hypothesis, or Campaign is mandatory.
2. Independently identified **Question**, **Hypothesis**, **Observation**, **Evidence**, and **Decision** objects. Each has its epistemic role; do not create a generic `Claim` merely to avoid the distinction.
3. Typed relationships sufficient for `observation → opens question`, `hypothesis → addresses question`, `evidence → informs/supports/contradicts subject`, `decision → based on evidence`, and `new state → supersedes old state`. A relation must have valid endpoint types. Additional relation types should be introduced from use cases, not an unrestricted string graph.
4. Explicit operations for creating, linking, revising, challenging, rejecting, and superseding scientific objects. Operations check local referential integrity and required actor/rationale/review state. No operation silently converts a SourceAssertion or Result into Evidence.
5. Stable identity independent of Python object, process, path, or database row; explicit schema/revision metadata; historical inspection; and a durable local repository boundary. A current view may be mutable, but prior scientifically consequential states remain reconstructable.
6. External owner-issued references stored intact with owner/kind and historical pin where needed. A missing or unauthorized target does not delete the project relation or become a new scientific conclusion.

The initial local repository may use files or a database. Whichever implementation is chosen must reopen exactly the same graph, reject a partial invalid update without silently changing it, and expose earlier revisions. Event sourcing is **not** required; an EventLedger entry is not the semantic source of a Question or Evidence item. Storage is accessed behind a repository boundary so scientific operations do not depend on a directory layout.

## Proposed internal seams

These are responsibilities for the first implementation, not package names or final Python classes:

| Seam | Owns |
| --- | --- |
| Scientific model | Project framing, typed objects/relations, statuses, and validation of local scientific invariants. |
| Project operations | Explicit commands that create or revise graph meaning with actor, basis, and rationale; no implicit inference from external records. |
| Project repository | Atomic local persistence, schema/revision checks, historical reads, and export of structured state. |
| Reference boundary | Retention of opaque provider-issued references and explicit resolution outcomes through an injected resolver; no Sabueso/Praxis parser inside Nextia. |
| Provenance boundary | Consequential mutation metadata and correlation for MOLI/Recorda, without making a recorder the ProjectGraph database. |
| DiscoveryEngine | Initially thin: validates a requested project operation and its authority. Method selection, Run execution, scheduling, and recovery follow the shared execution decision. |

The component can be used on its own. MOLI may later supply Workspace context, reference resolvers, authorization and provenance sinks through interfaces/adapters; Nextia should not import a MOLI Agent or hard-code another component's storage path.

If a Nextia-owned object stores a physical measurement rather than citing an external Result, it must retain the value, unit, and scientific meaning; a bare number is insufficient under MOLI's quantity policy.

## Generic acceptance journeys

### A. From external statement to project decision

Create project `P` and Question `Q` about fictional protein `X`. Retain versioned knowledge reference `K1`. A scientist explicitly records why `K1` informs `Q`, creating Evidence `E1` with its own statement, limitations, actor and basis. A Decision `D1` may cite `E1`. A later provider revision or inability to resolve `K1` leaves the original reference, `E1`, and `D1` intact. This path has no required Run or Hypothesis.

### B. Exploratory observation

Reference a Result `R1` from a separate producer. A scientist explicitly creates Observation `O1` from `R1`, then opens Question `Q2` from `O1`. A Hypothesis may be added later. The Result remains authoritative at its producer; the Observation belongs to Nextia.

### Historical counterexamples

Two Evidence objects may disagree about the same Hypothesis. A Decision can be rejected or superseded without deleting its rationale. A failed attempt can remain referenced even if it produced no Result. Public tests use fictional content and no real pilot material.

A separate controlled exercise should use an authorized real scientific workflow to check usability. Only generalized findings belong in public issues and fixtures.

## Subsequent execution slice

Once MOLI #28 settles the authority of ExecutionPlan, Run, Result and Artifact references, add Campaign and execution relations. A Campaign is a project purpose/work scope, not a Praxis Protocol. Nextia may request/accept a Praxis method and track attempt lifecycle, but a producer's authoritative Result/Artifact remains externally owned. Retries get separate identities and statuses. The later engine can enforce approvals and deterministic protocol-selection policy without becoming an LLM planner.

## Decisions to prove before a stable API

- Minimal object/relation vocabulary and transition rules under both journeys; avoid a mandatory hypothesis-first or pharmacology-specific workflow.
- Revision/persistence strategy, including concurrent update detection, migrations, and historical views.
- ExecutionPlan/Run authority and how a project graph references provider-owned outputs (MOLI #28).
- Exact cross-component reference semantics and confidentiality-safe resolution (MOLI #3 for Sabueso).

Only after these are exercised should implementation names, serialized grammar, and a public API be treated as stable.
