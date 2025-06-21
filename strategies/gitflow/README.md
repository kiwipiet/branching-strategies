# Gitflow

A more structured approach, Gitflow defines specific branches for different purposes: main (or master) for production releases, develop for ongoing development, feature branches for new features, release branches for preparing new releases, and hotfix branches for urgent bug fixes in production.

## Main Branches

- **`main` (or `master`)**
  - Always contains **production-ready** code.
  - Tagged with release versions (e.g., `v1.0.0`).

- **`develop`**
  - Integration branch for all completed features.
  - Reflects the latest delivered development changes.

## Supporting Branches

### `feature/*`

- Branched from: `develop`
- Purpose: New features or enhancements
- Merged into: `develop`
- Deleted after merge

### `release/*`

- Branched from: `develop`
- Purpose: Final pre-release stabilization (e.g., version bumping, final testing)
- Merged into: `main` and `develop`
- Tagged with release version (on `main`)
- Deleted after merge

### `hotfix/*`

- Branched from: `main`
- Purpose: Urgent fixes in production
- Merged into: `main` and `develop`
- Tagged with patch version (on `main`)
- Deleted after merge

### `bugfix/*` (optional)

- Branched from: `develop` or `release/*`
- Purpose: Fix non-critical bugs
- Merged into: source branch

## GitFlow Workflow Summary

```text
develop     → feature/*
develop     → release/*
main        → hotfix/*
release/*   → main + develop
hotfix/*    → main + develop
```

## Pros

- Clear separation of concerns.
- Supports parallel development and multiple releases.
- Formalizes versioning and release cycles.

## Cons

- More complex than simpler models (e.g., trunk-based).
- Can be heavyweight for small teams or continuous deployment.

> Pro Tip: Use GitFlow extensions (e.g., git flow init) or GitHub workflows to automate parts of the process.