---
title: "Unified risk management, Explorer policies and Risk Insights (FortiCNAPP 26.3.0 admin guide)"
path: "user-pasted attachment e8810e15-attachment.txt"
url: "https://docs.fortinet.com/document/forticnapp/26.3.0/administration-guide/566100/creating-tuning-and-cloning-insights"
topic: product-overview
updated: unknown
source_modified_utc: unknown
ingested: 2026-10-22
sha1: f20ab20aa46e73b4fffa33cc263a25c3e3902dfc
status: needs-review
evidence: user-pasted-vendor-documentation
---

## Provenance

User-supplied text (12109 bytes) from the FortiCNAPP 26.3.0 administration guide. The text ends with two links (Creating, tuning and cloning insights; Creating remediation tickets) whose pages were NOT fetched or supplied, so those procedures are not covered. All features are labelled PREVIEW by the source. Original attachment unchanged.

## Key facts from the supplied source

- Unified risk management splits the console into Threat and Risk sections. Features: Risk Insights (QBL policies, FortiCNAPP AI Assist remediation, Jira tickets), Risk Alerts dashboard (alerts from LQL policies), Explorer queries saved in the query catalog, extra Risk Insights data when DSPM is enabled.
- Explorer policies are created from Explorer saved queries (Actions > Create policy). Unlike most policies (LQL-based, generate alerts) they are Explorer/QBL-based and generate risk insights. First insights appear within 24 hours of saving.
- Limit: 25 enabled custom Insights (Explorer policies you create or clone) per account, applied independently per account incl. sub-accounts; also enforced through API, CLI and Terraform. Fortinet-provided and disabled Insights do not count. At the limit you can edit existing ones but not create, clone or enable more; accounts already over the limit keep existing ones until below 25.
- Evaluation every six hours. A fixed risk stays Active until the next evaluation, then Detection status becomes Resolved (finding is not removed). "Last evaluated on" shows the last run.
- Recommended prerequisites: AI Assist (Settings > General), Jira alert channel, resource groups.
- Risk categories: Compliance (compliance violation filter), Data exposure (storage reachable by host/identity, host/identity with storage access, publicly exposed storage), Identity and access (identity resource), Vulnerability (vulnerability filter); otherwise uncategorized.
- Insights page: widgets (New risk insights, Detection status, Ticket assignment, MTTR); filter, search, group by Insight or Resource, sort. Table fields include Insight Risk Score (combined from resource finding scores), Detection status (Resolved only when all affected resource findings are resolved), Ticket assignment (No Ticket / Ticket Created / Resolved; Ticket Created does not mirror Jira status), Unresolved resources.
- Insight details: Risk context, Finding detection status, Finding ticket assignment, Impact across Top Accounts, Recommended remediation, Affected Resource Findings. Context panel tabs: Risk Factors, Findings (Compliance Violations, Vulnerabilities; "Insight Findings Only" toggle), Graph (View in Explorer), Tickets; actions View resource details and Create ticket.
- AI Assist remediation is shown when enabled, a response was generated, and either the policy has no remediation text or confidence > 0.6 (it then overrides policy remediation). Static policy remediation is shown when AI Assist is disabled, has no response, or confidence <= 0.6.

## Review flags

- Policy "begins generating risk insights within 24 hours" vs "evaluates policies every six hours / new risks within six hours": not reconciled in the source (likely first-run vs steady-state, unconfirmed).
- Source says "25 active Explorer policies" in one place and "25 enabled custom Insights per account" in another; treated as the same limit.
- Preview feature: behaviour and limits may change.

## Extraction limits

All supplied text readable. The AI icon glyph was not rendered in the paste. Linked pages not fetched.

## Full supplied text

Unified risk management
PREVIEW FEATURE: This section describes functionality that is currently in preview.

Unified risk management separates threat analysis from risk analysis to provide a more streamlined experience. With this feature enabled, the console is now divided into easily accessible Threat and Risk sections, offering tools for risk discovery, analysis, and remediation.
Features:
	•	Risk Insights: Leverage QBL policies to gain valuable insights on risks, powered by FortiCNAPP AI Assist. Additionally, create remediation tickets directly in the console using Jira integration.
	•	Risk Alerts: Alerts related to risk now display in the Risk Alerts dashboard, providing easier access to risk-related alerts surfaced by LQL policies.
	•	Explorer Queries: Save and reuse Explorer (QBL) queries in the query catalog, which can now be used to generate risk insights.
	•	DSPM integration: When DSPM is enabled, additional data is available in Risk Insights.
