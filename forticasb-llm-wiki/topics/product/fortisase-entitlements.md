---
title: FortiSASE entitlements and order examples
summary: How FortiCASB entitlement works with FortiSASE Standard, Advanced and Comprehensive, which capabilities stay in FortiOS/FortiSASE, and the three worked order examples.
sources: [forticasb-commercial-platform-update-v1-5, deck-tdm-presentation-casb, deck-forticasb-sales-unofficial-2026-09]
updated: 2026-10-26
status: current
---

# FortiSASE entitlements and order examples

## Entitlement by FortiSASE tier

| FortiSASE tier | FortiCASB entitlement | Notes |
|---|---|---|
| Standard | **None.** Includes inline CASB capabilities delivered by FortiOS. | Customers needing the full FortiCASB service buy a standalone FortiCASB subscription or upgrade to Advanced/Comprehensive. Existing Standard customers with an already activated FortiCASB tenant are honored until the end of the current licence period. |
| Advanced | Full FortiCASB entitlement | If more SaaS users need FortiCASB than the FortiSASE licence covers, the excess users are licensed through the applicable FCSSM-1278 band. |
| Comprehensive | Full FortiCASB entitlement | Same excess-user rule. |

## Division of function
- Inline application visibility and enforcement remain FortiOS / FortiSASE capabilities.
- API-based SaaS connections, posture monitoring (SSPM), activity monitoring and data scanning (DLP) are delivered by FortiCASB.
- FortiCASB monitors and enforces the **pooled scanning allowance**.

`[src: forticasb-commercial-platform-update-v1-5]`

## Worked order examples (annual list prices from the source)

1. **200 FortiSASE Standard users + 500 FortiCASB users.** Standard has no FortiCASB entitlement, so all 500 are licensed separately.
   - 200 x `FC2-10-EMS05-547-02-12` (FortiSASE Standard, 50-499 users) at $90 = $18,000
   - 500 x `FC2-10-FCSSM-1278-02-12` at $59 = $29,500
   - **Total $47,500**
2. **200 FortiSASE Advanced users + 1,000 FortiCASB users.** Advanced includes FortiCASB for 200 users; 800 remain.
   - 200 x `FC2-10-EMS05-676-02-12` (Advanced, 50-499 users) at $117 = $23,400
   - 800 x `FC2-10-FCSSM-1278-02-12` at $59 = $47,200
   - **Total $70,600**
3. **500 FortiSASE Comprehensive users + 3,000 FortiCASB users.** Comprehensive includes FortiCASB for 500 users; 2,500 remain (band 2,000-9,999).
   - 500 x `FC3-10-EMS05-759-02-12` (Comprehensive, 500-1,999 users) at $208 = $104,000
   - 2,500 x `FC3-10-FCSSM-1278-02-12` at $52 = $130,000
   - **Total $234,000**

`[src: forticasb-commercial-platform-update-v1-5]`

The unofficial Sept 2026 sales deck confirms the same entitlement model (no FortiCASB entitlement on Standard; FortiCASB user licenses included with Advanced and Comprehensive; standalone add-on SKUs for Standard and for extra capacity) and its three BOM examples mirror the three above (same SKUs and quantities, no prices in the deck; the deck uses the `-02-DD` suffix). It adds that the **FortiSASE dashboard integration** is only included in the Advanced and Comprehensive tiers; a Standard tier customer buys standalone and accesses the standalone FortiCloud portal. `[src: deck-forticasb-sales-unofficial-2026-09, slides 23, 25-29]`

## Inline and API CASB together
The earlier TDM deck describes "FortiGuard CASB" as a dual-mode offering (inline via FortiGate/FortiSASE plus API CASB via FortiCASB) with ordering guides for SASE and ZTNA. See [Inline vs API CASB](inline-vs-api-casb.md). That deck predates the Sept 2026 entitlement rules; where they differ, the v1.5 rules apply. `[src: deck-tdm-presentation-casb, slides 40-42]`

## Related
- [Licensing and SKUs](licensing-and-skus.md)
- [Inline vs API CASB](inline-vs-api-casb.md)
- [Product names and the rebrand](naming-and-rebrand.md)
