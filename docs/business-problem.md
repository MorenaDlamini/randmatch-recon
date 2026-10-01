# The business problem

## Who has it

- **The merchant** takes money in store (Yoco, iKhokha), online (Paystack, Peach, Payfast, Ozow)
  and by EFT or PayShap for invoices. They want to know that every sale was paid, and what it cost.
- **The bookkeeper** closes the month for many such merchants in Xero or Sage. They are the
  multiplier: one bookkeeper using a tool brings every client with them.
- **The finance manager** at a larger merchant who has to explain a short payout to the business.
- **The auditor**, who asks where any number came from.

## What happens today

1. Each provider pays a **net, batched deposit**. Yoco pays out daily after a cut-off
   ([Yoco](https://www.yoco.com/za/blog/when-will-i-get-my-money/)); Peach makes "one
   consolidated deposit" per business day
   ([Peach](https://support.peachpayments.com/support/solutions/articles/47001250592-understanding-your-peach-payments-settlements));
   Paystack splits payouts into batches
   ([Paystack](https://support.paystack.com/hc/en-us/articles/360012149479-When-will-I-receive-my-payouts)).
2. None of those deposits matches a sale. Fees are netted off, refunds and chargebacks are
   deducted, and funds can be held for review.
3. Each provider's accounting integration reconciles **only that provider**: Yoco's Xero app
   matches Yoco payouts ([Xero App Store](https://apps.xero.com/za/app/yoco)), and Paystack's
   covers invoice payments only ([Xero App Store](https://apps.xero.com/za/app/paystack)).
4. So the bookkeeper downloads each provider's export and the bank statement (CSV or OFX for most
   business accounts), and rebuilds the picture in Excel.

## Why it matters

- **It's slow.** At mid-market retailers, Ecentric cites "two and three weeks" to see the
  month-end position (vendor claim,
  [Bizcommunity](https://www.bizcommunity.com/article/automation-efficiency-and-accuracy-for-sa-retailers-its-time-for-reconassist-561290a)).
- **People already pay for it.** Stitch sells reconciliation "across methods and providers"
  ([Stitch](https://stitch.money/reconciliation)), and so do Transaction Junction and Ecentric,
  to enterprise.
- **Regulation is heading the same way.** The SARB's draft Authorisation Framework would require
  money remitters to "reconcile the funds paid into its clients' segregated bank account with a
  specific client transaction" (draft, May 2026).
- **When records don't agree, money goes missing.** The CFPB's case against Synapse describes
  records that didn't match its partner banks', and a shortfall of $60–90 million
  ([CFPB](https://www.consumerfinance.gov/enforcement/actions/synapse-financial-technologies-inc/)).

## What "solved" looks like

- Every payout from every provider is broken down into what it's made of, automatically, for
  most of them.
- Everything that doesn't match is in a queue, with a reason a bookkeeper can act on.
- Any number can be traced back to the rows it came from.
- The month closes from one place, not one spreadsheet per provider.

## Out of scope

- Moving money. randmatch reads what happened; it never pays, refunds or posts to a bank.
- Card data. No card numbers are handled.
- Replacing the accounting package. Journals are exported for review, not posted silently.

## Risks and unknowns

- **How big is the segment?** No survey counts SA merchants on two or more providers.
- **Will Xero's AI or a provider absorb this?** Xero's reconciliation agent is moving into the
  space; Stitch could move down-market.
- **Personal information.** Exports can include customer names. Process locally, strip on
  import, store nothing personal (POPIA).

## First validation step

Five conversations with South African bookkeepers who serve merchants on more than one provider:

1. Which providers do your clients use, and how many per client?
2. Walk me through last month's close for one of them. Where did the time go?
3. What do you do when a payout is short?
4. What would you need to trust a tool's match without checking it?
5. What would make you stop using it?

Notes go in `docs/discovery/` with names removed.

The research behind this page is in
[dotnet-ai-engineering/research](https://github.com/MorenaDlamini/dotnet-ai-engineering/tree/master/research), dated 2026-10-01.
