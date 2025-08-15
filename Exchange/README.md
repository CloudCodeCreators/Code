# 📧 Exchange Scripts and Tools

<div align="center">

![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white)
![Microsoft Exchange](https://img.shields.io/badge/Microsoft%20Exchange-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)
![Security](https://img.shields.io/badge/Security-FF6B6B?style=for-the-badge&logo=shield&logoColor=white)

*PowerShell scripts and tools for Microsoft Exchange Server and Exchange Online management, with a focus on security assessments and maintenance utilities.*

</div>

---

## � Scripts Overview

<div align="center">

### 🛡️ **Post_check_CVE-2025-53786_mitigation.ps1**

<img src="https://img.shields.io/badge/CVE--2025--53786-Critical-red?style=for-the-badge" alt="CVE-2025-53786">
<img src="https://img.shields.io/badge/Exchange_Hybrid-Supported-green?style=for-the-badge" alt="Exchange Hybrid">

</div>

---

## 📖 Purpose

> **🎯 Real-World Experience:** *This week was a lot of fun in patching several Exchange environments in regards to CVE-2025-53786.*

The **Hybrid Configuration Wizard (HCW)** was executed with the new option to configure a dedicated Exchange hybrid application in Microsoft Entra ID. As a final step, the cleanup script was fired but we noticed that there was **not a lot of output regarding certificates and additional info**. 

So we quickly created a script that checks:
- 🔍 The older **shared service principal** 
- 🆕 The newly created **dedicated Exchange hybrid application** in Microsoft Entra ID

### 💡 Why This Matters

If you manage Exchange hybrid deployments, it's worth validating service principals and certificates after automated changes - **a quick verification script can save hours of troubleshooting**. Happy to share the script or walk through the checks! 🚀

---

## ⚙️ What It Does

<table>
<tr>
<td width="50%" valign="top">

### 🔐 **Validation Checks**
- ✅ Connects to Microsoft Graph for your chosen tenant
- ✅ Supports UPN, tenant domain, or custom domain input
- ✅ Validates newly created dedicated Exchange hybrid app (`ExchangeServerApp-{Guid}`)
- ✅ Confirms proper certificates and permissions are present

</td>
<td width="50%" valign="top">

### 🧹 **Security Verification**  
- ✅ Confirms legacy shared service principal cleanup
- ✅ Verifies **no remaining certificates** after cleanup
- ✅ Lists and validates all certificates and client secrets
- ✅ Highlights expired or missing credentials
- ✅ Generates detailed HTML report

</td>
</tr>
</table>

> **🔒 Expected Secure State:** After successful cleanup, the shared service principal should have **no remaining certificates** - this is the expected secure configuration.

---

## 🎯 Why Use This Script?

<div align="center">

| 🚀 **Rapid Assessment** | 📊 **Clear Visibility** | 🛡️ **Security Focus** |
|:---:|:---:|:---:|
| Quick tenant impact check | Certificate status overview | CVE-2025-53786 validation |
| *Minutes, not hours* | *HTML + Console output* | *Validation only, no changes* |

</div>

> **⚠️ Important:** This is a **validation tool only** - it does not remediate, but gives clear visibility into certificate status for Exchange Online identities.

---

## 📋 Prerequisites

```powershell
# Required Components
✅ PowerShell 5.1 or later
✅ Microsoft Graph PowerShell SDK  
✅ Required permissions: Application.Read.All
```

---

## 🚀 Usage

### Step 1: Install Dependencies
```powershell
# Install the Microsoft Graph PowerShell module
Install-Module Microsoft.Graph -Scope CurrentUser
```

### Step 2: Run the Script
```powershell
# Execute the validation script
.\Post_check_CVE-2025-53786_mitigation.ps1
```

### Step 3: Review Results
1. 📺 **Follow the prompts** to select your tenant
2. 👀 **Review on-screen results** in real-time  
3. 📄 **Check the generated HTML report** for detailed analysis

---

## 📊 Output

The script provides comprehensive reporting:

<table>
<tr>
<td align="center" width="25%">

### 🖥️ **Console**
Real-time validation results with color-coded status

</td>
<td align="center" width="25%">

### 📄 **HTML Report**  
Detailed report saved to current directory

</td>
<td align="center" width="25%">

### ⚠️ **Warnings**
Certificate expiration alerts

</td>
<td align="center" width="25%">

### 🚨 **Alerts**
Missing credential notifications

</td>
</tr>
</table>

---

## 📝 Blog Post (Coming Soon)

<div align="center">

🚧 **In Development** 🚧

*For detailed insights into CVE-2025-53786 and the remediation process, check out our upcoming blog post:*

</div>

### 📚 What We'll Cover:
- 🔍 **Understanding the vulnerability** - Technical deep-dive
- 📊 **Impact assessment** - Risk evaluation methodology  
- 🛠️ **Step-by-step mitigation** - Complete remediation guide
- 💡 **Lessons learned** - Real-world patching experiences across multiple Exchange environments
- 🏆 **Best practices** - Proven strategies for hybrid deployments

---

<div align="center">

## ⚠️ **Important Security Notice**

> **🛡️ This script is for validation only.**  
> Always review official Microsoft guidance for mitigation steps and follow your organization's change management procedures.

---

### 🧪 **Testing Reminder**

**Always test scripts in a non-production environment before deploying to production systems.**

---

*Made with ❤️ for the Exchange Admin Community*

</div>
