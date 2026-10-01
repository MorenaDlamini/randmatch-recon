# Azure for recon, AWS for the ledger

- **Status:** proposed
- **Date:** 2026-10-01
- **Deciders:** Morena Dlamini

## Context and problem statement

The C#/.NET market in SA names Azure most (17 of 27 adverts; Azure DevOps 14). The product
fintechs that build payments (Ozow, Peach, Stitch, iKhokha, Luno) publish AWS stacks, and Ozow's is
ASP.NET Core, Postgres, ECS and Terraform. One cloud would prove half of that.

## Decision drivers

- Prove the Azure services the adverts name
- Prove the AWS stack the payment companies run
- Keep the split load-bearing, not decorative: each half is deployed where its audience runs it
- Cost: everything must be torn down by script

## Considered options

1. Recon on Azure, ledger on AWS
2. Everything on Azure
3. Everything on AWS

## Pros and cons of the options

- **Recon on Azure, ledger on AWS.** Good: Each half matches its audience; the cross-cloud call is a real integration to design. Bad: Two clouds to learn, secure and pay for.
- **Everything on Azure.** Good: One bill, one identity model. Bad: Nothing to show the AWS-first fintechs.
- **Everything on AWS.** Good: Matches the fintechs. Bad: Misses most of the .NET adverts.

## Decision outcome

**Proposed:** Recon on Azure, ledger on AWS, with tear-down scripts before the first deployment. Revisit if running costs exceed what a portfolio justifies.

This record moves to `accepted` when I've rewritten this section in my own words after the first
spike, and recorded what the spike changed.

## AI input

Drafted with Claude Code from the research notes in
[dotnet-ai-engineering/research](https://github.com/MorenaDlamini/dotnet-ai-engineering/tree/master/research) (2026-10-01).
The options and drivers came from that research. What was adopted: the framing above. What still
has to be done by me: confirm or reject the outcome after building the first slice, and replace
the "Proposed" paragraph with the decision as I'd defend it in an interview.
