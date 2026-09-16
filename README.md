# Feature Lifecycle

A reusable Codex skill for taking a repository feature from discovery through scoped implementation, validation, review, and an explicitly authorized release.

It is stack-agnostic by default. For repositories derived from the StagePilot boilerplate, it also preserves the reusable TanStack Start, Convex, and Better Auth conventions without carrying over StagePilot's product-specific rules.

## Install

Install it globally for Codex:

```powershell
npx skills add erwancodes/feature-lifecycle-skill --skill feature-lifecycle --global --agent codex --copy -y
```

Or use the interactive installer, which lets you choose the target agent and scope:

```powershell
npx skills add erwancodes/feature-lifecycle-skill
```

Begin a new task, then invoke it with:

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
