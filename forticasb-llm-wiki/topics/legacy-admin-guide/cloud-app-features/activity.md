---
title: Activity
summary: Activity page: map, filters, alert correlation, Microsoft app integration and Google third-party app verification status.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Activity

FortiCASB monitors and tracks user data traffic and activities on cloud platforms. The Activity page has a map of approximate geolocations of events and an activities list. Screenshots were not extracted.

## Activity map options

- **Activity**: click an activity bubble to show activities at that location.
- **Move**: click and drag the map.
- **Zoom**: buttons at the bottom-right corner.
- **Refresh**: click Refresh to refresh the map.

[src: forticasb-admin-guide-24-4-b, p.458]

## Filter example

1. Click the **+Add Filter** drop-down.
2. Select filter type **Activity**.
3. Scroll to an activity type, for example **Access File**.
4. Click **Search**; only "Access File" activities in the time range are shown.

[src: forticasb-admin-guide-24-4-b, p.459-460]

## Activity alert correlation

One activity can trigger multiple alerts from different policies. Example: the Google Workspace event "Upload File" triggered 4 alerts; clicking the alert button opens Alert Overview, which showed 4 DLP policies: DLP USA/Germany Passport Number Policy, DLP UK Passport Number Policy, DLP Birthday Policy, and DLP SSN Policy. Daily activities can be compiled into Activity reports (guide: "Generate Activity Report", p.303). [src: forticasb-admin-guide-24-4-b, p.460]

## Microsoft app integration (Office 365 only)

Under **Office 365 > Activity**, the **App** column shows documents located in Microsoft Yammer or Microsoft Teams. [src: forticasb-admin-guide-24-4-b, p.461]

## Google third-party app verification (Google Workspace only)

Third-party apps under Google Workspace are reviewed by Google for security and privacy compliance; unverified apps are subject to restrictions. The **App** column in Activity reflects verification status.

| Status shown | Description |
|---|---|
| App name (shown as "(App Name)") | The app has not gone through Google verification. |
| Unidentified | Can be one of Google Docs, Sheets, Slides, Forms, Drawing, etc. |
| App name (icon) with no status | The app is verified by Google. |

[src: forticasb-admin-guide-24-4-b, p.461-462]

## Related

- [Alerts](alerts.md)
- [Files](files.md)
- [Yammer integration](yammer-integration.md)
- [Cloud application features index](index.md)
