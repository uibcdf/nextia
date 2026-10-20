# Initial Implementation Questions

This is a temporary implementation checkpoint, not frozen architecture.

## Design pause — 2026-10-08

The first implementation design is paused until a real scientific project is
mature enough to expose concrete Discovery needs. The existing conceptual
boundaries remain the baseline; API, class structure, persistence, and integration
choices remain open.

During scientific work, retain concrete examples in the project's ordinary
records: Questions, Result interpretations, Decisions and their rationale,
contradictory findings, failed attempts and retries, and changes in direction.
No Nextia-specific recording format is required during this pause.

Resume when a real scientific trajectory needs to be preserved, inspected
historically, or repeated, and the limitations of the current tools can be
identified. Use that trajectory to define and test the smallest useful
DiscoveryProject/DiscoveryEngine loop, coordinating shared contracts with MOLI
and Praxis as needed. Keep confidential project content in its controlled
workspace.

## Questions to revisit when design resumes

Initial questions:

- minimal stable identity/reference model;
- serialization and schema-version strategy;
- graph representation and persistence boundary;
- immutable/history-preserving update model;
- minimal object set for a first real project;
- Run/Artifact/Result/Observation/Evidence separation;
- deterministic Engine command/request interface;
- Praxis Capability/Protocol references;
- approval-gate representation;
- failure/retry/cancellation semantics;
- provenance and snapshots;
- local-first persistence with a path to shared/remote services.

Avoid implementing every conceptual object at once. Use a real scientific project to test whether the model remains general.
