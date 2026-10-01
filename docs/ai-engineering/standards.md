# AI engineering standards

How AI is used in this repository, and how its output is checked. The point isn't to use less AI.
It's to be able to show, for any line, who decided it and what proved it.

## What AI may do

- Draft acceptance criteria, edge cases, test data and documentation.
- Propose two or three design options with their failure modes.
- Scaffold projects, configuration, IaC, Dockerfiles, migrations and pipelines.
- Review diffs, attack designs, and propose hypotheses during an incident.

## What AI may not do

- Write the core logic named in `CLAUDE.md`.
- Make a decision. ADRs record what it proposed; the Decision paragraph is written by me.
- See real merchant or customer data. Prompts use synthetic data from `randmatch-sim`.
- Merge anything. Every change goes through a PR I've read line by line.

## Review rules

1. **Every accepted AI review finding needs a failing test or a stated reason.**
2. **Every rejected finding gets one line saying why.**
3. **Claims about a library, a cloud limit or an API are checked against official docs**, and the
   doc is linked in the PR.
4. **Code I can't explain line by line doesn't get committed.**
5. **Tests that survive mutation testing are rewritten**, whoever wrote them.

## Disclosure

The PR template's "AI involvement" section is filled in on every PR: tools used, what was
generated and what was hand-written, and the triage of AI review findings.

## Measurement

`docs/ai-engineering/metrics.md` records, per PR, time spent, rework, and defects caught by tests
in AI-generated code. It's self-reported, labelled as such, and kept honest rather than
impressive.
