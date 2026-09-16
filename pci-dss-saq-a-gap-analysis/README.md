# PCI DSS v4.0.1 SAQ A Gap Analysis

**Willowmere Home & Living** — a 22 control self assessment against PCI DSS v4.0.1

Prepared by Reward Oladejo-Olagboye, 16 September 2026. Standard referenced: PCI DSS v4.0.1, Self Assessment Questionnaire A

*Willowmere Home & Living is a fictional organisation created to demonstrate a structured PCI DSS gap analysis methodology.*

## For Leadership: What You Need to Know

We reviewed how our online store handles card payments against PCI DSS. Because all card payments are handled through Stripe's hosted checkout, customer card numbers never touch our own systems, removing most of the risk a typical online retailer carries.

The area that needs attention is newer, and catches a lot of businesses out. Small pieces of code on our checkout page, analytics tools and chat widgets, are not currently tracked or monitored the way the rules now require. Attackers have started targeting exactly this kind of unmonitored code to quietly steal card details as customers type them in. It comes down to two practical things: keeping an up to date list of every piece of code running on the checkout page, and making sure one named person is responsible for keeping it that way.

## Purpose and Scope

This document assesses Willowmere's compliance with PCI DSS v4.0.1 using SAQ A, the questionnaire for merchants who have fully outsourced cardholder data handling to a validated third party. It covers the checkout page and its supporting infrastructure, the scripts and third party services loaded on it, and administrative access to systems capable of affecting it.

## SAQ Eligibility Determination

All card payment capture is handled by Stripe Checkout, a fully hosted, PCI DSS validated redirect page. Willowmere's own servers never receive, transmit, process or store cardholder data. On this basis, Willowmere correctly qualifies for SAQ A rather than SAQ A EP or SAQ D. This should be reconfirmed annually, since any change to the checkout flow could shift the eligibility category.

## Methodology

Willowmere's practices were assessed against all 22 SAQ A requirements, including a live audit of the checkout page using browser developer tools, a review of administrative access across the CMS, CDN and DNS providers, and discussion with the team responsible for day to day website operations. Each control was RAG rated: Green fully met with evidence, Amber partial or outdated evidence, Red not currently met.

## Gap Analysis

| No. | PCI Req. | Control | Current State | RAG | Remediation |
|---|---|---|---|---|---|
| 1 | Req 3 | Account Data Protection | No cardholder data stored on Willowmere's systems, policy confirmed annually. | Green | No action required. |
| 2 | Req 4 | Transmission Encryption | Checkout and Stripe pages both enforce TLS 1.3, confirmed via SSL Labs scan. | Green | No action required, retest annually. |
| 3 | Req 2 | Vendor Default Credentials | Admin accounts use unique passwords, CDN console still uses default recovery contact. | Amber | Update CDN console recovery contact. |
| 4 | Req 9 | Physical Access to Cardholder Data | No card details ever accepted by phone, post or in person. | Green | No action required. |
| 5 | Req 12.1 | Information Security Policy | Policy exists but was last reviewed over two years ago. | Amber | Review, reissue, and schedule mandatory annual review. |
| 6 | Req 12.8 | Service Provider Management | Provider list exists, current AOCs not collected from all. | Red | Request current AOCs, set annual renewal reminder. |
| 7 | Req 12.1.2 | Named Roles and Responsibilities | PCI tasks handled informally by "the IT team", no named owner. | Red | Assign a named Compliance Lead role. |
| 8 | Req 12.3.1 | Targeted Risk Analyses | No documented risk analysis for flexible frequency controls. | Red | Document a short risk based justification for review frequencies. |
| 9 | Req 12.6 | Security Awareness Training | Informal guidance given, no training records kept. | Amber | Move to a tracked annual training programme. |
| 10 | Req 12.10 | Incident Response Plan | General plan exists, not tested against a payment specific scenario. | Amber | Run a tabletop exercise and update the plan. |
| 11 | Req 6.4.3 | Payment Page Script Inventory | No formal inventory of scripts loading on the checkout page. | Red | Audit the checkout page and build a script inventory. |
| 12 | Req 11.6.1 | Script Tamper Detection | No Content Security Policy or tamper detection deployed. | Red | Deploy a CSP with Subresource Integrity hashes. |
| 13 | Req 6.3.1 | Vulnerability Identification for Scripts | No process to monitor third party scripts for known vulnerabilities. | Red | Subscribe to a vulnerability feed, assign triage responsibility. |
| 14 | Req 6 (practice) | Script Bill of Materials | No record of script versions loaded on the checkout page. | Red | Maintain a version log for every script and library. |
| 15 | Req 8.4.2 | Multi Factor Authentication | MFA enforced on CMS admin, not on CDN console or DNS account. | Amber | Extend MFA to every admin interface. |
| 16 | Req 8.2.1 | Unique User IDs | Every staff member has an individual account, no shared logins found. | Green | No action required. |
| 17 | Req 8.3.4 | Account Lockout | Accounts lock after 10 failed attempts, 30 minute minimum lockout. | Green | No action required. |
| 18 | Req 8.3.6 | Password Length and Complexity | CMS enforces 12 character minimum, a legacy invoicing tool enforces only 8. | Amber | Upgrade the legacy tool or exclude it from PCI scope. |
| 19 | Req 8.2.8 | Session Timeout | Admin sessions time out after 15 minutes of inactivity. | Green | No action required. |
| 20 | Req 11.4 | Provider Penetration Testing | Stripe's AOC and penetration testing summary obtained annually. | Green | No action required. |
| 21 | Req 12.11 | Annual SAQ and AOC Submission | Last year's SAQ submitted later than intended, no calendar reminder. | Amber | Set a recurring reminder eleven months out. |
| 22 | Req 6.5.1 | Change Management for Payment Pages | Developers can change the checkout page directly, no review or sign off. | Red | Introduce a documented change management process. |

