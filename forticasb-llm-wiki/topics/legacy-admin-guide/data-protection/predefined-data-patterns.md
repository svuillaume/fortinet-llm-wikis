---
title: Predefined Data Patterns
summary: Predefined DLP data patterns in legacy FortiCASB: personal identity, financial, and malware/ransomware categories.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Predefined Data Patterns

Located at Data Protection > Policies > Data Patterns > Predefined tab. Patterns classify private and confidential data per regulatory requirements; FortiCASB alerts administrators on SaaS activity on files matching them. In 2023 additional patterns were added with FortiGuard support, for "a total of 113 data patterns with 3 pattern categories". Maximum uncompressed/compressed file size supported: 20 MB. Latest updates: FortiGuard DLP updates.

Count oddity: the guide also states 34 "basic" predefined patterns (default policy) and 147 predefined patterns ([data-security-policy.md](data-security-policy.md)); the 113 figure is the only one tied to this section. The list of the 34 basic patterns is not found in sources. [src: forticasb-admin-guide-24-4-b, p.387]

## Personal Identity Information
Scanned during policy scans; alert when the pattern is accessed.

### Personal identity numbers
| Pattern | Description |
|---|---|
| DLP Birthdate Pattern | Birthdate |
| DLP SSN Pattern | United States social security number |
| DLP Polish Social Security Number Pattern | Poland social security number |
| DLP CN Resident Identity Pattern | China resident identity number |
| DLP Email Address Pattern | Email address |

### Passport numbers
| Pattern | Description |
|---|---|
| DLP USA/Germany Passport Number Pattern | United States and Germany passport number |
| DLP JP Passport Number Pattern | Japan passport number |
| DLP AU Passport Number Pattern | Australia passport number |
| DLP UK Passport Number Pattern | United Kingdom passport number |
| DLP CA Passport Number Pattern | Canada passport number |
| DLP CN Passport Number Pattern | China passport number |
| DLP FR Passport Number Pattern | France passport number |
[src: forticasb-admin-guide-24-4-b, p.388]

### International Bank Account Number (IBAN)
| Pattern | Description |
|---|---|
| DLP German IBAN Pattern | Germany International Bank Account Number |
| DLP Italian IBAN Pattern | Italian IBAN |
| DLP Spanish IBAN Pattern | Spanish IBAN |
| DLP Swedish IBAN Pattern | Swedish IBAN |
| DLP Swiss IBAN Pattern | Swiss IBAN |
| DLP UK IBAN Pattern | United Kingdom IBAN |
[src: forticasb-admin-guide-24-4-b, p.389]

### Driver license
Non-US/Canada:
| Pattern | Description |
|---|---|
| DLP CN Driver License Pattern | China driver's license number |
| DLP UK Driver License Pattern | United Kingdom driver's license number |

United States (pattern name `DLP US <XX> Driver License Pattern`; description "United States <state> driver's license number"):
| Code | State/District |
|---|---|
| AL | Alabama |
| AK | Alaska |
| AZ | Arizona |
| AR | Arkansas |
| CA | California |
| CO | Colorado |
| CT | Connecticut |
| DE | Delaware |
| DC | Washington DC |
| FL | Florida |
| GA | Georgia |
| HI | Hawaii |
| ID | Idaho |
| IL | Illinois |
| IN | Indiana |
| IA | Iowa |
| KS | Kansas |
| KY | Kentucky |
| LA | Louisiana |
| ME | Maine |
| MD | Maryland |
| MA | Massachusetts |
| MI | Michigan |
| MN | Minnesota |
| MS | Mississippi |
| MO | Missouri |
| MT | Montana |
| ND | North Dakota |
| NE | Nebraska |
| NV | Nevada |
| NH | New Hampshire |
| NJ | New Jersey |
| NM | New Mexico |
| NY | New York |
| NC | North Carolina |
| OH | Ohio |
| OK | Oklahoma |
| OR | Oregon |
| PA | Pennsylvania |
| RI | Rhode Island |
| SC | South Carolina |
| SD | South Dakota |
| TN | Tennessee |
| TX | Texas |
| UT | Utah |
| VT | Vermont |
| VA | Virginia |
| WA | Washington |
| WV | West Virginia |
| WI | Wisconsin |
| WY | Wyoming |

Canada (pattern name `DLP CA <XX> Driver License Pattern`; description "Canada <province> driver's license number"):
| Code | Province/Territory |
|---|---|
| AB | Alberta |
| BC | British Columbia |
| MB | Manitoba |
| NB | New Brunswick |
| NL-1 | Newfoundland and Labrador |
| NL-2 | Newfoundland and Labrador |
| NT | Northwest Territories |
| NS | Nova Scotia |
| NU | Nunavut |
| ON | Ontario |
| PE-1 | Prince Edward Island |
| PE-2 | Prince Edward Island |
| QC | Quebec |
| SK | Saskatchewan |
| YT | Yukon |

[src: forticasb-admin-guide-24-4-b, p.389-393]

## Financial Information
| Pattern | Description (as printed) |
|---|---|
| DLP JCB Pattern | JCB credit card number |
| DLP Maestro Card Pattern | Maestro debit card number |
| DLP MasterCard Pattern | Master credit card number |
| DLP American Express Pattern | American Express credit card number |
| DLP Diners Club Card Pattern | Diners Cloud [sic] credit card number |
| DLP Discover Card Pattern | Discover credit card number |
| DLP China Union Pay Pattern | China Union Pay credit card number |
| DLP Visa Credit Card Pattern | Visa credit card number |
| DLP BC Global Credit Card Pattern | Korean BC credit card number |
| DLP Carte Blanche Credit Card Pattern | Carte Blanche credit card number |
| DLP Insta Payment Credit Card Pattern | Instant payments are credit transfers that make funds available in a payee's account within ten seconds of a payment order being made |
| DLP Korean Local Credit Card Pattern | Korean local credit card number (Samsung, Lotte, Hyundai, Hana, BC, NG, Shinhan, and KB) |
| DLP Laser Credit Card Pattern | Laser was primarily an electronic point of sale debit card, but could also be used by telephone and internet, at ATMs and to pay regular bills by direct debit |
| DLP Solo Credit Card Pattern | Solo credit card number |
| DLP Switch Credit Card Pattern | Switch credit card number |
| DLP CA Insurance Number Pattern | Canadian Insurance number |
| DLP UK Insurance Number Pattern | United Kingdom Insurance number |
| DLP VSMC Pattern | Victoria Secret Master Card |
| DLP Australia SWIFT Code Pattern | Australia SWIFT code number |
| DLP China SWIFT Code Pattern | China SWIFT code number |
| DLP Germany SWIFT Code Pattern | Germany SWIFT code number |
| DLP France SWIFT Code Pattern | France SWIFT code number |
| DLP Japan SWIFT Code Pattern | Japan SWIFT code number |
| DLP United Kingdom SWIFT Code Pattern | United Kingdom SWIFT code number |
| DLP USA SWIFT Code Pattern | United States SWIFT code number |
[src: forticasb-admin-guide-24-4-b, p.393-395]

## Malware and Ransomware
| Pattern | Description |
|---|---|
| Ransomware Encrypted File Detection Pattern | Scans for ransomware encrypted files utilizing Fortinet Security Fabric |
| AV Scan Pattern | Scans for malware and virus utilizing Fortinet Security Fabric |
[src: forticasb-admin-guide-24-4-b, p.395]

## Related
- [customized-data-patterns.md](customized-data-patterns.md)
- [data-security-policy.md](data-security-policy.md)
- [policy-match-criteria.md](policy-match-criteria.md)
