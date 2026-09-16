# Eleven Staff, One Trust

**Dismissed this year for looking at records they had no reason to see**

A composite Data Protection Impact Assessment, mapped to the NCSC Cyber Assessment Framework via DSPT Category 1. What a regional shared care record actually shares, told through a composite case study spanning general practice, community mental health, and social care.

Reward Oladejo-Olagboye, Compliance Officer

*This case study is entirely fictional. Leah, the Ashcombe Integrated Care System, and every organisation named here are composite constructions created for professional development and portfolio purposes only. None represent any real individual, patient, service user, or organisation.*

## Leah's File

Leah is 34, with a diagnosis of bipolar disorder managed by a GP, a community psychiatric nurse, and a part time social worker, each historically keeping their own file on her. Eight months ago an out of hours GP with no access to her psychiatric notes gave generic advice on a Sunday night call, leaving her anxious until her own nurse called the next morning.

This year, Ashcombe's GP practices, its community mental health trust, and its adult social care team began sharing a single care record to close exactly this gap. A second out of hours call went differently, with the duty clinician able to see her history and give advice specific to her.

But the same system that closed one gap opened another. Three months in, while booking a routine appointment for a sprained ankle, Leah noticed a receptionist's glance pause on a safeguarding note written over a year earlier, long since resolved. Nobody broke a rule. The receptionist had access because the system gave her access, not because she needed that note to book an appointment. Leah did not complain, but became noticeably more guarded with her GP afterwards.

## Why This Is a Legal Requirement, Not a Courtesy

Information about a person's mental health is special category data under UK GDPR. Processing it needs both a lawful basis and a specific condition under Article 9, usually that it is necessary for health or social care. An organisation must name the legal ground and show real safeguards around who can see the data, how it moves, and how long it stays on record.

Under Article 35 of UK GDPR, a DPIA is mandatory wherever processing is likely to cause high risk, and this shared care record clears that bar several times over: special category health data processed at scale across three organisations; records matched and combined from previously separate systems; data belonging to a group generally recognised as vulnerable; and a technology platform not previously used to link these three services. Meeting one of these criteria is often enough on its own. This meets four.

## What Changes at This Scale

The Data Security and Protection Toolkit, DSPT, is the annual self assessment that CQC registered providers, NHS organisations, and their suppliers complete each year against the National Data Guardian's ten data security standards. Larger, higher risk organisations sit in Category 1, assessed instead against a version aligned to the NCSC Cyber Assessment Framework, four objectives covering how an organisation manages risk, protects against attack, detects incidents, and responds when something goes wrong. DSPT added a fifth objective on top: using and sharing information appropriately, which exists because of exactly what happened to Leah.

Here, the controllers are a group of GP practices, an NHS community mental health trust, and a local authority social care team, jointly running a shared care record across the fictional Ashcombe Integrated Care System. The purpose, faster and safer decisions in urgent situations, is legitimate, but a GP receptionist booking a routine appointment does not need to see an eighteen month old safeguarding note. Where a summary view achieves the same safety outcome as a full record, proportionality points toward the summary, with full access available only on a documented reason.

NHS England issued a national warning earlier this year after a trust dismissed staff for exactly this kind of access, unrelated to the patients' care, warning that unauthorised access can mean dismissal, regulatory referral, or prosecution.

## Risk Assessment: Leah's Shared Care Record

| Risk Area | Existing Control Now | Current | Mitigation Target | Target | CAF Objective |
|---|---|---|---|---|---|
| Inconsistent access controls across the three systems | No shared standard, each organisation manages its own logins. | Red | Single role based access model, enforced across all three systems. | Green | Objective B, Identity and Access |
| No unified audit trail across the three organisations | Each system logs access locally, no shared visibility. | Red | Shared audit log recording every access event, regardless of origin. | Amber | Objective C, Security Monitoring |
| Unclear breach ownership across more than one controller | No agreed lead organisation for a joint incident. | Amber | Joint incident protocol naming a lead organisation and notification timelines. | Green | Objective D, Response and Recovery |
| No data sharing agreement covering all three organisations | Sharing rests on informal understanding, not a signed agreement. | Red | Single tripartite agreement in place before going live. | Green | Objective E, Using and Sharing Information |
| Wider attack surface from newly connected systems | Each system assessed in isolation, no joint architecture review. | Amber | Joint risk assessment of the integration, signed off by each IT lead. | Amber | Objective A, Risk Management |
| Staff outside a person's usual care team can view her full history | Full record access granted to any authorised user by default. | Amber | Context sensitive access, summary view by default, full access on documented reason. | Green | Objective E, Using and Sharing Information |
| Retention periods differ across the three legacy systems | Each system retains records on its own local schedule. | Amber | Single retention schedule applied to the shared record. | Amber | Objective A, Governance |
| Individuals are not told their record is now shared | Privacy notices refer only to each organisation's own use of data. | Amber | Updated privacy notices, plus a joint communication before going live. | Green | Objective E, Using and Sharing Information |
| Subject access requests become more complex | No coordinated process for a request spanning more than one organisation. | Amber | Single coordinated process, with one nominated lead organisation. | Green | Objective E, Using and Sharing Information |
| Joint incident response has never been tested across all three | Each organisation has tested its own response separately. | Red | Joint tabletop exercise simulating a shared record breach before launch. | Amber | Objective D, Response and Recovery |

## Residual Risk, and What This Shows

Four risks stay amber even after mitigation: full audit alignment across three legacy systems, the wider attack surface created by connecting three previously separate systems, harmonising retention across those systems, and a joint incident response never actually tested together. None meet the bar for mandatory ICO consultation under Article 36 once the other six mitigations are in place, but they are tracked deliberately, not assumed away. This assessment would need formal sign off from a Data Protection Officer at each organisation before going live, reviewed within twelve months or sooner if scope changes.

Leah does not exist, but the pattern does. Three services, each careful on their own, become riskier the moment they are joined without also joining their governance.