Creating Explorer policies
PREVIEW FEATURE: This section describes functionality that is currently in preview.
You can create Explorer policies to generate risk insights. See Risk Insights.
Explorer policies are created from Explorer saved queries.
Explorer policies are different from other kinds of FortiCNAPP policies. Most other policies are based on LQL queries and can be used to generate alerts. Explorer policies are based on Explorer queries and generate risk insights.
Important note on Explorer policies and insights
To ensure optimal performance, you are limited to a maximum of 25 active Explorer policies. Disabled policies do not count towards this limit.
If your organization requires more policies than this, please contact your support team to explore alternative solutions that meet your needs.
To create an Explorer policy:
	1	In Explorer, in the query builder, click Select a saved query and select a query from the list.
	2	Click Actions and select Create policy.
	3	Follow the process in Managing policies and click Save. The policy is added and begins generating risk insights within 24 hours.
Risk Insights
PREVIEW FEATURE: This section describes functionality that is currently in preview.
The Risk Insights dashboard lists policy-based risk insights.
Risk insights are produced by Explorer policies. Findings are generated for every resource that matches the policy criteria. Each finding represents a unique resource.
Insights can be filtered and sorted. You can drill down for more information about impacted resources and remediation options.
FortiCNAPP provides a set of predefined Explorer policies to generate insights. You can use these policies as they are or clone them to create your own policies. You can also create your own policies manually for fully customized insights.
From Risk Insights, you can do the following:
	•	View insights
	•	Create remediation tickets
	•	Create, tune, or clone insights
Recommended prerequisites
We recommend that you configure the following:
	•	AI Assist: Generative AI is used to provide tailored remediation suggestions. To take advantage of this feature, enable FortiCNAPP AI Assist in Settings > General. See FortiCNAPP AI Assist.
	•	Jira alert channel: The Creating remediation tickets feature requires a Jira alert channel integration. See Jira alert channel.
	•	Resource groups: Use resource groups to group resources into logical groups and for administration and access control. See Resource Groups.
Policy evaluation frequency
Risk Insights evaluates policies every six hours. New risks appear at the next evaluation, within six hours.
After you fix a risk, its finding stays Active until the next evaluation confirms the fix. Its Detection status then changes to Resolved. The finding is not removed.
Last evaluated on, at the top of the Risk Insights page, shows when the most recent evaluation ran.
Limitations
Each account can have up to 25 enabled custom Insights (Explorer policies that you create or clone). Fortinet-provided Insights and disabled custom Insights do not count toward this limit. The limit applies independently to each account, including sub-accounts within an organization. The same limit applies when you create or enable policies through the API, the CLI, or Terraform.
When the limit is reached, you can still edit existing custom Insights, but you cannot create, clone, or enable additional ones until an enabled custom Insight is disabled or deleted.
Accounts that already exceed the limit retain their existing custom Insights and evaluations, but must reduce the number of enabled custom Insights below 25 before creating or enabling new ones. If your organization requires more, contact your support team.
Risk categories
PREVIEW FEATURE: This section describes functionality that is currently in preview.
Risk insights can have the following categories:
	•	Compliance: This insight is generated by a policy with a compliance violation filter.
	•	Data exposure: This insight includes:
	•	Storage assets that can be accessed by a host or identity.
	•	A host or identity that can access storage assets.
	•	Publicly exposed storage assets.
	•	Identity and access: This insight is generated by a policy with an identity resource.
	•	Vulnerability: This insight is generated by a policy with a vulnerability filter.
Risk insights that do not meet any of the above conditions will appear uncategorized.
Viewing insights
PREVIEW FEATURE: This section describes functionality that is currently in preview.
To view risk insights, go to Insights.
Click an insight to view the insight details. See Viewing insight details.
Summary widgets
The following summary widgets are available:
	•	New risk insights: Shows active risk insights that do not yet have any tickets assigned to the affected resources.
	•	Insight detection status: Shows the count of active and resolved risk insights.
	•	Insight ticket assignment: Shows the count of risk insights by ticket assignment.
	•	Mean time to resolve (MTTR): Shows the overall mean time to resolve.
