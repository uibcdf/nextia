# Initial Implementation Questions

This is a temporary implementation checkpoint, not frozen architecture.

Start by proving the smallest useful DiscoveryProject/DiscoveryEngine loop.

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
