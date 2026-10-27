---
title: Customized Data Patterns
summary: Creating customized DLP data patterns in legacy FortiCASB using regex (PCRE) or Exact Data Match CSV datasets.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Customized Data Patterns

User-defined DLP patterns applied to a Data Security Policy like predefined ones. Located at Data Protection > Policies > Data Patterns > Customized Data Pattern tab. Matching is driven by Regex/PCRE (Perl Compatible Regular Expressions). [src: forticasb-admin-guide-24-4-b, p.395]

## Configurable parameters
| Field | Description |
|---|---|
| Name | Name of the data pattern |
| Description | Description of the data pattern |
| Category | Data category from the list |
| Uncompressed File Size | Upper bound of an object size, in MB, for a full content scan |
| Compressed File Size | Upper bound of a zip file size, in MB, for a full content scan |
| Regex Context | Regex to search for a specific string |
[src: forticasb-admin-guide-24-4-b, p.396]

## Exact Data Match (EDM) category
EDM scans for specific sensitive data against a predefined dataset supplied as a CSV file uploaded when creating the pattern.

Characteristics:
- A match occurs only if the sensitive data matches the dataset exactly.
- Symbols in the dataset, as well as `", . And`, must match the scanned data exactly.
- With a matching threshold, an alert triggers when the number of matched values from the CSV is equal to or greater than the threshold.

CSV requirements:
- No header row.
- English (Latin script) only.
- Maximum 120 rows and 30 columns per data set.
- RFC-4180 format recommended.
- First Normal Form recommended: atomic values per column (e.g. first and last name in separate columns; city and zip code in separate columns).

Example data (the guide's table layout was garbled in text extraction; this reconstruction of four rows is probable but unverified): Jason, Valentino, 1204 Jefferson St., Riverside, CA, 92504; Marry, Baxter, 415 W Willow Grove Ave, Philadelphia, PA, 19118; David, Solace, 555 Pierce Street APT #123, Albany, CA, 94706; Thomas, Jefferson, 1600 Pennsylvania Avenue NW, Washington, DC, 20500.
[src: forticasb-admin-guide-24-4-b, p.396-397]

## Example: Regex (Brazilian CPF)
Monitors for the 11-digit Brazilian taxpayer ID in format xxx.xxx.xxx-xx.
1. Go to Data Protection > Policies > Data Pattern and click the **Customized** tab.
2. Click **+ADD NEW**.
3. Data Pattern Name: `Brazil CPF`.
4. Description: `Brazilian taxpayer identification code with numerical format in xxx.xxx.xxx-xx`.
5. Category: `Financial Information`.
6. Max Uncompressed File Size and Max Compressed File Size: default `10MB`.
7. Regex (PCRE):
```
^\d{3}\.\d{3}\.\d{3}\-\d{2}$
```
8. Click **Add Customized Data Pattern**.

The pattern can then be added and enabled in a Data Security Policy.
[src: forticasb-admin-guide-24-4-b, p.397-398]

## Example: Exact Data Match
First create a CSV file named `Group1EDM.csv` with the content described above (four rows; garbled in extraction, see note).
1. Go to Data Protection > Policies > Data Pattern and click the **Customized** tab.
2. Click **+ADD NEW**.
3. Data Pattern Name: `Group-1-EDM`.
4. Description: `Target group for EDM search`.
5. Category: **Exact Data Match**.
6. Max Uncompressed File Size and Max Compressed File Size: default `10MB`.
7. CSV File: browse and upload the CSV.
8. Matching Threshold: press **+** to select `2`.
9. Click **Add Customized Data Pattern**.

With threshold 2, any 2 cell values matching between the CSV and scanned data trigger a DLP alert. Example: "Thomas" and "Albany" both found in the file triggers an alert; only "Thomas" does not.
[src: forticasb-admin-guide-24-4-b, p.398-399]

## Gaps
Guide p.400 is blank. Menu path is written both as "Data Pattern" and "Data Patterns" in the guide.

## Related
- [predefined-data-patterns.md](predefined-data-patterns.md)
- [data-security-policy.md](data-security-policy.md)
- [index.md](index.md)