## Key Findings: Priority Gaps

**Payment Page Script Inventory (Control 11).** No formal inventory exists of scripts on the checkout page. This is the single most common failure point for SAQ A merchants under v4.0.1, since attackers now compromise a third party script with legitimate access rather than breaching servers directly. See Appendix below for the completed inventory.

**Script Tamper Detection (Control 12).** No CSP or tamper detection is deployed, so a compromised script could run for months undetected. PCI DSS v4.0.1 makes this mandatory, not optional.

**Named Roles and Responsibilities (Control 7).** PCI tasks sit with "the IT team" as a concept rather than a specific person, which is how controls quietly lapse.

**Service Provider Management (Control 6).** Current AOCs have not been collected from all providers. SAQ A eligibility rests on every provider touching the payment flow being able to demonstrate its own compliance.

**Targeted Risk Analyses (Control 8).** This newer, governance focused requirement asks Willowmere to show its reasoning for chosen review frequencies, not to change the control itself.

**Change Management for Payment Pages (Control 22).** Developers can push changes directly with no review. Most real world Magecart style attacks succeed through exactly this kind of unreviewed change.

## Remediation Roadmap

**Immediate, 0 to 30 days:** assign a named Compliance Lead (Control 7); audit the checkout page and build a script inventory (Control 11); request current AOCs from all providers (Control 6).

**Short term, 30 to 90 days:** deploy a CSP and tamper detection (Control 12); extend MFA to the CDN console and DNS account (Control 15); introduce documented change management (Control 22); document targeted risk analyses (Control 8).

**Ongoing:** subscribe to a vulnerability feed (Control 13); maintain a script version log (Control 14); replace or exclude the legacy invoicing tool (Control 18); move to tracked annual training (Control 9); calendar annual policy and SAQ reviews (Controls 5, 21).

## Payment Page Script Inventory

| Script / Vendor | Source Domain | Loads on Checkout | Integrity Monitored | Status |
|---|---|---|---|---|
| Stripe Checkout.js | js.stripe.com | Yes | Yes, by Stripe | Green |
| Google Analytics (gtag.js) | googletagmanager.com | Yes, on confirmation page | No | Red |
| Meta Pixel | connect.facebook.net | Yes, on confirmation page | No | Red |
| Klaviyo | static.klaviyo.com | Yes | No | Red |
| Intercom Chat Widget | widget.intercom.io | Yes, site wide | No | Red |
| Hotjar | script.hotjar.com | Yes | No | Red |
| Cloudflare CDN | cdnjs.cloudflare.com | Indirect, serves other scripts | Partial, via CDN provider | Amber |
| jQuery (self hosted) | willowmerehome.co.uk/assets | Yes | No, version not tracked | Red |

## Conclusion

Willowmere's decision to fully outsource card capture to Stripe has already eliminated the largest categories of PCI risk a merchant can carry. The gaps identified here sit almost entirely in the newer script security and governance requirements introduced by v4.0.1, rather than in the foundational controls, which are largely in good order. None of the identified gaps require storing cardholder data or rebuilding the checkout flow, and the roadmap above is achievable within a single quarter.
