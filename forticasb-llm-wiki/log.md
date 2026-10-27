# FortiCASB LLM Wiki - log

Append-only. One entry per action: date, action, source, pages touched.

## 2026-10-26 - initial build
- **Action:** scope, inventory, ingest, compile, lint.
- **Scope:** all FortiCASB / FortiCASB-SSPM documents found under the home folder (read-only search; originals untouched) plus the FortiCASB 24.4.b Admin Guide. Output: this folder.
- **Sources ingested (24 stubs in `sources/`):** Admin Guide 24.4.b (574 pp.), FortiCASB-SSPM User Guide (Feb 2026), Suridata user guide, commercial and platform update v1.5, legacy lifecycle notice, Expert Talks deck, data sheet draft v0.10 (page 1 of 6 only), 8 enablement decks (deduplicated by hash), 1 xlsx, 9 HTML competitive reports/newsletters. See `sources/_skipped.md` for what was left out (video, zip copies, out-of-scope FortiCNAPP material).
- **Pages written:** `topics/product` (11), `topics/sspm-user-guide` (11), `topics/competitive` (8), `topics/legacy-admin-guide` (core 11, onboarding 22, overview-features 20, data-protection 10, cloud-app-features 12, api 10, appendix 6) - see `index.md` for the full list.
- **Conflicts recorded (status: needs-review):** SKU names and prices (decks vs commercial update v1.5); legacy end-of-order date vs "no dates to be communicated"; minimum users; competitive scores, prices, Gartner references and the Suridata acquisition date.
- **Known extraction limits:** screenshots not extracted; some PDF tables lost column alignment and were reconstructed (flagged on pages); heatmap grids in the HTML reports are missing from extracted text; data sheet snapshot covers only its first page.
- **Lint:** 0 broken links, 0 missing frontmatter fields, 0 unknown source references.

## 2026-10-26 - ingest
- **Action:** ingest new PPTX (unofficial, no existing stub matched).
- **Source:** FortiCASB Sales Deck-Unofficial-9-2026-jhurley.pptx (31 slides, 15 with notes) -> sources/deck-forticasb-sales-unofficial-2026-09.md (sha256 19f71609...).
- **Pages touched:** licensing-and-skus.md, fortisase-entitlements.md, naming-and-rebrand.md, roadmap-and-faq.md, connector-types-and-permissions.md, overview-and-use-cases.md, index.md.
- **Conflicts flagged:** sales deck BOM band labels ("250-2,499" / "2,500+") disagree with its own SKU table and the v1.5 bands; deck note says Data Scanning SKUs were removed 9/4/2026, in tension with v1.5's data-scanning model under development.
- **Not extracted:** screenshot-based slides (How to Order, onboarding screenshots 15-19) carry no text.

## 2026-10-26 - review
- **Action:** user approved (remove) review queue IDs 3-12 via /llm-wiki-lint args; status set needs-review -> current.
- **Files changed:** competitive/{vs-microsoft-defender-for-cloud-apps, pricing-benchmarks, newsletter-digest-2026, market-landscape, vendor-profiles, fortinet-fit-and-gaps, capability-matrix, index}.md, product/{licensing-and-skus, roadmap-and-faq}.md (frontmatter status only).
- **Retained caveats:** recorded conflicts, evidence flags, missing heatmap grids, unshipped roadmap items, and the disagreement register remain documented on the pages; approval accepted them without resolving them.
- **Still queued:** product/lifecycle-and-migration.md (dated EOL notice vs v1.5 "no dates"); sources vs-defender-for-cloud-apps-v1.md and v2.md (superseded by -2026-10).
