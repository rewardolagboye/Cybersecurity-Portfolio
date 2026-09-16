# Password and Authentication Policy Review

**Alderbridge Financial Services Ltd** — a structured gap review against NIST, CIS and ISO 27001 benchmarks

Prepared by Reward Oladejo-Olagboye, 10 August 2026. Standards referenced: NIST SP 800 63B, CIS Controls v8, ISO/IEC 27001:2022

## For the Board: What You Need to Know

We reviewed our current password and login rules against recognised international good practice, to check whether they still hold up. The short answer is that our rules are reasonable but out of date, built around ideas once considered best practice, such as forcing everyone to change their password every 90 days, that current expert guidance has moved away from because it does not meaningfully improve security and often leads to weaker, more predictable passwords.

The two most important gaps: extra login verification is only required when staff work remotely, and should apply consistently regardless of location; and new passwords are not checked against lists of passwords already known to have been leaked elsewhere, a quick, low cost check that meaningfully reduces risk. None of the recommended changes require rebuilding the policy from scratch.

## Purpose and Scope

This document reviews Alderbridge's existing Password and Authentication Policy against current industry guidance, covering staff, contractors and third parties accessing Alderbridge systems. It does not extend to physical access control or customer facing authentication. The review was prompted in part by a related finding in the organisation's cybersecurity risk register, which identified inconsistent multi factor authentication enforcement as a high priority risk.

## Review Methodology

The policy was assessed against three reference sources: NIST Special Publication 800 63B (Digital Identity Guidelines), CIS Controls version 8 Control 5 and Control 6, and ISO/IEC 27001:2022 Annex A controls A.5.17 and A.8.5. Each review question and gap was RAG rated, Red for not met, Amber for partial coverage, Green for fully met.

## Policy Under Review

The current policy requires: a minimum 8 character password; at least one uppercase, one lowercase, one number and one special character; a 90 day change cycle; no reuse of the previous 5 passwords; account lockout after 5 failed attempts; MFA for remote access only; no sharing or writing down of passwords; and individual responsibility for credential confidentiality.

## Structured Review Questions and Findings

| No. | Review Question | RAG | Notes |
|---|---|---|---|
| 1 | Minimum and maximum length aligned to current guidance? | Medium | Minimum is 8 characters, no maximum set, passphrases not encouraged. |
| 2 | MFA required for all account types? | High | Required for remote access only, on premises and privileged sessions not covered. |
| 3 | Passwords screened against known breached credential lists? | High | No screening mechanism referenced anywhere. |
| 4 | Standard vs privileged account requirements separated? | High | All account types subject to the same uniform requirements. |
| 5 | Service, system or application account credentials addressed? | High | Scope covers user accounts only. |
| 6 | Shared accounts prohibited, default credentials changed? | Medium | Sharing discouraged informally only, defaults not addressed. |
| 7 | Rotation based on risk or compromise rather than a fixed interval? | High | Rotation fixed at 90 days regardless of any compromise indicator. |
| 8 | Approved password manager referenced? | High | No guidance provided. |
| 9 | Lockout duration and recovery process defined? | Medium | Threshold defined, no duration or recovery process specified. |
| 10 | Named owner and review cycle assigned? | High | No ownership or review cadence stated. |
| 11 | Aligned with a recognised external standard? | Medium | Reflects a dated composition and rotation model. |

## Gap Analysis

| ID | Area | Gap | Severity | Recommendation |
|---|---|---|---|---|
| G01 | Password Rotation | Fixed 90 day rotation regardless of compromise indicators. | Medium | Replace with rotation triggered by evidence of compromise. |
| G02 | MFA | Not mandated for all account types, remote access only. | High | Extend mandatory MFA to all privileged, admin and on premises sessions. |
| G03 | Minimum Length | 8 characters, no maximum, no passphrase encouragement. | Medium | Raise to at least 12 characters, support up to 64, encourage passphrases. |
| G04 | Breached Password Screening | No screening at point of creation or change. | High | Implement automated screening against a breached password database. |
| G05 | Service Accounts | No distinct requirements for service or system credentials. | Medium | Add a dedicated section on service account vaulting and rotation ownership. |
| G06 | Password Manager | Policy is silent on approved tools. | Low | Recommend and provide an approved enterprise password manager. |
| G07 | Lockout and Recovery | No lockout duration or verified recovery process. | Low | Define a specific lockout duration and auditable recovery process. |
| G08 | Shared and Default Credentials | Not explicitly prohibited or addressed. | High | Prohibit shared credentials, require default passwords changed before production. |
| G09 | Privileged Account Differentiation | Same requirements for standard and privileged accounts. | High | Introduce elevated requirements including shorter timeouts and mandatory MFA. |
| G10 | Ownership and Review Cadence | No review frequency or accountable owner stated. | Low | Assign a named policy owner and mandate an annual review cycle. |

## Recommended Redline Summary

Replace fixed 90 day rotation with compromise triggered rotation (G01); extend MFA to all privileged, administrative and on premises sessions (G02, G09); raise minimum length to 12 characters and encourage passphrases (G03); introduce automated breached password screening (G04); add a service account clause (G05); recommend an approved password manager (G06); define lockout duration and recovery process (G07); prohibit shared accounts and default credentials in production (G08); assign a named owner and annual review cycle (G10).

## Conclusion

The current policy reflects an older composition and rotation based model that has largely been superseded by current guidance. None of the identified gaps require a wholesale rewrite. Implementing the ten recommendations would bring the policy substantially in line with NIST, CIS and ISO 27001 expectations, and directly address the MFA risk already flagged in the organisation's risk register.

## Reference Standards Consulted

**NIST SP 800 63B**, Digital Identity Guidelines, covering authentication and credential lifecycle management. **CIS Controls v8**, Control 5 Account Management and Control 6 Access Control Management. **ISO/IEC 27001:2022**, Annex A.5.17 Authentication Information and A.8.5 Secure Authentication.
