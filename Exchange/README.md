# Exchange Scripts and Tools

This folder contains PowerShell scripts and tools for Microsoft Exchange Server and Exchange Online management, with a focus on security assessments and maintenance utilities.

## 📋 Scripts Overview

### Post_check_CVE-2025-53786_mitigation.ps1

## Purpose
This week was a lot of fun in patching several Exchange environments in regards to CVE-2025-53786. The HCW (Hybrid Configuration Wizard) was executed with the new option to configure a dedicated Exchange hybrid application in Microsoft Entra ID. As a final step, the cleanup script was fired but we noticed that there was not a lot of output regarding certificates and additional info. So we quickly created a script that checks the older shared service principal and also the newly created dedicated Exchange hybrid application in Microsoft Entra ID.

If you manage Exchange hybrid deployments, it's worth validating service principals and certificates after automated changes - a quick verification script can save hours of troubleshooting. Happy to share the script or walk through the checks!

## What It Does
- Connects to Microsoft Graph for your chosen tenant (supports UPN, tenant domain, or custom domain input)
- Checks both App Registration and Service Principal for Exchange Online ("Office 365 Exchange Online")
- Lists and validates all certificates and client secrets, highlighting expired or missing credentials
- Generates a detailed HTML report for your records

## Why Use This Script?
This is a rapid assessment tool to help admins quickly check if their tenant is potentially impacted by CVE-2025-53786. It does not remediate, but gives clear visibility into certificate status for Exchange Online identities.

## Prerequisites
- PowerShell 5.1 or later
- Microsoft Graph PowerShell SDK
- Required permissions: `Application.Read.All`

## Usage
1. Install the required Microsoft Graph PowerShell module:
   ```powershell
   Install-Module Microsoft.Graph -Scope CurrentUser
   ```

2. Run the script in PowerShell with the required Microsoft Graph permissions:
   ```powershell
   .\Post_check_CVE-2025-53786_mitigation.ps1
   ```

3. Follow the prompts to select your tenant
4. Review the on-screen results and the generated HTML report

## Output
The script generates:
- Console output with real-time validation results
- HTML report saved to the current directory
- Certificate expiration warnings
- Missing credential alerts

> **⚠️ Important Note:** This script is for validation only. Always review official Microsoft guidance for mitigation steps and follow your organization's change management procedures.

## Blog Post
For detailed insights into CVE-2025-53786 and the remediation process, check out our blog post that covers:
- Understanding the vulnerability
- Impact assessment
- Step-by-step mitigation process
- Lessons learned from patching multiple Exchange environments
- Best practices for hybrid deployments

---

*Always test scripts in a non-production environment before deploying to production systems.*
