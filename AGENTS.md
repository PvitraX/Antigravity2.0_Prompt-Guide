# AGENTS.md Template

> Drop this file in your project root. Antigravity reads it as standing instructions for every agent session in that project.
> Customize the sections below for your project.

---

```markdown
# Project: [Your Project Name]

## Stack
- Frontend: Next.js 15, TypeScript, Tailwind CSS, shadcn/ui
- Backend: Node.js, Hono, Drizzle ORM
- Database: PostgreSQL (Supabase)
- Auth: Supabase Auth (JWT)
- Deployment: Vercel (frontend), Railway (backend)

## Key Directories
- /src/app — Next.js App Router pages
- /src/components — Reusable UI components
- /src/lib — Shared utilities and helpers
- /src/features — Feature-specific modules (keep features self-contained)
- /api — Backend Hono routes
- /db — Drizzle schema and migrations
- /tests — All test files (mirror src/ structure)

## Coding Standards
- TypeScript strict mode. No `any` types.
- All components are functional. No class components.
- Use Zod for all input validation (API routes and forms).
- Error responses always follow: `{ error: string, code?: string }`
- Never hardcode secrets. Use environment variables from .env.

## Do Not Touch
- /src/app/(auth)/ — Auth flow is finalized. Do not modify.
- .env.production — Never write to production env files.
- /db/migrations/ — Never edit existing migration files. Create new ones.

## Testing Requirements
- Every new API route must have integration tests.
- Every new React hook must have unit tests.
- Run `npm test` before reporting a task complete.
- If tests fail, fix them before finishing.

## Subagent Rules
- Maximum subagent depth: 2
- Maximum parallel subagents: 5
- Always report a summary of files changed when done.

## Style Guide
- Components: PascalCase
- Utilities/hooks: camelCase
- Files: kebab-case
- Database tables: snake_case
- Use named exports for components (not default exports, except pages).

## Definition of Done
A task is complete when:
1. Feature works as described
2. TypeScript compiles with no errors
3. Tests pass
4. No console.log statements left in code
5. New env vars added to .env.example
```