Filtering insights
Use the filters at the top of the page to limit the displayed insights.
The summary widgets provide summaries of specific filters. Click a summary value or filter icon to apply the filter to the insights list. Click the same filter again to remove the filter.
Searching insights
Use the search fields at the top of the tables to search for specific insights or resources.
Grouping insights
Use the Group by... links to group by Insight or Resource.
Sorting insights
Use the Sort button to change the sorting.
Risk insights table fields
PREVIEW FEATURE: This section describes functionality that is currently in preview.
The following fields are available in the insights table:
Field
Description
Accounts
The cloud accounts with access to the affected resources.
Actions
Provides available operations for this insight.
Created by
The creator of the insight policy.
Detection age
The length of time since the insight was first detected.
Detection status
The status of the detection, either Active or Resolved. An insight is Resolved when all affected resource findings have been resolved.
First detected
The date and time of the first detection of this insight.
Insight Risk Score
The combined risk score for this insight, calculated based on the risk scores of the resource findings.
Resource category
The categories of the affected resources.
Risk category
The categorization of the risks. See Risk categories.
Risk insight
The name and description of this insight.
Risk insight Id
The ID of this insight.
Ticket assignment
Indicates ticket assignment status, one of the following:
	•	No Ticket: No ticket has been created for these findings.
	•	Ticket Created: A ticket has been created. This does not reflect its status in Jira.
	•	Resolved: Findings are no longer detected, whether or not a ticket was created.
Unresolved resources
The number of unresolved resources compared with the total number of affected resources.
Viewing insight details
PREVIEW FEATURE: This section describes functionality that is currently in preview.

in the Risk Insights, click an insight to view the insight details.

The insight details page provides filtering, searching, and sorting options similar to the insights list page.

The following summary widgets are displayed:

Risk context: Provides a summary description of the risk. Click the more information icon to view more detail related to the risk score.

Finding detection status: Shows your related resource finding progress toward risk resolution, based on daily scans, updated at each evaluation, every six hours.

Finding ticket assignment: Shows whether tickets have been created for this insight's resource findings. It does not reflect the ticket status in Jira. See the Tickets tab in the finding.

Impact across Top Accounts: Shows the number of affected resources grouped by account.

Recommended remediation
The Recommended remediation section presents the actions you can take to remediate this risk.

AI Assist
When FortiCNAPP AI Assist is enabled, the remediation recommendations may be tailored to your specific context.

AI Assist remediation recommendations appear when:
You have enabled FortiCNAPP AI Assist. See FortiCNAPP AI Assist.

AI Assist has generated a response.

Either of the following is true:

The policy has no remediation instructions.

AI Assist is confident about its answer (a confidence score greater than 0.6) even if the policy already has remediation instructions.

Static remediation recommendations appear when:
FortiCNAPP AI Assist is disabled.

AI Assist has not generated a response.

The policy has remediation instructions and the AI Assist confidence is low (less than or equal to 0.6).

AI Assist remediation will override policy remediation when AI Assist is highly confident, even if the policy provides remediation steps.

An AI icon () identifies AI Assist-generated content. Hover over the icon to see additional context, such as when AI Assist content is being used as a fallback or when confidence is low.

Affected Resource Findings
The Affected Resource Findings table lists the resources affected by this risk. Click a resource finding to view more information about the resource in a context panel. See Affected resource context panel.

Affected resource context panel
PREVIEW FEATURE: This section describes functionality that is currently in preview.
In Risk Insights > Insight details, click an affected resource finding to view a context panel with more information about the resource.
Click View resource details to open the resource details page in Resource Inventory.
Click Create ticket to create a new Jira ticket for remediation of this risk. See Creating remediation tickets.
The context panel shows the following tabs:
	•	Risk Factors
	•	Findings
	•	Graph
	•	Tickets
Risk Factors
Shows the calculated risk score for this resource and details of the top contributing risk factors.
Findings
This tab shows the findings related to this resource, grouped into the following tabs:
	•	Compliance Violations: Compliance policy violations for this resource.
	•	Vulnerabilities: Vulnerabilities related to this resource. Click View all in Vulnerabilities to view all of the vulnerabilities for this resource in the Vulnerabilities dashboard.
In both tabs, disable Insight Findings Only or click Show all findings to view all of the findings for this resource including those outside of the scope of this risk insight. The resource may be affected by compliance violations or vulnerabilities that are not caught by the risk insight policy query.
Graph
View the graph for this resource. Click View in Explorer to open the graph in Explorer.
Tickets
View existing Jira remediation tickets that have been created for this resource finding. See Creating remediation tickets.

https://docs.fortinet.com/document/forticnapp/26.3.0/administration-guide/566100/creating-tuning-and-cloning-insights

https://docs.fortinet.com/document/forticnapp/26.3.0/administration-guide/508764/creating-remediation-tickets
