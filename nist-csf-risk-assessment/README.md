# Cybersecurity Risk Register and Assessment Report

**Alderbridge Financial Services Ltd** — a NIST Cybersecurity Framework aligned risk assessment

Prepared by Reward Oladejo-Olagboye, 29 July 2026

*Alderbridge Financial Services Ltd is a fictional organisation created to demonstrate a structured cybersecurity risk assessment methodology.*

## Executive Summary

This report presents a cybersecurity risk assessment conducted for Alderbridge Financial Services Ltd, a UK regulated financial services provider offering retail banking, personal lending and payment processing services. The assessment was carried out using the NIST Cybersecurity Framework as the primary structuring model, covering the five core functions of Identify, Protect, Detect, Respond and Recover.

Eighteen risks were identified across the organisation's technology estate, spanning legacy infrastructure, identity and access management, third party dependencies, monitoring capability, incident response readiness and business continuity arrangements. Of these, three were rated High after accounting for existing controls, principally relating to the unsupported legacy core banking platform, untested incident response arrangements and untested backup restoration procedures.

The findings indicate that while Alderbridge maintains a reasonable baseline of technical controls, a number of foundational governance gaps, particularly around testing, documentation and third party oversight, materially increase the organisation's exposure to operational disruption and regulatory scrutiny. A phased remediation roadmap is proposed, prioritising the highest rated risks for action within the next 30 to 90 days, with the remaining risks addressed across a 6 to 12 month programme.

## Scope

This assessment covers the technology systems, infrastructure and third party relationships that support Alderbridge's core retail banking and payment processing operations, including the core banking platform, cloud hosted payment processing systems, identity and access management arrangements, third party vendor relationships, security monitoring and incident response capability, and backup and business continuity arrangements. Physical branch security, general HR policy, and marketing channels not involved in payment processing fall outside scope.

## Methodology

Each risk was scored on two five point scales, likelihood (1, Rare, to 5, Almost Certain) and impact (1, Negligible, to 5, Severe). Inherent and residual risk ratings were calculated by multiplying likelihood by impact, producing a score from 1 to 25, banded as Low (1 to 6), Medium (7 to 12), High (13 to 19) and Critical (20 to 25). Inherent risk reflects the risk level before existing controls; residual risk reflects the level once existing controls are applied, and is the rating used to prioritise remediation.

## Risk Register

| ID | Risk | Function | Likelihood | Impact | Inherent Risk | Existing Controls | Residual Risk | Owner |
|---|---|---|---|---|---|---|---|---|
| R01 | Incomplete and outdated asset inventory across core banking and supporting infrastructure | Identify | 3 | 3 | 9 (Medium) | Annual manual asset audit conducted by IT operations | 6 (Low) | Head of IT Infrastructure |
| R02 | Undocumented and unmanaged third party vendor technology relationships, including payment gateway providers | Identify | 4 | 3 | 12 (Medium) | Procurement conducts basic due diligence at onboarding only | 9 (Medium) | Head of Procurement and Vendor Risk |
| R03 | Absence of a formal data classification standard for customer financial records | Identify | 3 | 3 | 9 (Medium) | Data handled under general data protection policy, no formal classification levels | 9 (Medium) | Data Protection Officer |
| R04 | No formal risk assessment process applied to new digital product launches | Identify | 3 | 3 | 9 (Medium) | Ad hoc technical review by engineering leads prior to launch | 6 (Low) | Head of Product and Technology |
| R05 | Core banking platform runs on an unsupported legacy operating system with no vendor security patching available | Protect | 4 | 5 | 20 (Critical) | Network segmentation and compensating firewall rules around the legacy environment | 16 (High) | Head of IT Infrastructure |
| R06 | Multi factor authentication is not consistently enforced across all privileged and administrative accounts | Protect | 4 | 4 | 16 (High) | MFA enforced for remote access only, not for on premises privileged sessions | 9 (Medium) | IAM Lead |
| R07 | Weak segregation of duties within payment approval workflows allows a single user to initiate and approve high value transactions | Protect | 3 | 5 | 15 (High) | Manual monthly review of high value transaction logs | 8 (Medium) | Head of Payments Operations |
| R08 | Inadequate encryption of customer financial data at rest within the core customer database | Protect | 3 | 5 | 15 (High) | Database access restricted to named administrators only | 12 (Medium) | Head of IT Infrastructure |
| R09 | Absence of a formal joiner mover leaver process resulting in delayed access revocation for departing staff | Protect | 3 | 3 | 9 (Medium) | Quarterly manual access review conducted by IT | 6 (Low) | Head of HR and IAM Lead |
| R10 | Insufficient security awareness training coverage for staff handling financial transactions | Protect | 3 | 3 | 9 (Medium) | Annual generic compliance training, not role specific | 6 (Low) | Head of Learning and Development |
| R11 | Limited security monitoring coverage across cloud hosted payment processing platforms | Detect | 4 | 4 | 16 (High) | On premises SIEM in place, cloud platforms not yet integrated | 12 (Medium) | SOC Manager |
| R12 | No formal threat intelligence feed integrated into security monitoring operations | Detect | 3 | 3 | 9 (Medium) | Ad hoc review of public vendor advisories | 6 (Low) | SOC Manager |
| R13 | Delayed review cadence for privileged account activity logs, typically reviewed monthly rather than near real time | Detect | 3 | 3 | 9 (Medium) | Monthly manual log review by IT security team | 6 (Low) | SOC Manager |
| R14 | Incident response plan has not been tested through a simulation or tabletop exercise within the last 12 months | Respond | 4 | 5 | 20 (Critical) | Documented incident response plan exists but has not been rehearsed | 16 (High) | Head of Information Security |
| R15 | No clearly defined communication plan for regulatory breach notification to the FCA and ICO | Respond | 3 | 4 | 12 (Medium) | General escalation contacts documented, no formal notification playbook | 8 (Medium) | Head of Compliance |
| R16 | Backup restoration procedures for core banking systems have not been tested within the last 12 months | Recover | 4 | 5 | 20 (Critical) | Nightly backups taken and stored offsite, restoration not verified | 16 (High) | Head of IT Operations |
| R17 | No documented business continuity plan specific to a payment processing outage | Recover | 4 | 5 | 20 (Critical) | General organisational business continuity plan exists, not payment specific | 12 (Medium) | Head of Operational Resilience |
| R18 | Single cloud hosting provider dependency for payment processing infrastructure with no failover arrangement | Recover | 3 | 5 | 15 (High) | Contractual SLA in place with hosting provider, no secondary provider | 12 (Medium) | Head of IT Infrastructure |

