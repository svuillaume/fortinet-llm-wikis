---
title: Product names and the FortiCASB rebrand
summary: Which product each FortiCASB-related name refers to (Legacy 24.4.b, FortiCASB-SSPM, FortiCASB Basic, FortiCASB new, FortiGuard CASB, Suridata) and how they map.
sources: [forticasb-commercial-platform-update-v1-5, forticasb-data-sheet-v0-10, forticasb-admin-guide-24-4-b, forticasb-sspm-user-guide-2026-02, suridata-user-guide, deck-tdm-presentation-casb, deck-intro-to-forticasb-sspm-nov25, expert-talks-forticasb-sspm-suridata, deck-forticasb-sales-unofficial-2026-09]
updated: 2026-10-26
status: current
---

# Product names and the FortiCASB rebrand

Several names appear across the source documents. They refer to different platforms or editions. Read this page first when a document says "FortiCASB".

## Name map

| Name in sources | What it is | Where documented |
|---|---|---|
| **FortiCASB Legacy** (also "FortiCASB", "FortiCASB 24.4.b") | The original API-based CASB platform with business units, cloud-account onboarding wizards, data-security policies, FortiAnalyzer integration, REST API. Portal: `www.forticasb.com` (to be presented as the "FortiCASB Legacy portal"). SKUs FCASB-145 and FCASB-307. | [Legacy Admin Guide](../legacy-admin-guide/introduction-and-features.md) `[src: forticasb-admin-guide-24-4-b, p.17-21]`, `[src: forticasb-commercial-platform-update-v1-5]` |
| **FortiCASB-SSPM** | The newer agentless SaaS security platform (SaaS Graph, third-party app control, identities, workflows, App Store of >100 connectors). Document set titled "FortiCASB-SSPM User Guide" (dated Feb 10, 2026). The predecessor document, "User Guide to Suridata's SaaS Security Platform", has near-identical content. | [SSPM User Guide section](../sspm-user-guide/index.md) `[src: forticasb-sspm-user-guide-2026-02]`, `[src: suridata-user-guide]` |
| **FortiCASB (new name)** | Announced new name for FortiCASB-SSPM. It "will become the primary FortiCASB platform"; new business is directed to it. Added to the FortiCloud portal. | `[src: forticasb-commercial-platform-update-v1-5]` |
| **FortiCASB (Basic)** | An edition listed next to FortiCASB-SSPM in the Nov 2025 / 2026 enablement decks (SKU family 1277): shadow SaaS discovery, data discovery, DSPM, Gen-AI identification; no SaaS Graph, third-party control, identity posture, workflows or SSPM. Not mentioned in the Sept 2026 commercial update. | [Editions](legacy-vs-sspm-comparison.md), `[src: deck-intro-to-forticasb-sspm-nov25]` |
| **FortiGuard CASB** | Dual-mode CASB offering combining inline CASB (FortiGate/FortiSASE) with API CASB (FortiCASB), licensed with ZTNA/SASE. | [Inline vs API CASB](inline-vs-api-casb.md) `[src: deck-tdm-presentation-casb]` |
| **Suridata** | Name in the predecessor user guide and in speaker notes of some decks (for example "Suridata tracks which plugins are in use"). The unofficial Sept 2026 sales deck still uses the Suridata domain for the dedicated tenant URL (`CustomerName.app.suridata.ai`). How Fortinet obtained the technology is **not found in sources**. | `[src: suridata-user-guide]`, `[src: deck-techtalk-forticasb-sspm-v1-1]`, `[src: deck-forticasb-sales-unofficial-2026-09, slide 13]` |

## Direction stated in the Sept 2026 commercial update (v1.5)

- FortiCASB-SSPM will be renamed FortiCASB and becomes the primary platform; the existing platform is referred to as FortiCASB Legacy.
- FCASB-145 and FCASB-307 SKUs are not converted or reused for FortiCASB.
- A formal End of Order / End of Support process will be initiated separately; no dates are to be communicated until approved and published (see [Lifecycle and migration](lifecycle-and-migration.md) for a conflicting dated notice).
- Existing Legacy customers keep support under active subscriptions; migration is recommended but not required until lifecycle guidance is issued.
- FortiCASB is added to the FortiCloud portal; `www.forticasb.com` is presented as the Legacy portal.
- If an opportunity depends on a capability that may not yet exist in FortiCASB, the CSE team is to be contacted before committing a platform or migration approach.

`[src: forticasb-commercial-platform-update-v1-5]`

## Naming usage in this wiki

- "FortiCASB Legacy" = the Admin Guide 24.4.b platform.
- "FortiCASB-SSPM" = the platform documented by the SSPM User Guide; the same platform is called "FortiCASB" in the Sept 2026 data sheet draft `[src: forticasb-data-sheet-v0-10]`.
- Source documents are not always consistent about which one they mean; each wiki page states its source.

## Related
- [Product overview and use cases](overview-and-use-cases.md)
- [Licensing and SKUs](licensing-and-skus.md)
- [Lifecycle and migration](lifecycle-and-migration.md)
- [Legacy vs SSPM comparison](legacy-vs-sspm-comparison.md)
