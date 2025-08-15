# Post_check_CVE-2025-53786_mitigation.ps1

[⬇️ Download the script directly](https://github.com/CloudCodeCreators/Code/raw/main/Exchange/Post_check_CVE-2025-53786_mitigation.ps1)
## Purpose
This PowerShell script provides a quick and clear way to validate your Microsoft 365 tenant for exposure to CVE-2025-53786, a vulnerability affecting Exchange Online and related certificate-based authentication.

## What It Does
- Connects to Microsoft Graph for your chosen tenant (supports UPN, tenant domain, or custom domain input)
- Checks both App Registration and Service Principal for Exchange Online ("Office 365 Exchange Online")
- Lists and validates all certificates and client secrets, highlighting expired or missing credentials
- Generates a detailed HTML report for your records

## Why Use This Script?
This is a rapid assessment tool to help admins quickly check if their tenant is potentially impacted by CVE-2025-53786. It does not remediate, but gives clear visibility into certificate status for Exchange Online identities.

## Usage
1. Run the script in PowerShell with the required Microsoft Graph permissions (Application.Read.All).
2. Follow the prompts to select your tenant.
3. Review the on-screen results and the generated HTML report.

> **Note:** This script is for validation only. Always review official Microsoft guidance for mitigation steps.


[📥 Download Script](https://github.com/CloudCodeCreators/Code/blob/main/Exchange/Post_check_CVE-2025-53786_mitigation.ps1)