## Top Priority Risks

**R05, Legacy core banking system on an unsupported operating system.** The platform underpinning retail deposit accounts and payment initiation has reached end of vendor support, so no further security patches are issued. A successful exploit would affect every customer account and payment transaction processed through it. Rated Critical before controls, High after compensating network segmentation. Recommended action: commission a structured migration plan to a supported platform, and in the interim strengthen monitoring and network isolation of the legacy environment.

**R06, Inconsistent multi factor authentication on privileged accounts.** MFA is enforced for remote access but not for privileged accounts accessed from within the corporate network. An attacker who gains a foothold inside the network could move to sensitive systems without a second factor. Rated High before controls, Medium after partial coverage. Recommended action: extend MFA to all privileged and administrative accounts regardless of connection origin.

**R11, Limited monitoring on cloud hosted payment platforms.** The SIEM capability was built around on premises infrastructure and has not been extended to the cloud hosted platforms processing card payments, directly affecting PCI DSS compliance obligations. Rated High before controls, Medium after existing on premises coverage. Recommended action: integrate cloud payment platform logging into the existing SIEM with detection use cases specific to payment fraud.

**R14, Untested incident response plan.** A documented plan exists but has not been exercised through a tabletop simulation in the last 12 months. Plans that have never been rehearsed frequently fail under real conditions. Rated Critical before controls, High after accounting for the existence of a documented plan. Recommended action: schedule a tabletop exercise within 30 days simulating a realistic payment fraud or ransomware scenario.

**R16, Untested backup restoration procedures.** Nightly backups are taken and stored offsite, but restoration has never been verified. A backup that cannot be restored provides no real protection against ransomware or catastrophic data loss. Rated Critical before controls, High after accounting for regular but unverified backups. Recommended action: perform a full restoration test within 30 days and establish quarterly testing.

**R17, No payment specific business continuity plan.** A general continuity plan exists but lacks specific procedures for a sustained payment processing outage. Rated Critical before controls, Medium after the general plan already in place. Recommended action: develop a payment processing specific continuity annex with failover procedures and defined recovery objectives.

## Remediation Roadmap

**Immediate, 0 to 30 days:** tabletop exercise for the incident response plan (R14); backup restoration test for core banking systems (R16); extend MFA to all on premises privileged accounts (R06).

**Short term, 30 to 90 days:** migration or compensating control plan for the legacy operating system (R05); integrate cloud payment platforms into the SIEM (R11); develop and test a payment specific business continuity plan (R17); formalise the FCA and ICO breach notification playbook (R15); strengthen segregation of duties in payment approvals (R07).

**Long term, 6 to 12 months:** formal data classification standard (R03); near real time monitoring of privileged account activity (R13); structured third party risk management programme (R02); role specific security awareness training (R10); evaluate secondary cloud hosting arrangements (R18).

## Conclusion

The findings indicate a concentrated set of high priority risks centred on legacy infrastructure, testing discipline and monitoring coverage, rather than a broad absence of controls. This is a favourable starting position: the existing control framework provides a reasonable foundation, and the remediation roadmap is designed to close the highest impact gaps within a realistic timeframe.
