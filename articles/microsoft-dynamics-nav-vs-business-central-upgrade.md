---
layout: article
title: "Microsoft Dynamics NAV vs Business Central: Upgrade Guide 2026"
description: "Complete upgrade guide from Dynamics NAV to Business Central covering migration paths, costs, timelines, feature gains, and decision framework for 2026."
date: 2026-05-18
category: compare
permalink: /compare/dynamics-nav-vs-business-central-upgrade/
tags: [Microsoft Dynamics, ERP Migration, Dynamics NAV, Business Central, Cloud ERP, Navision]
---

Microsoft Dynamics NAV — still called Navision in hallway conversations across Northern Europe — has been the backbone of mid-market operations for more than two decades. Over 160,000 customers built their businesses on NAV. Warehouses run on it. Manufacturing floors depend on it. Finance teams close their books with it every month. But the product has reached the end of the road. Mainstream support ended for NAV 2018 in January 2023, and the remaining extended support windows are closing fast. Microsoft has made its position unambiguous: Dynamics 365 Business Central is the successor, the only successor, and the platform receiving all future investment.

This guide is not a sales pitch for Business Central. It is a migration planning document for IT directors, CFOs, and operations leaders who need to understand what the upgrade actually involves — the costs, the timelines, the architectural differences, and the honest trade-offs. NAV customers who plan their upgrade in 2026 will secure better partner availability and more favorable licensing. Those who wait will face the same compressed timelines and inflated costs that plagued late movers in every previous Microsoft ERP transition.

## Executive Summary

Dynamics NAV is a proven on-premises ERP built on C/AL code, SQL Server, and the classic Windows client architecture. Business Central is its cloud-native successor, rewritten in AL language, delivered as a SaaS service on Azure, and deeply integrated with the Microsoft 365 and Power Platform ecosystem. The core business logic — general ledger, purchasing, sales, inventory, manufacturing — carries forward. The technology stack, deployment model, and extensibility architecture do not.

Typical upgrade costs range from $30,000 for straightforward single-entity implementations to $200,000 or more for complex multi-company environments with heavy customization. Timelines run 3 to 9 months depending on scope. Organizations with more than 50 custom objects or deep ISV add-on dependencies should budget toward the higher end of both ranges.

The business case is straightforward: NAV is a depreciating asset. Every month of delay increases migration risk, reduces partner availability, and accumulates technical debt that makes the eventual upgrade more expensive.

## Why Upgrade from Dynamics NAV

### Support Has Ended or Is Ending

Microsoft ended mainstream support for Dynamics NAV 2018 — the final NAV-branded release — in January 2023. Extended support continues through January 2028, but extended support means security patches only. No feature updates. No regulatory compliance updates. No tax table changes. No new integration capabilities. Organizations in regulated industries face audit risk from running unsupported ERP software. For everyone else, the risk is simpler: when something breaks, Microsoft will not fix it.

### The Technology Stack Is Obsolete

NAV's architecture reflects decisions made in the 1990s and refined through the 2000s. The C/SIDE development environment and C/AL programming language have no future. Microsoft stopped accepting C/AL code contributions years ago. The talent pool of developers fluent in C/AL shrinks every quarter as experienced consultants retire or retrain on AL. Finding a C/AL developer in 2026 is already difficult. By 2028, it will be functionally impossible at reasonable rates.

The Windows client (RoleTailored Client) requires on-premises infrastructure — servers, VPNs, terminal services — that modern IT organizations are actively decommissioning. NAV's web client, while functional, was always a retrofit rather than a native experience.

### Your ISV Add-Ons Are Migrating Without You

The independent software vendor ecosystem that made NAV powerful — Jet Reports, Continia, Lanham Associates, Insight Works — has already shifted development to Business Central. Many ISVs have stopped releasing NAV-compatible updates entirely. The add-ons you depend on are either already Business Central-only or will be within 12 to 18 months. Staying on NAV means running increasingly outdated versions of the tools your operations depend on.

### Microsoft's Investment Is Unidirectional

Business Central receives two major updates per year (Wave 1 in April, Wave 2 in October), plus continuous minor updates. NAV receives nothing. Every feature Microsoft builds — Copilot AI assistance, warehouse automation, sustainability tracking, advanced intercompany — lands exclusively in Business Central. The gap between what NAV can do and what Business Central can do widens with every release cycle.

## Feature Comparison

| Capability | Dynamics NAV | Business Central |
|---|---|---|
| Deployment | On-premises only | Cloud (SaaS), on-premises, hybrid |
| Development Language | C/AL (deprecated) | AL (modern, VS Code-based) |
| Development Environment | C/SIDE | Visual Studio Code + AL Extension |
| Update Frequency | Manual upgrades (18-24 mo cycles) | Continuous (2 major + minor updates/year) |
| Client Access | Windows client, limited web | Full web client, mobile apps, Teams integration |
| Extensibility | Direct code modification | Extension-based (AppSource marketplace) |
| AI Capabilities | None | Copilot (bank reconciliation, marketing text, analysis) |
| Power Platform | No native integration | Native Dataverse, Power BI, Power Automate |
| API Architecture | SOAP/OData (limited) | Full REST APIs, webhooks, event-driven |
| Multi-Environment | Complex (separate databases) | Built-in sandbox and production environments |
| Per-User Licensing | Perpetual + enhancement plan | $70 Essential / $100 Premium per user/month |
| Infrastructure | Customer-managed SQL Server | Microsoft-managed Azure |
| Compliance | Manual (customer responsibility) | SOC 1/2, ISO 27001, GDPR tools built in |
| Localization | 44 country versions | 50+ country localizations, continuous updates |

