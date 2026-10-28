---
layout: article
title: "Who Owns Your ERP Data? Export, Retention and Exit Checklist"
description: "What ERP data ownership means in practice, which contract clauses protect you, which export formats to demand, and how to plan a vendor exit without losing history."
date: 2026-10-28
last_modified_at: 2026-10-28
answer: "You own your ERP data, but ownership is only useful if the contract and the software let you extract it. Check four clauses before signing: ownership, export format, retention after termination, and deletion. Then test a full export, including attachments and transaction history, before the contract starts."
category: guide
permalink: /guides/erp-data-ownership-and-exit/
categories:
  - Buying Guides
tags:
  - erp data ownership
  - erp exit
  - data portability
  - vendor lock-in
  - erp contract
author: B2B ERP Editorial Team
---

## Why ownership clauses are not enough

Most ERP contracts state that the customer owns its data. That sentence is necessary but not sufficient. Ownership means nothing if the vendor controls the only practical way to read the data, charges an extraction fee, or deletes the environment thirty days after termination.

Data portability has three parts: the legal right to the data, the technical ability to extract it, and the operational time to do so before access ends. Weaken any one part and the exit becomes expensive.

## What counts as your ERP data

Buyers often think of data as the customer and transaction tables. In practice, a usable exit needs more:

- Master data: customers, suppliers, items, bills of material, price lists, chart of accounts.
- Open transactions: orders, invoices, purchase orders, work orders, shipments.
- Historical transactions: posted journals, closed orders, inventory movements.
- Attachments: scanned invoices, contracts, drawings, quality certificates.
- Configuration: approval workflows, tax rules, posting logic, report definitions.
- Customisations: custom fields, scripts, integrations and their documentation.
- Audit trail: who changed what, and when.

The last four items are where exits fail. Transaction tables export cleanly. Attachments and configuration usually do not.

## Four contract clauses to check

### Ownership and licence scope

The contract should state that the customer owns all customer data, including derivatives such as reports and extracts. Check whether the vendor claims a licence to use aggregated or anonymised data and whether you can refuse it.

### Export format and method

Demand a named format, not a promise of "reasonable assistance". Prefer a documented, machine-readable format such as CSV or JSON, delivered through a documented API or a bulk export tool. Ask for the schema and the field definitions. A PDF report is not an export.

### Retention after termination

Ask how long data remains available after the contract ends and at what cost. A useful clause gives a defined read-only window long enough to complete a migration, plus a stated price for extensions. Thirty days is not enough for a mid-market ERP exit.

### Deletion and certification

The contract should require deletion after the retention window and a written certificate of destruction on request. Check whether backups are included and how long they persist.

## Test the export before you sign

Do not accept a data-export capability you have not seen. During the evaluation, ask the vendor to run a full export from a demonstration tenant and give you the files.

Test these points:

1. Can you export every table without a row limit?
2. Do attachments come out with usable filenames and a mapping to their parent record?
3. Does the export include custom fields and their definitions?
4. Are posting dates, currencies and exchange rates preserved?
5. Can you export the audit trail?
6. Is the export scriptable, so it can be repeated during the project?

If the vendor cannot demonstrate this in the sales cycle, assume it will be harder after signature.

## Plan the exit while you are implementing

The cheapest time to design an exit is during implementation, when the vendor still needs your reference and the project team still knows the data model.

- Write the data dictionary as part of the implementation, not as an afterthought.
- Keep integration definitions in your own repository.
- Store attachments in a way you could rebuild elsewhere.
- Record which reports are used for statutory or management reporting.
- Nominate an internal data owner who stays after the project ends.

These steps cost little during the project and save months at exit.

## The exit runbook

When you decide to leave, run the exit as a project with dates and owners:

1. Give contractual notice and confirm the retention window in writing.
2. Freeze the data model: record the version, schema and customisations.
3. Run a full export and store two copies in separate locations.
4. Validate row counts against the live system for every major table.
5. Export attachments and confirm they open after transfer.
6. Export the audit trail and archived reports.
7. Reconcile the final trial balance before access ends.
8. Obtain written confirmation of the deletion date.

Keep the validation evidence. If a dispute arises later, row-count reconciliation is the proof that the export was complete.

## Common exit failures

- Leaving the export to the last month of the contract.
- Discovering that attachments are stored by the vendor's document service, not the ERP.
- Losing custom field definitions, so the exported data has no meaning.
- Assuming backups are included in the retention clause when they are not.
- Forgetting that integrations stop working the day access ends.
- No internal owner who understands the data model after the partner leaves.

Each of these is preventable with a clause and a test during the sales cycle.

## Frequently Asked Questions

### Do we own the data if the vendor hosts the system?

Yes, in almost every commercial contract the customer owns its data and the vendor holds it as a processor. The practical question is whether you can extract it in a usable form, which is a contract and tooling question.

### What format should we demand?

A documented, machine-readable format delivered in bulk, with a schema. CSV or JSON plus an attachment manifest is usually enough. Avoid formats that only reproduce reports.

### Is a data escrow service worth it?

It helps when the vendor could fail or disappear. Escrow does not replace a tested export, because the escrow copy is often stale. Use escrow as a backstop, not as the exit plan.
