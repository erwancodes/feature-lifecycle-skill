# Feature Lifecycle

A reusable Codex skill for taking a repository feature from discovery through scoped implementation, validation, review, and an explicitly authorized release.

It is stack-agnostic by default. For repositories derived from the StagePilot boilerplate, it also preserves the reusable TanStack Start, Convex, and Better Auth conventions without carrying over StagePilot's product-specific rules.

## Install

Clone the repository into the local Codex skills directory:

```powershell
git clone https://github.com/erwancodes/feature-lifecycle-skill.git "$env:USERPROFILE\.codex\skills\feature-lifecycle"
```

Restart Codex or begin a new task, then invoke it with:

```text
$feature-lifecycle
```

## What it enforces

- Inspect and plan from the real repository before making risky changes.
- Preserve unrelated working-tree changes.
- Require explicit authorization for merges, deployments, releases, production data changes, and other external mutations.
- Validate and audit the final diff before review.
- Use StagePilot boilerplate architecture rules only when the project declares that lineage.

## License

[MIT](LICENSE)
