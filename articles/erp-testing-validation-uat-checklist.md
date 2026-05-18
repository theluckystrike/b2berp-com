---
layout: article
title: "ERP Testing and Validation: Complete UAT Checklist for Go-Live"
description: "Comprehensive ERP testing guide covering unit testing, integration testing, UAT scenarios, data migration validation, performance testing, and go/no-go criteria for a successful go-live."
date: 2026-05-18
author: B2B ERP Editorial Team
category: guide
categories: [Implementation]
tags: [erp testing, uat checklist, erp go-live, data migration validation, integration testing, performance testing, erp implementation, user acceptance testing]
permalink: /guides/erp-testing-validation-uat-checklist/
---

ERP implementations fail at a staggering rate. Industry analysts consistently place the failure rate between 55% and 75%, and inadequate testing is cited as a root cause in the majority of post-mortems. Organizations spend months on requirements gathering and configuration, then compress the testing phase to meet an arbitrary go-live date. The result is a production system riddled with defects that erode user trust and corrupt data.

Testing an ERP system is fundamentally different from testing a custom application. You are validating that a configurable platform, integrated with your existing systems, populated with your migrated data, and operated by your specific users, will support your actual business processes without failure. This guide covers the full testing lifecycle with actionable checklists at each phase.

## The ERP Testing Pyramid

ERP testing follows a layered approach where each phase builds on the confidence established by the previous one. Skipping layers creates compounding risk.

1. **Unit Testing** -- validates individual configuration elements in isolation (pricing rules, workflow steps, tax formulas)
2. **Integration Testing** -- validates that configured modules communicate correctly across end-to-end business processes
3. **User Acceptance Testing (UAT)** -- puts real business users in front of the system with realistic scenarios mirroring daily work
4. **Data Migration Validation** -- ensures legacy data has been correctly extracted, transformed, and loaded
5. **Performance Testing** -- validates response time and throughput under realistic and peak load conditions
6. **Go/No-Go Decision** -- synthesizes results from all phases into a structured decision framework

## Phase 1: Unit Testing

Unit testing in an ERP context means validating individual configuration elements before combining them into end-to-end processes. This phase is typically led by the implementation team, not business users.

### Unit Testing Checklist

- [ ] **Master data configuration**: Verify chart of accounts, cost centers, profit centers, and organizational hierarchies match approved design documents
- [ ] **User roles and permissions**: Confirm each role grants exactly the access specified in the security matrix. Test both positive access (can perform allowed actions) and negative access (cannot perform restricted actions)
- [ ] **Workflow rules**: Test each approval workflow in isolation. Verify routing logic, escalation timers, delegation rules, and rejection paths
- [ ] **Pricing and discount rules**: Validate every pricing condition, discount tier, and surcharge calculation against documented business rules
- [ ] **Tax configuration**: Test tax determination for every jurisdiction and product/service combination in scope. Cross-reference with tax counsel signoff
- [ ] **Number ranges and sequences**: Confirm document numbering for purchase orders, sales orders, invoices, and journal entries follows the approved scheme with no gaps or collisions
- [ ] **Custom fields and validations**: Verify that every custom field enforces its intended data type, length, required/optional status, and default value
- [ ] **Output formatting**: Check print layouts, PDF generation, and email templates for all document types against approved designs
- [ ] **Alerts and notifications**: Trigger each configured alert and confirm recipients, content, and delivery channel

The most expensive unit testing mistakes involve security and tax. A role that inadvertently grants posting access to the general ledger will not surface until an unauthorized user creates journal entries in production. A tax rule that miscalculates by fractions of a percent will generate audit exposure that compounds with every transaction. Test these exhaustively.

## Phase 2: Integration Testing

Integration testing validates the handoffs between modules. In an ERP system, virtually every business process spans multiple modules, and the integration points are where most defects hide.

### Integration Testing Checklist

- [ ] **Order-to-cash (O2C)**: Sales quote through delivery, invoice, payment, and revenue recognition. Verify financial postings at each stage
- [ ] **Procure-to-pay (P2P)**: Requisition through PO, goods receipt, invoice verification, and payment. Test three-way matching and exception handling
- [ ] **Plan-to-produce (manufacturing)**: Demand planning through production order, material consumption, finished goods receipt, and cost settlement. Validate BOM explosion and routing
- [ ] **Hire-to-retire (HR/payroll)**: Onboarding through payroll processing, benefit deductions, tax withholding, and disbursement
- [ ] **Record-to-report (finance)**: Journal entries through period-end close to financial statements. Test intercompany eliminations and currency revaluation
- [ ] **Inventory movements**: Test all movement types (receipts, issues, transfers, returns, scrap, cycle counts) and verify each creates the correct financial posting
- [ ] **Cross-module triggers**: Verify that events in one module reliably trigger actions in dependent modules and handle edge cases
- [ ] **EDI and external interfaces**: Test every inbound and outbound interchange with trading partners including error recovery
- [ ] **API integrations**: For every third-party integration (CRM, WMS, ecommerce, banking), test the full round-trip
- [ ] **Batch job sequences**: Validate that scheduled batch jobs execute in correct order and handle failures gracefully

