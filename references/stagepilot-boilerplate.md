# StagePilot boilerplate conventions

Apply this reference only when the user or repository documentation identifies the project as based on the StagePilot boilerplate.

## Architecture contract

- Preserve the established TanStack Start, Convex, and Better Auth architecture. Do not introduce PostgreSQL, Redis, Prisma, or Drizzle unless the user explicitly approves an architectural change.
- Before changing Convex code, read `convex/_generated/ai/guidelines.md` when it exists. Use the repository's generated Convex types and documented query, mutation, and action patterns.
- Persist shared application state through Convex and perform access decisions in trusted server-side functions. Derive the authenticated identity server-side; never trust a client-provided user ID, role, tenant, entitlement, or price.
- Keep AI integration behind the repository's central provider/model registry and normalized error handling when one exists. Do not expose provider credentials to the client.
- Add the Node runtime directive only to server action files that require Node-only APIs.

## Product-specific rules deliberately excluded

The StagePilot domain model is not boilerplate. Do not carry over its school subscription field, organization URL shape, in-app changelog implementation, product wording, or business-specific authorization rules. Define equivalents from the new application's own requirements.
