# CLAUDE.md

Guidance for Claude Code (and any AI assistant) in this repository.

## The domain

Payout reconciliation for South African merchants who take payments through several providers. Part of randmatch:

| Repo | Role |
|---|---|
| [randmatch-recon](https://github.com/MorenaDlamini/randmatch-recon) | The product: ingestion, matching, the exceptions queue, the AI break-explainer |
| [randmatch-ledger](https://github.com/MorenaDlamini/randmatch-ledger) | The double-entry clearing ledger: postings, journal export, audit |
| [randmatch-sim](https://github.com/MorenaDlamini/randmatch-sim) | The simulator: provider exports, bank files and webhooks with planted breaks |

Glossary:
- **Payout:** a net, batched deposit from a provider.
- **Settlement export:** the provider's file explaining a payout.
- **Clearing account:** what a provider still owes a merchant.
- **Break:** anything that doesn't reconcile.
- **Planted break:** a break `randmatch-sim` created on purpose and recorded in its manifest.

## The learning rule

**Files under `src/Matching/` are written by me.** Review them, question them, suggest tests and edge
cases, but do not implement them. If I ask for the solution, give a hint or point to the doc
instead. Scaffolding, configuration, Dockerfiles, IaC, migrations and test data around that
core are fine to generate, and I'll read every line before it's committed.

## Agent roles

Use these roles explicitly and say which one you're acting as:

| Role | Does | Never |
|---|---|---|
| Spec reviewer | Challenges `specs/<feature>/spec.md` and `plan.md`: missing cases, untestable criteria, hidden assumptions | Writes the spec |
| Test writer | Proposes failing tests from the acceptance criteria, including property and concurrency tests | Weakens a test to make it pass |
| Code reviewer | Reviews the diff as a strict senior .NET engineer at a bank: what fails in production, and what would an interviewer ask | Approves its own generated code |
| Security scanner | Attacks the change: tenant escape, replayed webhook, forged signature, injection, secrets | Claims a vulnerability without a reproduction |

## Conventions

- **Money** is `decimal` in C# and `numeric`/`decimal` in the database, with currency. Never
  `double` or `float`.
- **Time** is UTC everywhere, as `DateTimeOffset`, with a `TimeProvider` in tests.
- **Every write that can be retried is idempotent**, and has a test proving it.
- **Every test file opens with a comment naming the risk it covers.**
- **No real merchant or customer data** anywhere: not in code, tests, prompts or issues.
- **A new package or service needs a decision record** in `docs/adr/`.

## Workflow

Issue, then a spec and plan merged in their own PR (`specs/README.md`), then an ADR if a decision
is involved, then small PRs that fill in the template's "AI involvement" section. See
`docs/ai-engineering/standards.md`.

Use plan mode before larger changes. Keep diffs small. Check library APIs against official docs.
