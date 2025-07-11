# Feature Branching

This strategy involves creating separate branches for each new feature or bug fix. This allows developers to work on different features independently, without affecting the main codebase, and then merge their changes back in through pull requests after testing and review.

```mermaid
gitGraph
   checkout main
   commit id: "Initial commit"
   commit id: "Production ready code"
   branch hotfix/1234
   checkout hotfix/1234
   commit id: "Minor prod fix"
   checkout main
   branch feature/login-page
   checkout feature/login-page
   commit id: "Build login form"
   commit id: "Add validation logic"
   checkout main
   merge hotfix/1234 tag: "PR merged"
   checkout feature/login-page
   merge main tag: "PR merged"
   commit id: "Post-merge changes"
```

## Key Concepts

- **Branch Naming:**
  - Use clear, consistent names:
    - `feature/login-form`
    - `bugfix/null-ref`
    - `chore/update-readme`

- **Branch Source:**
  - Typically branched from:
    - `main` (trunk-based)
    - or `dev` (if used as an integration branch)

- **Merging:**
  - Merged via Pull Request (PR) after completion and testing.
  - PRs include code review, automated tests, and CI checks.

- **Lifecycle:**
  - Branches should be short-lived.
  - Deleted after merge.

## Benefits

- **Isolation:** Develop features without impacting production code.
- **Parallel Development:** Teams can work on multiple tasks simultaneously.
- **Safe Integration:** PRs and CI pipelines help catch issues before merging.

## Risks

- **Long-lived branches** can cause:
  - Merge conflicts
  - Integration drift

- **Delayed feedback** if CI/CD is not run frequently.

---

## Recommended Practices

- Keep branches small and focused.
- Merge into `main` early and often.
- Use feature flags to integrate incomplete features safely.

---

> Pro Tip: Use PR templates and enforce CI checks to ensure high code quality.
