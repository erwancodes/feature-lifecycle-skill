---
name: feature-lifecycle
description: "Deliver a repository feature safely from code-grounded discovery through scoped implementation, validation, review, and an explicitly authorized release. Use for feature work that may involve planning, coding, auditing, commits, pull requests, or releases; adapt to the repository's stack and conventions."
---

# Feature lifecycle

Take a feature through clear decision gates. Preserve the user's scope and repository conventions; this skill supplies a delivery discipline, not a technology or product architecture.

If the repository is explicitly derived from the StagePilot boilerplate, read [the boilerplate conventions](references/stagepilot-boilerplate.md) before planning or coding. Those conventions are conditional: do not impose them on unrelated repositories.

## 1. Inspect and frame

Before proposing a solution:

- Read repository instructions and the files they explicitly require.
- Inspect the working tree, current branch, relevant implementation paths, tests, scripts, existing patterns, and target integration points.
- Treat unrelated working-tree changes as user-owned. Do not reset, clean, checkout, overwrite, stage, or move them.
- Identify external systems and release dependencies (for example: database, auth, payment provider, CI/CD, hosting, feature flags). Verify access and target environment before promising an external result.

For work that changes behavior or carries meaningful risk, give a concise, code-grounded plan before editing. Include the current flow, affected files, data and authorization implications, compatibility or migration risk, validation, rollback, and implementation order. Ask only questions that materially change the approach, then wait for explicit scope approval before changing files.

If the user has already explicitly approved a detailed plan, confirm it still matches the repository state and proceed within that scope.

## 2. Implement deliberately

- Use an existing feature branch when appropriate; otherwise create `codex/<short-feature-slug>` from the user's current branch only after scope approval. Do not disrupt unrelated user work.
- Make the smallest coherent change that satisfies the approved outcome. Reuse project conventions and dependencies before adding abstractions or infrastructure.
- Apply authorization and validation on the server or trusted boundary. Never rely on client-supplied identity, role, tenant, entitlement, or price for access control.
- Keep credentials, tokens, cookies, private keys, and production secrets out of source, examples, commits, logs, and pull requests. Use the repository's approved environment/configuration mechanism.
- Update generated artifacts only through the repository's documented generator, and include tests where the project has an applicable test convention.

## 3. Validate and audit the final diff

Run the narrowest relevant checks first, then the repository's broader checks when justified. Typical evidence includes formatting/diff checks, typechecking, focused tests, the full test suite, build, and feature-specific manual or runtime verification. Never report an unrun command or inaccessible environment as passed.

Review the final diff as well as the checks. Classify actionable findings:

- **P0** — security, data loss, release blocker, or broken critical path.
- **P1** — major regression or missing authorization, validation, or compatibility handling.
- **P2** — significant correctness, usability, accessibility, or maintainability concern.
- **P3** — minor polish or follow-up.

At minimum, consider authorization and isolation, secret exposure, schema and migration safety, error/loading/empty states, retries and idempotency where relevant, user-visible accessibility, generated files, deployment configuration, and test coverage. Resolve P0/P1 issues before asking for review or releasing.

## 4. Commit, pull request, and release boundaries

When the user requests a commit or pull request:

1. Stage only files in the approved feature scope; leave unrelated changes untouched.
2. Create a concise, accurate conventional commit when that is the repository convention.
3. Push the feature branch and open a pull request against the intended base branch. Describe the behavior, validation evidence, audit findings, configuration or migration notes, and any review points.
4. Do not merge, delete branches, deploy, publish a release, alter production data, or change paid/external services unless the user explicitly authorizes that exact action.

Pause after a PR is ready for user review. Address approved review feedback within scope, revalidate, and update the PR.

For an explicitly authorized release, first reconcile version sources, tags, and changelog conventions. Follow the repository's versioning and release process, document user-visible and migration/configuration changes, rerun relevant validation, and report the exact deployment target and evidence.

## Communication contract

Keep updates short and evidence-based. At each gate say what was inspected, what changed, what passed, what remains uncertain or blocked, and which explicit approval is required next. The handoff should identify the branch, commits/PR when created, validation and audit result, release/deployment status, and unrelated dirty files left untouched.
