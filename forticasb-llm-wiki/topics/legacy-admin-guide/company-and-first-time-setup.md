---
title: Company Management and First Time Setup
summary: Company management functions, account permission levels and the first-time setup procedure for FortiCASB.
sources: [forticasb-admin-guide-24-4-b]
updated: 2026-10-26
status: current
---

# Company Management and First Time Setup

Company management covers system configuration, business unit and user management. Screenshots were not extracted.

## Key functionality (Company page)
- View License Purchased
- Data Protection Usage
- Company and Business Unit Configuration
- User Management (see [User management and permissions](user-management-and-permissions.md))
- Microsoft Entra ID AU (Administrative Unit) Management (see [Entra ID administrative units](entra-id-administrative-units.md))
- Generate and Manage API Credentials (see [NAT IP and API credentials](nat-ip-and-api-credentials.md))

On first login you are prompted to create a company, business unit(s), and users. [src: forticasb-admin-guide-24-4-b, p.24]

## Account permission levels
- **Administrator**: full permissions, including creating, accessing, and assigning companies and organizations.
- **Business users with full access** (FortiCloud): same full permissions.
- **Business users with limited access** (FortiCloud): can only view companies they are part of.

Administrators continue to First Time Setup; limited-access business users skip to switching business units (see [Business units](business-units.md)). Setup differs for branched organizations (multiple branch offices, compartmentalized structure) versus a single unified office. [src: forticasb-admin-guide-24-4-b, p.24]

## Prerequisites
- A valid FortiCASB license (from your primary Fortinet Service Provider).
- An administrator with a Primary FortiCloud account to add company, business units, and users.

EU data location: all data collected for EU companies must be located in the EU region; host the service on either the Global site or the EU site. [src: forticasb-admin-guide-24-4-b, p.24-25]

## First time setup steps
A default company and business unit are created using your admin account.
1. Go to https://www.forticasb.com/.
2. Click **Login** (redirect to Fortinet single sign-on).
3. Log in with your admin account, or create a new admin account.
4. If applicable, select an account on the FortiCASB account selection page.
5. In the popup, enter a company name and description.
6. Click **Add Company**.
7. (Important) A default Business Unit must be created: in the Company page, click **Set as Default** to make the first business unit the default.
8. Click **Go to this BU** to verify the default business unit was created.

A pop-up blocker will block the FortiCASB GUI; set an exception or open the GUI manually. Next: [Business units](business-units.md). [src: forticasb-admin-guide-24-4-b, p.25-26]

## Related
- [Business units](business-units.md)
- [User management and permissions](user-management-and-permissions.md)
- [Licensing](licensing.md)
- [Legacy onboarding chapter](../legacy-admin-guide/onboarding/)
