# DiscoveryEngine

DiscoveryEngine is deterministic execution/orchestration operating on DiscoveryProjects.

## Responsibilities

- validate prerequisites;
- request/invoke Praxis Capabilities;
- select a Protocol under explicit deterministic policy or accept a selected Protocol;
- instantiate Runs;
- register status, failure, retry, Artifacts, Results, and provenance;
- update graph relations;
- manage Campaign execution;
- enforce configured approval gates;
- preserve execution history.

## Non-responsibilities

DiscoveryEngine does not inherently:

- invent Hypotheses through opaque LLM reasoning;
- silently reinterpret Evidence;
- certify Praxis Capabilities;
- erase contradictory history;
- make Decisions beyond configured authority.

If scientific judgment is required, it should request human and/or MOLI Agent input.
