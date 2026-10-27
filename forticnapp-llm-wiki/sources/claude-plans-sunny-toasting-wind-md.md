---
title: Route Risk Hunting through on-device WebGPU
path: /Users/svuillaume/.claude/plans/sunny-toasting-wind.md
topic: lql
updated: 2026-09-18
size: 8255
sha1: 04681db94268
status: current
---

**Original path:** `/Users/svuillaume/.claude/plans/sunny-toasting-wind.md`

**Topic:** [[lql]]

## Summary (first paragraph of source)

The Admin menu's "Server" dropdown currently only lists **Bifrost** and **Local (llama-cpp)** — both server-side gateways that `serve.py` proxies to. The user wants a third option, **On-device (WebGPU)**, so all of Risk Hunting (LQL Builder generation, FortiCNAPP Search, and the CVE/Attack Surface AI analysis) can run entirely through the already-loaded WebLLM engine in the browser, with no server
