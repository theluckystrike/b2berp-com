---
layout: article
title: "Running Two ERP Systems in Parallel: Scope, Exit Criteria and Cost"
description: "How to plan a parallel run between an old and a new ERP, which processes to reconcile, how to define exit criteria, and what the parallel period costs."
date: 2026-10-28
last_modified_at: 2026-10-28
answer: "A parallel run means the old and new ERP both process live transactions for a limited period. Run both through at least two full monthly closes, reconcile the general ledger and inventory to the same balances, and set written exit criteria before go-live. Parallel running is a control, not a migration strategy, and it doubles data entry."
category: guide
permalink: /guides/running-two-erp-systems-in-parallel/
categories:
  - Buying Guides
tags:
  - erp migration
  - parallel run
  - erp go live
  - cutover
  - data reconciliation
author: B2B ERP Editorial Team
---

## What a parallel run actually is

A parallel run means the legacy ERP and the new ERP both process real transactions for the same period. Staff enter the same invoice, shipment or production order twice, once in each system. At the end of the period, the two systems must produce the same financial and inventory results.

It is not the same as a test environment. A test environment uses copied data and simulated transactions. A parallel run uses live transactions and real money. That difference is why a parallel run is expensive and why it is worth planning carefully.

## Decide whether you need one

A parallel run buys certainty at the cost of effort. It suits organisations where an error would be material or where the migration touches several plants, warehouses or legal entities. It is less necessary when the scope is narrow, the data is clean and the legacy system can stay readable for reference.

Use these questions to decide:

- Does the business close its books monthly without tolerance for restatement?
- Does inventory valuation feed external reporting or lender covenants?
- Are several sites or legal entities cut over at once?
- Is the migration team's first ERP project for this company?
- Can the legacy system remain available in read-only mode after go-live?

Three or more yes answers usually justify a parallel period. If the answer is no to most, a strong reconciliation and a read-only archive may be enough.

## Set the scope before you start

Do not parallel everything. Duplicate effort is the main cost, so choose the processes where an error would hurt.

| Process | Parallel it when | Keep it single-run when |
|---------|------------------|------------------------|
| General ledger | Always, to prove trial balance | Never skip |
| Accounts payable and receivable | Cash flow and ageing matter | Volume is low and reversible |
| Inventory and costing | Valuation or traceability is regulated | Only non-stock items |
| Production orders | Work orders drive WIP and cost | Simple assembly with no WIP |
| Payroll | Rarely, because of statutory filing | Almost always |
| Sales orders and shipping | Revenue recognition is complex | Orders are simple and repeatable |

For each process in scope, name the owner, the source of truth during the run, and the report that proves the match.

## Define exit criteria in writing

The parallel run ends when the numbers agree, not when the calendar says so. Write exit criteria before go-live and get finance sign-off on them. Practical criteria look like this:

- The trial balance matches the legacy system at the end of two consecutive monthly closes, within a tolerance you define in advance.
- Inventory quantity and value reconcile by item and location at each close.
- Accounts receivable and payable ageing report differences are explained and cleared.
- No open incident remains that affects financial posting.
- The support team closes period-end tickets inside an agreed time.
- Department managers confirm they can run their reports without help.

If a criterion fails, extend the run. Do not enter a third month with unresolved differences and call it acceptance.

## Run the close twice, deliberately

The parallel period should cover at least two full monthly closes. The first close finds the defects. The second close proves the fixes hold. A single close shows that the systems matched once, often because the team worked around known gaps by hand.

During each close:

1. Freeze both systems at the same cut-off time.
2. Run the same reports from both systems.
3. Compare at the most granular level available, ideally by account and by item.
4. Record every difference with an owner and a resolution date.
5. Review unresolved differences with the controller before the next period opens.

Keep a reconciliation log. It becomes the evidence that the new system is trustworthy and the basis for retiring the old one.

## Staff the period realistically

Parallel running doubles transaction entry for the people who do the work. The same invoice clerk, warehouse operator or production planner now has two queues. Do not assume the team can absorb this without relief.

Plan for:

- Temporary data-entry support in the highest-volume processes.
- A daily reconciliation stand-up during the first two weeks of each close.
- A named owner for each process, with authority to stop the run.
- A defect log that the implementation partner reviews each day.
- Overtime or backfill budget approved before the run starts.

If the team cannot sustain the double entry, shorten the scope rather than let reconciliations slip. A partial parallel run that is completed is worth more than a full one that is abandoned in week three.

## Understand the cost

The cost of a parallel run has four parts: duplicate transaction entry, duplicate infrastructure and licences, reconciliation effort, and delayed decommissioning of the legacy system. Vendors often charge for the legacy system during the overlap, and some charge for extra environments in the new system.

Add these lines to the project budget before the run begins. A parallel period that is not budgeted becomes a surprise in the first month-end, which is the worst possible time to ask for money.

## Close the run properly

When the exit criteria are met, record the decision and stop the duplicate entry on a fixed date. Then:

- Switch the legacy system to read-only and remove write access.
- Archive the final reconciliation and the sign-off.
- Cancel duplicate licences and infrastructure.
- Schedule deletion of legacy data according to your retention policy.
- Brief users on where to find history.

A parallel run that never formally ends keeps costing money and keeps two versions of the truth alive.

## Frequently Asked Questions

### How long should a parallel run last?

Long enough to cover at least two monthly closes and any quarterly process in scope. The duration is set by the number of closes needed to prove the numbers match, not by a fixed number of weeks.

### Do we need to parallel payroll?

Usually not. Payroll is statutory, repeatable and expensive to duplicate. Run payroll in one system, verify with a test calculation, and keep the legacy records readable.

### Can we parallel only the general ledger?

Yes, and many mid-market projects do. Parallel the ledger and the inventory valuation, then reconcile subledgers by report rather than by duplicate entry. This keeps the control benefit while reducing data-entry load.
