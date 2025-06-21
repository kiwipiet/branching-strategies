# Release Flow

The release flow branching strategy is a Git-based workflow designed to balance fast feature development with predictable and stable releases. It’s commonly used in enterprise environments and is a refined version of the trunk-based development model with long-term support branches.

Here's a summary of the key concepts:

## Main Branches

- **`main` (or `master`)**
  - Contains the latest production-ready code.
  - All releases are built from this branch.
  - Always stable.

- **`release/*`**
  - Created from `main` when preparing a release.
  - Used for stabilization, bug fixes, and hardening.
  - Example: `release/2025.06`, `release/v1.0`.

- **`dev` or `develop`** (optional)
  - Used for staging features before merging into `main`.
  - Can be skipped if feature branches merge directly into `main`.

## Supporting Branches

- **`feature/*`**
  - For individual features or stories.
  - Branched from `main` (or `dev`) and merged back after completion.
  - Deleted after merging.

- **`hotfix/*`**
  - For urgent production fixes.
  - Branched from `main`, merged back into both `main` and `release/*`.

- **`bugfix/*`**
  - For non-critical bugs during release hardening.
  - Branched from a `release/*` branch.

## Merge Flow

```text
feature/*     → main (or dev)
main          → release/*
hotfix/*      → main → release/*
release/*     → main (if applicable)
```

## CI/CD Considerations

- CI runs on all branches.
- Releases are deployed from release/* or main.
- Feature branches use PR validation (tests, linting, reviews).

## Benefits

- Stability: Keeps production code isolated from active development.
- Flexibility: Supports multiple active releases.
- Traceability: Clear audit trail of changes and fixes.