## Migration Paths

### Path 1: Direct Upgrade (NAV 2018 to Business Central)

Organizations running NAV 2018 have the most straightforward upgrade path. Microsoft provides data upgrade toolkits that handle the transition from C/AL to AL for standard objects. The core data — chart of accounts, customer and vendor records, open transactions, item master — migrates through automated tooling. Custom objects and modifications require manual conversion.

This path works best for organizations with fewer than 20 custom objects and limited ISV dependencies. Expect 3 to 5 months of elapsed time including testing.

### Path 2: Staged Upgrade (NAV 2009-2016 to NAV 2018 to Business Central)

Organizations running older NAV versions (2009, 2013, 2015, 2016) cannot upgrade directly to Business Central. The supported path requires first upgrading to NAV 2018, stabilizing, and then migrating to Business Central. Each hop carries its own data conversion, testing, and validation requirements.

This doubles the project timeline and cost. Budget 6 to 9 months and plan for two distinct go-live events. Some organizations choose to run NAV 2018 as an interim state for 3 to 6 months before beginning the Business Central migration.

### Path 3: Reimplementation

Organizations with extensive customization — 50 or more modified objects, deeply embedded ISV solutions, or complex manufacturing configurations — often find reimplementation more cost-effective than upgrade. Reimplementation means starting fresh with Business Central, configuring it from requirements rather than migrating technical debt, and using data migration tools to bring across master data and open transactions.

Reimplementation is the most expensive path upfront ($120,000 to $200,000 or more) but often delivers the cleanest result. It forces the organization to re-evaluate business processes rather than simply replicating legacy workflows in new technology.

### Path 4: Cloud Migration Assessment Program (CMAP)

Microsoft offers the Cloud Migration Assessment Program through qualified partners. CMAP provides a structured evaluation of your NAV environment, identifies migration blockers, estimates effort, and produces a migration roadmap. The assessment typically takes 2 to 4 weeks and costs $5,000 to $15,000 depending on complexity. This is money well spent for organizations uncertain about which migration path to pursue.

## Timeline and Cost

### Cost Breakdown

| Component | Small (1-15 users) | Mid-Market (16-75 users) | Enterprise (76-250 users) |
|---|---|---|---|
| Licensing (Year 1) | $12,600-$18,000 | $76,800-$90,000 | $240,000-$300,000 |
| Implementation Partner | $15,000-$40,000 | $50,000-$120,000 | $100,000-$200,000 |
| Data Migration | $3,000-$8,000 | $10,000-$30,000 | $25,000-$60,000 |
| Custom Development | $0-$15,000 | $15,000-$50,000 | $40,000-$100,000 |
| Training | $2,000-$5,000 | $8,000-$20,000 | $15,000-$40,000 |
| **Total First Year** | **$32,600-$86,000** | **$159,800-$310,000** | **$420,000-$700,000** |

Note: These figures assume Business Central online (SaaS). On-premises deployments add infrastructure costs but eliminate the per-user monthly licensing in favor of perpetual licenses with an annual enhancement plan.

### Timeline by Complexity

**Low complexity** (standard NAV with minimal customization): 3 to 4 months from kickoff to go-live. This includes 2 to 3 weeks of assessment, 4 to 6 weeks of configuration and data migration, 3 to 4 weeks of testing, and 2 weeks of training and go-live preparation.

**Medium complexity** (moderate customization, 2-5 ISV add-ons): 5 to 7 months. Add time for custom AL development to replace C/AL modifications, ISV add-on replacement or migration, and integration re-architecture.

**High complexity** (heavy customization, multi-company, manufacturing): 7 to 9 months. These projects typically require reimplementation rather than upgrade and involve significant business process redesign.

## What You Gain

**Continuous innovation without upgrade projects.** Business Central updates automatically twice per year. You never run another upgrade project. Features like Copilot AI, sustainability reporting, and advanced warehouse management arrive automatically.

**Modern developer ecosystem.** AL development in Visual Studio Code means access to a growing talent pool of developers trained on modern tools. AppSource provides a marketplace of 4,000-plus certified extensions that install without code modification.

**Native Microsoft integration.** Business Central connects natively to Microsoft 365, Power BI, Power Automate, Power Apps, and Teams. Financial data flows directly into Excel online. Approval workflows run in Teams. Dashboards update in real time through Power BI embedded.

**Reduced infrastructure burden.** Cloud deployment eliminates SQL Server management, backup administration, Windows Server patching, VPN configuration, and terminal services. Your IT team stops managing ERP infrastructure and starts managing ERP outcomes.

