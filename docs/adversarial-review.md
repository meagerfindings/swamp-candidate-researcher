# Adversarial Review — candidate-research workspace

## Scope

This review covers the public repo and the three published extension packages:

- `@mgreten/swamp-candidate-researcher-colorado`
- `@mgreten/swamp-candidate-researcher-federal`
- `@mgreten/swamp-candidate-researcher-colorado-judge`

## Universal

- **Credentials & Secrets:** PASS — no API keys, passwords, or personal secrets are present in the tracked public source.
- **Logging Quality:** ISSUE FOUND — the core research flow is mostly helper-driven and does not yet emit structured entry/completion logs per method.
- **Error Handling:** PASS — fetches are guarded by timeouts and failures are converted into packet-level status instead of uncontrolled crashes.
- **Testing Completeness:** ISSUE FOUND — there are unit/privacy tests now, but no end-to-end smoke test that exercises a live source fetch and publish-path packaging together.
- **Idempotency & Resilience:** PASS — the models are read/collect/synthesize oriented and avoid destructive mutation.
- **API Contracts:** ISSUE FOUND — source enrichment is still heuristic for some providers; it should eventually be backed by source-specific parsers or fixtures for Ballotpedia, Colorado SOS, FEC, and Colorado judicial sources.
- **Resource Management:** PASS — fetch timeouts use `AbortController` and timers are cleared.
- **Published Surface Hygiene:** PASS — the public collective is `@mgreten`, the README is neutralized, and the repo-level privacy checks cover personal and viewpoint-specific strings.

## Models

- **Schema strictness:** PASS — model inputs are Zod objects and are explicit rather than loose passthrough shapes.
- **Lifetime & GC:** PASS — the core model declares resource lifetimes and garbage-collection policies.
- **CRUD completeness:** not applicable — these are research/briefing models, not CRUD lifecycle models.
- **Pre-flight checks:** not applicable — there are no destructive live mutations that need policy-gated preflight checks.
- **Instance names:** PASS — resource names are slugified from the subject to avoid collisions.
- **Data access:** PASS — the models use the Swamp resource API instead of direct repository mutation.
- **Version upgrades:** not applicable — this is a new model family without a migration chain yet.

## Follow-ups

1. Add structured logging around the `plan`, `collect`, and `synthesize` methods.
2. Add one live-source smoke test per major source family.
3. Replace heuristic source enrichment with source-specific parsers as the source adapters mature.
