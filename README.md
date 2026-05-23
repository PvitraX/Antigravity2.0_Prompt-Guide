# 🚀 Antigravity 2.0 — Prompt Guide

> The community prompt guide for **Google Antigravity 2.0** — updated after Google I/O 2026.

[![Stars](https://img.shields.io/github/stars/yourusername/antigravity-prompt-guide?style=flat-square)](.)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen?style=flat-square)](./CONTRIBUTING.md)
[![Last Updated](https://img.shields.io/badge/updated-May%202026-blue?style=flat-square)](.)

---

## What is Antigravity 2.0?

Google Antigravity 2.0 is an **agent-first development platform** announced at Google I/O 2026. It's no longer just an IDE — it's a full multi-agent orchestration system with:

- 🖥️ **Desktop App** — visual agent orchestration, artifact review
- ⌨️ **Antigravity CLI** (`agy`) — terminal-first, replaces Gemini CLI
- 🧰 **Antigravity SDK** — programmatic agent workflows for CI/CD and products
- ☁️ **Managed Agents** — single API call, runs in Google's secure Linux sandbox
- ⚡ **Gemini 3.5 Flash** — 289 tokens/sec, 4x faster than GPT-5.5 and Claude Opus

The shift: **from single prompts → always-on multi-agent workflows.**

---

## 📁 Repo Structure

```
antigravity-prompt-guide/
├── prompts/
│   ├── cli/           # Terminal (agy) prompts and slash commands
│   ├── desktop/       # Desktop app agent orchestration prompts
│   ├── subagents/     # Parallel subagent prompt patterns
│   └── hooks/         # JSON hook configurations
├── examples/
│   ├── fullstack/     # Full app build prompts end-to-end
│   ├── refactor/      # Legacy codebase refactor prompts
│   └── research/      # Research + documentation agent prompts
├── tips/
│   └── cost-saving.md # How to avoid blowing your Ultra budget
└── CONTRIBUTING.md
```

---

## ⚡ Quick Start — 5 Prompts to Try Right Now

### 1. Scaffold a full-stack app in one shot
```
Build a full-stack SaaS boilerplate with:
- Next.js 15 frontend (App Router, TypeScript)
- Supabase for auth + database
- Stripe for payments
- Tailwind CSS + shadcn/ui
- Deploy config for Vercel

Create all files, set up env variables template, and write a setup README.
```

### 2. Parallel refactor with subagents
```
Refactor this codebase using 3 parallel subagents:
- Agent 1: Convert all callback-based handlers in /api to async/await
- Agent 2: Add TypeScript types to all untyped files in /lib
- Agent 3: Write unit tests for every function in /utils

Run them in parallel. Report when all three are complete.
```

### 3. Research + implement
```
Research the top 3 approaches for implementing real-time collaboration 
in a web app (like Google Docs). Compare: WebSockets, CRDTs, and 
Operational Transforms. Then implement the best option for our 
Next.js app in /src/collaboration. Include conflict resolution.
```

### 4. Debug + fix + test in one pass
```
Inspect the failing tests in /tests. For each failure:
1. Identify the root cause
2. Fix the underlying bug in the source
3. Update the test if the expected behavior was wrong
4. Run the test to confirm it passes

Do not skip any failing test. Report a summary when done.
```

### 5. CI/CD pipeline agent (scheduled)
```
Set up a scheduled daily agent that:
- Runs at 9am UTC every day
- Checks for dependency updates (npm outdated)
- Auto-patches minor/patch versions
- Runs the test suite
- Opens a PR if tests pass, or posts a Slack alert if they fail

Use the project's existing .env for credentials.
```

---

## 📂 Prompt Categories

| Category | Description | Link |
|----------|-------------|------|
| CLI Prompts | `agy` slash commands, terminal workflows | [→ prompts/cli](./prompts/cli/) |
| Desktop App | Visual orchestration, artifact review | [→ prompts/desktop](./prompts/desktop/) |
| Subagents | Parallel task splitting patterns | [→ prompts/subagents](./prompts/subagents/) |
| Hooks | JSON lifecycle hooks for agent control | [→ prompts/hooks](./prompts/hooks/) |
| Full-stack Examples | Complete app build prompts | [→ examples/fullstack](./examples/fullstack/) |
| Refactor Examples | Legacy code migration | [→ examples/refactor](./examples/refactor/) |
| Cost Saving Tips | Don't burn your Ultra credits | [→ tips/cost-saving.md](./tips/cost-saving.md/) |

---

## 🧠 The 4-Part Prompt Framework

Most people get mediocre results because they type one vague line. Use this structure:

```
[CONTEXT]  → What is the project, language, stack?
[GOAL]     → What exact output do you want?
[AGENTS]   → Should this be split across subagents? How many?
[CONSTRAINTS] → Budget, time, style, files to avoid touching?
```

**Example:**
```
CONTEXT: Next.js 15 e-commerce app, TypeScript, Postgres, deployed on Railway.
GOAL: Add a complete wishlist feature — DB schema, API routes, UI components, tests.
AGENTS: Use 2 subagents — one for backend (schema + API), one for frontend (UI + hooks).
CONSTRAINTS: Do not modify the existing /checkout flow. Keep components in /src/features/wishlist.
```

---

## 💡 Key Antigravity 2.0 Concepts

### Subagents
The orchestrator agent spawns specialized subagents for parallel subtasks. Each subagent gets its own focused context — no context pollution.

```
/agent refactor "Convert all callback-based handlers in @internal/api to use context.Context"
```

### JSON Hooks
Intercept and customize agent behavior at lifecycle stages — before a tool call, after file write, on error.

```json
{
  "hook": "before_file_write",
  "condition": "file.path.startsWith('/src/critical')",
  "action": "require_approval"
}
```

### Scheduled Tasks
Cron-style triggers that run agents automatically — daily digests, hourly health checks, monthly reports.

> ⚠️ **Design for idempotency.** Scheduled tasks can misfire and run twice. Always write them to handle duplicate runs safely.

### AGENTS.md
Drop an `AGENTS.md` file in your project root — Antigravity reads it as standing instructions for every agent session in that project.

---

## 💰 Cost Tips (Don't Burn Your Budget)

- **Cap subagent depth.** Dynamic subagents can spawn subagents. Without a cap, you'll blow through Ultra budget on recursive plans.
- **Cache aggressively.** Managed Agents bills per run, not per token. Repeated context = wasted money without caching.
- **Use scheduled tasks for idempotent work only.** State-dependent tasks need locking or they'll misfire.
- **Voice for short prompts, text for long specs.** Voice is faster for quick commands, worse for multi-line architecture specs.

Full cost guide → [tips/cost-saving.md](./tips/cost-saving.md)

---

## 🤝 Contributing

Got a prompt that works really well? Open a PR.

See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## 📬 Stay Updated

This repo is maintained by [@yourusername](https://x.com/yourusername) on X.  
Follow for daily Antigravity tips, prompt drops, and build threads.

---

*Not affiliated with Google. Community resource.*