**Built-in compliance.** SOC 1 and SOC 2 attestation, ISO 27001 certification, GDPR tooling, and data residency controls are built into the platform. Audit preparation for ERP-related controls becomes significantly simpler.

**Scalable licensing.** Add users, remove users, switch between Essential and Premium tiers — all without hardware capacity planning. Seasonal businesses can scale licensing to match operational demand.

## What You Lose

**Direct code access.** NAV allowed direct modification of base application objects. Business Central enforces an extension model where customizations are layered on top of the standard application without modifying source code. This is architecturally superior but requires a different development approach. Developers accustomed to C/SIDE find the transition frustrating for the first 2 to 3 months.

**On-premises control** (if choosing cloud). Cloud deployment means Microsoft manages your infrastructure. You cannot access the underlying SQL database directly. Reporting that relied on direct SQL queries must be rebuilt using APIs, OData feeds, or Power BI. Organizations in highly regulated industries or with data sovereignty requirements may need the on-premises deployment option, which preserves control but sacrifices some cloud-native features.

**Legacy customization investment.** Every line of C/AL code you wrote or paid for must be rewritten in AL or replaced with an AppSource extension. Customizations that cost $50,000 to build a decade ago still require $15,000 to $30,000 to recreate, even if the business logic is identical. This is the most emotionally difficult cost in the migration — paying again for capability you already have.

**Familiar interface workflows.** Power users who have spent 10 or more years in the NAV Windows client will find Business Central's web interface different. The core navigation logic is similar, but muscle memory built over years does not transfer instantly. Budget genuine training time, not just a day of overview sessions.

**Report customization flexibility.** NAV's classic report designer allowed significant formatting control. Business Central uses RDLC and Word layouts with different capabilities and constraints. Complex reports, especially those with precise formatting requirements for regulatory submission, may require significant rework.

## Decision Framework

### Upgrade Now If

- You are running NAV 2018 or later with fewer than 30 custom objects
- Your ISV add-ons have confirmed Business Central equivalents
- Your IT team is actively decommissioning on-premises infrastructure
- You need capabilities that only Business Central provides (Copilot, Power Platform, Teams integration)
- Your C/AL developer resources are aging out within 2 years
- You are in a regulated industry where running unsupported software creates compliance risk

### Delay (But Not Beyond 2027) If

- You are mid-cycle on another major system implementation (warehouse management, CRM, HR)
- Your organization is in active M&A that would change the scope of any ERP project
- Budget constraints are genuinely binding and a 6-month delay would materially improve funding
- You are running NAV 2009 or 2013 and need the staged upgrade path, which requires planning for two separate projects

### Do Not Delay If

- You are running NAV 2009 with direct SQL modifications and no documented customization inventory
- Your primary C/AL developer is within 18 months of retirement
- You have already received audit findings related to unsupported software
- Microsoft partners in your region are quoting 4 to 6 month wait times for new projects

## Frequently Asked Questions

**Can I run Business Central on-premises instead of cloud?**
Yes. Business Central offers an on-premises deployment option with perpetual licensing. However, on-premises deployments receive updates less frequently, miss some cloud-only features (Copilot, certain Power Platform integrations), and still require infrastructure management. Microsoft's strategic direction favors cloud, and the feature gap between cloud and on-premises will continue to widen.

**Will my existing NAV data migrate automatically?**
Master data (customers, vendors, items, chart of accounts) and open transactions migrate through Microsoft's data upgrade toolkit for supported upgrade paths. Historical transactions can be migrated but require additional effort. Many organizations choose to archive NAV historical data separately and start Business Central with a clean transactional history plus migrated open balances.

**What happens to my C/AL customizations?**
C/AL code does not run in Business Central. Every customization must be converted to AL and repackaged as an extension. Microsoft provides a code conversion tool (txt2al) that handles syntax translation for standard objects, but custom logic requires manual review and testing. Budget 2 to 4 hours of developer time per custom object for conversion and validation.

**How does licensing change?**
NAV used perpetual licenses with an annual enhancement plan (typically 16 to 18 percent of license cost). Business Central cloud uses per-user monthly subscriptions: $70 per user per month for Essentials (financials, supply chain, project management) or $100 per user per month for Premium (adds manufacturing and service management). For most organizations, the monthly cost is comparable to what they paid for enhancement plans plus infrastructure hosting.

**Can I keep some users on NAV while migrating others to Business Central?**
Running NAV and Business Central in parallel during migration is common and recommended. Most organizations maintain NAV in read-only mode for 3 to 6 months after go-live to allow reference lookups and historical reporting while users acclimate to Business Central. Running both systems in production with live transactions is technically possible but operationally complex and not recommended.

**What is the biggest risk in NAV-to-Business Central migration?**
Undocumented customizations. Organizations that modified NAV objects over 10 to 15 years without maintaining documentation discover during migration that they have 3 to 5 times more custom logic than they estimated. The single most valuable pre-migration activity is a complete customization audit: identify every modified object, document its business purpose, and determine whether the customization is still needed or can be replaced by standard Business Central functionality.