Always run integration tests against a dedicated environment with a full copy of migrated data, not a configuration sandbox with dummy data. Document every test with input data, expected results, actual results, and pass/fail status.

## Phase 3: User Acceptance Testing (UAT)

UAT is the business's opportunity to validate that the system supports their operations. It should be structured, time-boxed, and staffed with the people who will actually use the system daily, not project team members acting as proxies.

### UAT Checklist

- [ ] **Environment readiness**: UAT environment is provisioned with production-representative data, all integrations are connected, and user accounts are configured with production-equivalent roles
- [ ] **Scenario coverage**: Every business process in scope has at least one happy-path scenario, one exception scenario, and one edge case
- [ ] **User assignment**: Each scenario is assigned to a named business user, not to a project team member. Users have received training on the new system before UAT begins
- [ ] **Day-in-the-life scripts**: Create full-day scripts for each major role (AP clerk, warehouse manager, production planner, controller) that chain multiple scenarios in realistic sequence
- [ ] **Period-end scenarios**: Test month-end close, quarter-end close, and year-end close processes including all reconciliation steps and report generation
- [ ] **Exception handling**: Test what happens when things go wrong. Credit hold on a rush order. Partial delivery. Short payment. Returned goods. Vendor invoice mismatch. Production scrap above threshold
- [ ] **Reporting validation**: Users verify that every report they need for daily operations produces correct, complete, and timely results
- [ ] **Parallel run (optional)**: For high-risk processes like payroll and financial reporting, run the old and new systems in parallel for one or two cycles and reconcile outputs
- [ ] **Defect tracking and triage**: Every UAT defect is logged in a tracking system with severity (critical, major, minor, cosmetic), assigned to an owner, and triaged daily
- [ ] **Signoff protocol**: Each business process owner formally signs off that their processes are validated and ready for production. Verbal approval is not sufficient

### UAT Severity Definitions

| Severity | Definition | Go-Live Impact |
|----------|-----------|----------------|
| **Critical** | Core business process cannot execute (e.g., orders cannot be invoiced) | Blocks go-live |
| **Major** | Process works but requires unsustainable workaround | Requires documented workaround + fix date |
| **Minor** | Usability issue, no functional impact (e.g., unsorted dropdown) | Does not block |
| **Cosmetic** | Visual/formatting issue only | Does not block |

## Phase 4: Data Migration Validation

Data migration is consistently the most underestimated risk in ERP implementations. The complexity lies in reconciling decades of inconsistent data, mapping legacy structures to new structures, and ensuring referential integrity across millions of records.

### Data Migration Validation Checklist

- [ ] **Record count reconciliation**: Total records in source equals total records in target plus documented exclusions. Perform count reconciliation for every entity type: customers, vendors, items, BOMs, open orders, GL balances
- [ ] **Financial balance reconciliation**: Trial balance in the new system matches the audited trial balance from the legacy system to the penny. Any variance must be explained and approved by the controller
- [ ] **Open document migration**: All open purchase orders, sales orders, and production orders are migrated with correct statuses, quantities, and pricing
- [ ] **Historical data completeness**: If historical transactions are migrated, verify period-over-period totals match source system reports
- [ ] **Master data quality**: Spot-check at least 5% of migrated master data records for field-level accuracy. Pay special attention to addresses, tax IDs, bank details, and pricing
- [ ] **Referential integrity**: Every foreign key relationship is valid. No orphaned records. No customer orders referencing nonexistent customers. No BOM components referencing nonexistent items
- [ ] **Character encoding and special characters**: Verify that names, descriptions, and addresses with non-ASCII characters (accents, umlauts, CJK characters) migrated correctly
- [ ] **Attachment and document migration**: If files and attachments are in scope, verify a sample can be opened and are linked to the correct parent records
- [ ] **Cutover rehearsal**: Perform at least two full cutover rehearsals using the exact same scripts, tools, and sequence that will be used during the actual cutover. Time every step
- [ ] **Rollback plan**: Document and test the procedure to roll back data migration if a critical defect is discovered post-cutover. Verify the rollback can be completed within the agreed time window

The most dangerous migration defects are silent ones. A customer credit limit that migrates as zero will block every order. An item cost with an incorrect decimal place will corrupt every production order's financials. These pass automated checks because they are structurally correct. Only business users reviewing actual records catch them.

## Phase 5: Performance Testing

Performance testing validates that the system meets response time and throughput requirements under realistic conditions. A system that performs adequately with five concurrent users during testing may become unusable with 500.

### Performance Testing Checklist

