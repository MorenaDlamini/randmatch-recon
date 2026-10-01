# SQL Server for reconciliation

- **Status:** proposed
- **Date:** 2026-10-01
- **Deciders:** Morena Dlamini

## Context and problem statement

Reconciliation is set-based work: many-to-one matching across files, windowed comparisons over
value dates, and aged exception reporting. It needs a database whose query plans I can read and
tune, and it's the half of the system that .NET-heavy employers (banks, Ozow, the consultancies)
run on SQL Server.

## Decision drivers

- Matching is set-based and must be tunable, with plans I can explain
- SQL Server is named in 16 of 27 SA C#/.NET adverts read on 2026-10-01; Postgres in 2
- The ledger already uses Postgres, so this is a choice about the right engine per workload, not a default

## Considered options

1. SQL Server (Azure SQL when deployed)
2. Postgres, same as the ledger
3. A dataframe engine (DuckDB) for matching

## Pros and cons of the options

- **SQL Server (Azure SQL when deployed).** Good: Window functions, Query Store and execution plans are well understood; matches the .NET market; Azure SQL is a managed path. Bad: Licensing outside Azure; a second engine to run locally.
- **Postgres, same as the ledger.** Good: One engine; product fintechs favour it. Bad: Gives up the SQL Server depth the market asks for; nothing to compare.
- **A dataframe engine (DuckDB) for matching.** Good: Very fast for batch analytics. Bad: Not an OLTP store for the exceptions workflow; adds a third technology.

## Decision outcome

**Proposed:** SQL Server, on the grounds that the matching workload is set-based and the target market runs it. Revisit if the matching moves to a streaming design where a log-based store fits better.

This record moves to `accepted` when I've rewritten this section in my own words after the first
spike, and recorded what the spike changed.

## AI input

Drafted with Claude Code from the research notes in
[dotnet-ai-engineering/research](https://github.com/MorenaDlamini/dotnet-ai-engineering/tree/master/research) (2026-10-01).
The options and drivers came from that research. What was adopted: the framing above. What still
has to be done by me: confirm or reject the outcome after building the first slice, and replace
the "Proposed" paragraph with the decision as I'd defend it in an interview.
