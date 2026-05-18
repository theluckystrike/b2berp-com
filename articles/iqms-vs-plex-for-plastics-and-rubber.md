---
layout: article
title: "IQMS (DELMIAworks) vs Plex for Plastics and Rubber Manufacturing 2026"
description: "In-depth IQMS DELMIAworks vs Plex comparison for plastics and rubber manufacturers covering OEE, mold management, quality, pricing, and implementation."
date: 2026-05-18
category: compare
permalink: /compare/iqms-vs-plex-plastics-rubber/
tags:
  - IQMS
  - DELMIAworks
  - Plex
  - plastics ERP
  - rubber manufacturing
  - MES
  - OEE
  - manufacturing ERP
---

Plastics and rubber manufacturers operate under constraints that most ERP systems were never designed to handle. Mold management, shot tracking, cavity-level quality data, resin lot traceability, and real-time machine monitoring are foundational requirements that determine whether a plant runs profitably or bleeds margin through scrap, unplanned downtime, and compliance failures. Two platforms have established themselves as serious contenders in this space: IQMS, now branded as DELMIAworks under Dassault Systemes, and Plex, the cloud MES-ERP platform owned by Rockwell Automation. Their architectures, heritage, and strategic trajectories diverge in ways that matter when selecting a system to run a plastics or rubber operation for the next decade.

## Executive Summary

DELMIAworks (formerly IQMS) is a purpose-built ERP and MES platform designed specifically for plastics, rubber, and packaging manufacturers. Native mold management, real-time machine monitoring through direct press integration, cavity-level quality tracking, and resin lot traceability are embedded in the core platform rather than bolted on. Dassault Systemes acquired IQMS in 2019 and rebranded it as DELMIAworks.

Plex, acquired by Rockwell Automation in 2021 for $2.22 billion, is a cloud-native MES and ERP platform with broad manufacturing capabilities spanning automotive, food and beverage, aerospace, and industrial plastics. Plex brings strong IoT sensor integration through the Rockwell ecosystem, robust quality management with embedded SPC, and a genuinely multi-tenant cloud architecture.

For a dedicated plastics or rubber molder whose competitive advantage depends on mold optimization and press utilization, DELMIAworks offers unmatched vertical depth. For a diversified manufacturer who needs a unified cloud platform with strong IoT connectivity and automotive supply chain compliance, Plex provides broader reach.

## Company Overview

**DELMIAworks** traces its roots to IQMS, founded in 1989 in Paso Robles, California, with a singular mission: build ERP software that plastics manufacturers would actually use. The company spent three decades building domain knowledge that horizontal ERP vendors never developed. Dassault Systemes acquired IQMS in January 2019 for approximately $425 million, positioning it within the DELMIA manufacturing operations brand alongside Apriso and Ortems. The platform serves approximately 1,000 manufacturing sites, predominantly in North America. The sweet spot is mid-market plastics and rubber manufacturers with 50 to 500 employees.

**Plex** was founded in 1995 in Troy, Michigan, originally as a cloud-based MES for automotive suppliers. The platform evolved into a comprehensive ERP while retaining its manufacturing execution roots, giving Plex an unusual architecture where MES and ERP are a single platform and production data flows directly into financial transactions in real time. Rockwell Automation's acquisition created a vertically integrated stack spanning factory automation hardware, industrial IoT (FactoryTalk), and enterprise software. Plex serves over 700 customers across approximately 2,900 production facilities globally, with strongest penetration in automotive Tier 1 and Tier 2 suppliers.

## Feature Comparison

| Capability | DELMIAworks (IQMS) | Plex (Rockwell) |
|-----------|---------------------|------------------|
| **Core ERP (Finance, Purchasing, Sales)** | Full suite, integrated | Full suite, integrated |
| **MES / Production Execution** | Native, real-time | Native, real-time |
| **Machine Monitoring** | Direct press integration, cycle-level | IoT sensor-based, PLC integration |
| **Mold Management** | Native module with cavity tracking | Tooling management (general purpose) |
| **Resin / Material Lot Traceability** | Native, lot and sublot | Native, lot-level |
| **Quality Management** | Integrated with mold/cavity data | Integrated SPC, PPAP, FMEA |
| **OEE Tracking** | Real-time, per-press | Real-time, per-work-center |
| **Scheduling / APS** | Mold-aware finite scheduling | Finite capacity scheduling |
| **EDI / Automotive Supply Chain** | Supported | Deep AIAG/automotive compliance |
| **IoT / Sensor Integration** | Through Dassault ecosystem | Native Rockwell/FactoryTalk stack |
| **Cloud Architecture** | Hosted / private cloud | Multi-tenant SaaS |
| **Regulatory Compliance** | FDA, ISO, IATF support | FDA, ISO, IATF, SQF support |
| **PLM / Digital Twin** | Dassault 3DEXPERIENCE integration | Partner integrations |