- [ ] **Baseline response times**: Measure and document response times for the 20 most frequently used transactions under single-user conditions. These become the baseline for load testing comparison
- [ ] **Concurrent user load testing**: Simulate expected concurrent users with a realistic transaction mix. Target: 95th percentile response time under 3 seconds
- [ ] **Peak load testing**: Simulate peak conditions (month-end close, holiday order volume, MRP during business hours)
- [ ] **Stress testing**: Push beyond expected peak to identify the breaking point and whether degradation is graceful or catastrophic
- [ ] **Batch processing windows**: Verify that all batch jobs (MRP, financial postings, data warehouse extracts) complete within their scheduled windows. Time each job under full data volume
- [ ] **Report generation times**: Measure execution time for the 10 most complex reports under concurrent load. Reports that take 45 seconds during testing may take 15 minutes in production
- [ ] **Integration throughput**: Verify that EDI, API, and file-based integrations can process the expected daily volume within acceptable time windows. Test burst scenarios where a backlog must be processed
- [ ] **Database growth projection**: Estimate database size after 12, 24, and 36 months of production use. Verify that performance remains acceptable at projected data volumes
- [ ] **Network latency (multi-site)**: For organizations with multiple locations, test system performance from every site. Remote offices with high-latency connections may have unacceptable response times
- [ ] **Failover and recovery**: Test the disaster recovery procedure. Measure recovery time objective (RTO) and verify it meets the business requirement

Cloud ERP vendors quote performance benchmarks measured under ideal conditions. Your performance will differ because your data volume, customization complexity, and integration load are unique. Never accept vendor benchmarks as a substitute for testing with your actual data and usage patterns.

## Phase 6: Go/No-Go Decision Framework

The go/no-go decision must be based on objective criteria defined before testing begins, not on political pressure to meet a date.

### Go/No-Go Criteria Checklist

- [ ] **Zero open critical defects**: No exceptions. If a critical defect exists, go-live is postponed
- [ ] **All major defects have approved workarounds**: Every open major defect has a tested workaround plus a committed fix date within 30 days of go-live
- [ ] **UAT signoff from all process owners**: Every business process area has formal written signoff from its designated owner
- [ ] **Data migration reconciliation approved**: The controller or CFO has signed off that financial balances are reconciled and correct
- [ ] **Performance testing passed**: All performance targets met under expected and peak load conditions
- [ ] **Integration testing passed**: All external system integrations are operational and tested end-to-end
- [ ] **Cutover plan rehearsed**: At least two cutover rehearsals completed successfully within the time window
- [ ] **Rollback plan tested**: The rollback procedure has been executed successfully in a test environment
- [ ] **Training completed**: All end users have completed training and passed proficiency assessments
- [ ] **Support plan activated**: Hypercare support team is staffed, help desk is configured, and escalation paths are documented
- [ ] **Communication plan ready**: Go-live communication to all stakeholders (employees, customers, vendors, banks) is drafted and scheduled
- [ ] **Contingency budget approved**: A contingency budget (typically 15-20% of total project budget) is approved for post-go-live fixes and optimizations

Postponing go-live is expensive and politically painful. It is also far less expensive than going live with a broken system. When making a no-go decision, immediately establish the specific conditions that must be met before reconvening, the revised timeline, and the stakeholder communication plan.

## Building Your Testing Timeline

A realistic testing timeline for a mid-market ERP implementation:

| Phase | Duration | Prerequisites |
|-------|----------|--------------|
| Unit Testing | 3-4 weeks | Configuration complete |
| Integration Testing | 4-6 weeks | Unit testing passed |
| Data Migration Validation | Ongoing (3-4 rounds) | Migration scripts ready |
| UAT | 4-6 weeks | Integration testing passed, training complete |
| Performance Testing | 2-3 weeks | UAT environment stable |
| Cutover Rehearsal | 2 rounds, 1 week each | All phases substantially complete |
| Go/No-Go Decision | 1 week before go-live | All evidence compiled |

Total testing duration for a mid-market implementation: 14 to 20 weeks. Large enterprise implementations should plan for 20 to 30 weeks. The single most common mistake is compressing this timeline when earlier project phases overrun. Every week you cut from testing adds to the post-go-live stabilization period at much higher cost.

## Final Recommendations

**Start test planning during design, not after configuration.** UAT scenarios should be drafted during business process design when subject matter experts are engaged and requirements are fresh.

**Invest in test data management.** A production-representative test dataset that can be refreshed quickly is one of the highest-ROI investments in the entire implementation.

**Automate regression testing.** After every configuration change or defect fix, the full regression suite must be re-executed. Without automation, regression becomes a bottleneck that delays the project or gets skipped entirely.

**Track testing metrics visibly.** Display defect discovery rate, resolution rate, and test completion percentage on a daily dashboard. Testing metrics are the most reliable predictor of go-live readiness.

An ERP go-live is not the finish line. It is the starting line for realizing the business value that justified the investment. Rigorous testing determines whether that starting line leads to a sprint or a stumble.
