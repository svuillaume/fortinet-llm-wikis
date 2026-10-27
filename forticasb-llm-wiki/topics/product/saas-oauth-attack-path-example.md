---
title: SaaS OAuth token abuse: Salesloft/Drift to Salesforce attack path
summary: The attack path used in the enablement decks to illustrate third-party OAuth risk, and the controls FortiCASB-SSPM maps to it.
sources: [deck-techtalk-forticasb-sspm-v1-1, deck-intro-to-forticasb-sspm-nov25]
updated: 2026-10-26
status: current
---

# SaaS OAuth token abuse: Salesloft/Drift to Salesforce

The decks use a 2025 incident as a worked example (speaker notes: "Last summer 2025"). Details come from the deck slides and notes only; no external incident reports were consulted.

## Attack path as shown
1. A malicious actor exploits OAuth and over-scoped permissions to retrieve sensitive CRM data and harvest embedded credentials.
2. The **Drift app connector**: compromised OAuth tokens stored in Drift (Salesloft) are used to authenticate into **Salesforce**.
3. Data exfiltration: queries issued via SQL and bulk export; exported datasets parsed for AWS keys (AKIA), Snowflake tokens, passwords and org logins; objects touched include Users, Accounts, Opportunities and Cases. Deletion of jobs to evade detection.
4. Secrets reused to access downstream systems; Drift email OAuth tokens misused to access a small set of Google Workspace mailboxes.
5. Note on the slide: cloud behavior analytics may not detect targeted queries.

## Mechanics (speaker notes)
- A SaaS app (Drift/Salesloft) requests an OAuth token from Salesforce; the token is stored in the SaaS platform for the integration.
- If the token is stolen, an attacker uses it to access Salesforce and acts as the user/integration, bypassing normal login and password checks.
- Takeaway: a compromised OAuth token gives full access within the integration's scope; immediate revocation and audit are required.

## Mapped platform capabilities
- Inventory of third-party apps and tokens with permissions, scopes, expiration and last-active data; filter by sensitive access, inactivity, token expiration. See [Third-party apps](../sspm-user-guide/third-party-apps.md).
- Revoke access to apps and tokens (Microsoft, Google, Okta, Salesforce, Atlassian) from the platform. Same page.
- The slide states "FortiCASB-SSPM automatically detects malicious third-party connections and revokes their access". The User Guide documents manual or workflow-driven revocation; whether revocation is fully automatic by default: not found in sources.
- Saved filters ("Save as Risk") and [Workflows](../sspm-user-guide/workflows.md) can alert on new sensitive or GenAI-based third-party apps.

`[src: deck-techtalk-forticasb-sspm-v1-1, slide 8]`, `[src: deck-intro-to-forticasb-sspm-nov25, slide 3]`

## Related
- [Product overview](overview-and-use-cases.md)
- [Third-party apps](../sspm-user-guide/third-party-apps.md)
- [CASB, SSPM and related concepts](casb-sspm-concepts.md)