## Plastics-Specific Features

This is where the comparison becomes most consequential.

**DELMIAworks** was built by people who understand what happens inside a barrel at 400 degrees Fahrenheit. Mold management tracks every aspect of the mold lifecycle: cavity count, cavity status, shot count against preventive maintenance thresholds, mold location across plants, and mold-specific quality history. When a mold reaches its PM threshold, the system automatically triggers a work order and adjusts the production schedule. Press integration connects directly to controllers from Engel, Arburg, Husky, Sumitomo Demag, Milacron, and Nissei, capturing cycle time, shot weight, cushion position, barrel temperatures, and clamp tonnage at the cycle level. Resin management handles drying time tracking for hygroscopic materials, regrind percentage calculations, color concentrate ratios, and lot-level traceability through blending and regrinding. Secondary operations scheduling manages downstream processes like pad printing, hot stamping, ultrasonic welding, and assembly.

**Plex** approaches plastics from a broader manufacturing platform perspective. Its tooling management module tracks mold location, maintenance history, and usage counts, but does not natively model cavity-level detail or shot-count-based maintenance triggers. Manufacturers can configure custom workflows to approximate this, but it requires implementation effort DELMIAworks handles out of the box. Machine connectivity leverages the Rockwell ecosystem through OPC UA, MQTT, and direct PLC communication, which is more flexible across machine types but requires more configuration for plastics-specific parameters. Quality management is enterprise-grade with native SPC, PPAP, FMEA, and layered process audits, battle-tested across hundreds of automotive supply chain deployments. Material traceability supports lot-level tracking but plastics-specific concepts like regrind tracking and cavity-to-lot correlation require custom configuration.

## Machine Monitoring and OEE

**DELMIAworks** calculates OEE at the individual press level using data captured directly from machine controllers. Availability, performance, and quality metrics update in real time with drill-down capability to the cycle level. Because DELMIAworks understands the relationship between mold, press, and material, its OEE calculations can isolate whether a performance shortfall is caused by a press issue, a mold problem, or a material variation. This granularity is difficult to replicate in platforms that treat the press as a generic work center.

**Plex** provides OEE tracking at the work center level with real-time updates driven by IoT data collection. Dashboards support historical trend analysis, shift comparisons, and benchmarking across plants. For multi-process plants where plastics is one of several operations, Plex's standardized OEE approach provides consistent metrics across all work centers. The practical difference: DELMIAworks delivers deeper plastics-aware OEE out of the box, while Plex delivers broader OEE tracking that works across any manufacturing process.

## Quality Management

**DELMIAworks** ties quality data directly to mold cavities, press process parameters, and resin lots. An out-of-spec dimension can be traced to the specific cavity, the process conditions during that shot cycle, and the resin lot used. For medical device and automotive plastics manufacturers, this traceability is a regulatory requirement.

**Plex** offers broader quality tools: native PPAP management, control plan integration, layered process audits, FMEA documentation, and supplier quality management. For manufacturers embedded in automotive supply chains where these methodologies are mandated, Plex's quality framework accommodates diverse compliance demands within a single system.

## Pricing

| Pricing Dimension | DELMIAworks | Plex |
|-------------------|-------------|------|
| **License Model** | Named user, subscription | Named user, subscription |
| **Subscription Range** | $200-$400/user/month | $200-$400/user/month |
| **Typical Entry Point** | ~$150K/year (50 users) | ~$150K/year (50 users) |
| **Implementation Cost** | 1-2x annual subscription | 1.5-2.5x annual subscription |
| **Total First-Year Cost (100 users)** | $400K-$700K | $450K-$800K |
| **Machine Monitoring** | Included in MES module | Included or via Rockwell IoT bundle |

DELMIAworks pricing benefits from including plastics-specific functionality in the base platform. Manufacturers do not pay extra for mold management, press integration, or resin tracking. Plex pricing may increase when Rockwell IoT components are required for deep machine connectivity. Both vendors offer modular pricing, allowing phased deployments that start with core ERP and expand over time.

## Implementation

