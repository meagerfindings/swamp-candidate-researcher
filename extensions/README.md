# Swamp candidate-research monorepo

This repository is now organized as a **multi-extension workspace**.

## Publishable extensions

- `extensions/colorado-candidate/` — Colorado candidate research
- `extensions/federal-candidate/` — federal candidate research
- `extensions/colorado-judge/` — Colorado judge / retention research

## Shared internal code

The neutral shared implementation remains in the root `models/shared/` and `models/<jurisdiction>/` files for now.
The package entrypoints under `extensions/*/*.ts` simply re-export the canonical root models so we can publish
multiple extensions from one GitHub repo without duplicating logic.

## Publish examples

```sh
swamp extension fmt extensions/colorado-candidate/manifest.yaml --repo-dir . --check
swamp extension push extensions/colorado-candidate/manifest.yaml --dry-run
```

Repeat for the other manifests.