**DELMIAworks** implementations typically run 4 to 9 months for a single-site plastics manufacturer. The methodology is built around plastics industry workflows, which reduces business process mapping effort. Consultants understand mold scheduling, press allocation, and resin management without extensive education from the customer. Multi-site rollouts extend to 9 to 15 months. One risk factor: ensuring you get implementation consultants with IQMS-specific experience rather than generalist Dassault resources.

**Plex** implementations run 6 to 12 months for a single site, reflecting the configuration effort required to tailor generic manufacturing modules to plastics-specific processes. The cloud-native architecture eliminates infrastructure provisioning time, but functional configuration for plastics operations can offset this advantage. Multi-site deployments take 10 to 18 months.

## Best For

### Choose DELMIAworks if:

- Your primary process is injection molding, extrusion, blow molding, or rubber molding
- Mold management, cavity-level tracking, and shot-count-based maintenance are critical
- You need direct press integration with major injection molding machine manufacturers
- Resin lot traceability through blending and regrinding is a regulatory requirement
- You want plastics-specific OEE analysis that isolates mold, press, and material variables
- Your operation is predominantly plastics, not a diversified multi-process manufacturer

### Choose Plex if:

- You are a diversified manufacturer where plastics is one of several production processes
- You serve automotive OEMs and need native PPAP, FMEA, and AIAG-compliant quality management
- You want a genuinely cloud-native, multi-tenant platform with no on-premise infrastructure
- Your automation infrastructure is Rockwell-based and you want seamless PLC-to-ERP data flow
- You operate in food-contact plastics and need SQF or FSSC 22000 compliance support
- Multi-plant global operations with centralized reporting are a priority

## Verdict

DELMIAworks and Plex represent fundamentally different strategies. DELMIAworks is the specialist: purpose-built for the plastics industry over three decades, with domain depth that no horizontal platform can match. If your plant lives and dies by mold uptime, press utilization, and cavity-level quality, DELMIAworks speaks your language natively. Plex is the platform player: a cloud-native MES-ERP backed by Rockwell Automation's industrial IoT ecosystem, proven at scale in automotive and food supply chains.

The decision comes down to manufacturing identity. If you are a plastics company first and everything else second, DELMIAworks eliminates the configuration burden of adapting a general-purpose system to your industry. If plastics processing is a component of a broader operation, or your customer base demands automotive supply chain compliance, Plex provides the breadth and cloud architecture to unify operations on a single platform.

## Frequently Asked Questions

**Is IQMS the same as DELMIAworks?**
Yes. Dassault Systemes acquired IQMS in January 2019 and rebranded it as DELMIAworks. The core platform and plastics-specific functionality remain intact. The rebrand reflects integration into Dassault's DELMIA portfolio, adding access to simulation, PLM, and digital twin capabilities.

**Can Plex handle injection molding-specific requirements like cavity tracking?**
Plex's tooling management handles mold tracking at a general level. Cavity-level tracking and plastics-specific maintenance triggers such as shot count thresholds require custom configuration. It can be made to work, but it requires more implementation effort than DELMIAworks where these features are native.

**Which platform is better for automotive plastics suppliers?**
It depends on the balance between plastics depth and automotive compliance breadth. DELMIAworks supports IATF 16949 and EDI, and many automotive Tier 2 and Tier 3 suppliers use it successfully. Plex has deeper native support for PPAP, FMEA, and AIAG standards. If your customers require extensive PPAP documentation, Plex has an edge. If your competitive advantage is mold and press optimization, DELMIAworks delivers more value on the shop floor.

**Do both platforms support FDA-regulated plastics manufacturing?**
Yes. Both support lot traceability, electronic batch records, audit trails, and documentation required for FDA 21 CFR Part 11 compliance. DELMIAworks adds resin-level traceability through blending and regrinding, relevant for medical device plastics. Plex has additional compliance frameworks for food safety (SQF, FSSC 22000) benefiting food-contact packaging manufacturers.

**What is the total cost of ownership over five years?**
For a 100-user single-site plastics manufacturer, five-year TCO typically falls in the $1.5M to $2.5M range including subscription, implementation, training, and support. DELMIAworks may have lower configuration costs for plastics workflows since these are native. Plex may have higher initial configuration costs but lower infrastructure costs due to its cloud-native architecture.

**Can DELMIAworks integrate with Rockwell Automation equipment?**
DELMIAworks supports OPC UA and other industrial communication protocols, so integration with Rockwell PLCs is technically feasible. However, it lacks the native Rockwell integration that Plex offers. If your plant runs Rockwell automation infrastructure, Plex provides a more seamless data path. If your presses use embedded controllers from Engel or Arburg, DELMIAworks' direct press integrations may be more relevant.
