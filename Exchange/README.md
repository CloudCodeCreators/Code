# Exchange Scripts and Tools

<div align="center">

![PowerShell](https://img.shields.io/badge/PowerShell-5391FE?logo=powershell&logoColor=white)
![Microsoft Exchange](https://img.shields.io/badge/Microsoft%20Exchange-0078D4?logo=microsoft&logoColor=white)
![Security](https://img.shields.io/badge/Security-FF6B6B?logo=shield&logoColor=white)

*PowerShell scripts and tools for Microsoft Exchange Server and Exchange Online management, with a focus on security assessments and maintenance utilities.*

</div>

## Post_check_CVE-2025-53786_mitigation.ps1

### Overview
A comprehensive validation script developed following extensive experience patching multiple Exchange environments for CVE-2025-53786. This tool addresses the limited output provided by standard cleanup scripts by performing thorough validation of both legacy shared service principals and newly created dedicated Exchange hybrid applications.

### Business Value
- **Time Savings:** Quick verification prevents hours of troubleshooting
- **Risk Mitigation:** Validates proper CVE-2025-53786 remediation
- **Compliance:** Ensures security configurations meet Microsoft standards
- **Documentation:** Generates comprehensive reports for audit trails

### Technical Capabilities

**Validation Scope:**
- Dedicated Exchange hybrid application (`ExchangeServerApp-{Guid}`) certificate and permission verification
- Legacy shared service principal ("Office 365 Exchange Online") cleanup confirmation
- Certificate expiration monitoring and credential validation
- Comprehensive tenant-wide security assessment

**Expected Security State:**
After successful mitigation, the shared service principal should contain no certificates - this represents the proper secure configuration.

### Prerequisites
- PowerShell 5.1 or later
- Microsoft Graph PowerShell SDK
- Required permissions: `Application.Read.All`

### Implementation

**Installation:**
```powershell
Install-Module Microsoft.Graph -Scope CurrentUser
```

**Execution:**
```powershell
.\Post_check_CVE-2025-53786_mitigation.ps1
```

**Process:**
1. Select target tenant (supports UPN, tenant domain, or custom domain)
2. Review real-time console output
3. Analyze generated HTML report for detailed findings

### Output and Reporting

The script provides multiple output formats:
- **Console Output:** Real-time validation status with immediate feedback
- **HTML Report:** Comprehensive report saved to current directory
- **Alert System:** Certificate expiration warnings and missing credential notifications

### Important Considerations

> **Security Notice:** This tool performs validation only and does not make remediation changes. Always follow official Microsoft guidance and organizational change management procedures.

> **Testing Requirement:** Test in non-production environments before production deployment.

### Documentation (In Development)

Comprehensive documentation covering CVE-2025-53786 remediation insights:
- Vulnerability analysis and technical impact assessment
- Step-by-step mitigation procedures
- Real-world implementation experiences
- Exchange hybrid deployment best practices

---

*Professional tooling for Exchange administrators and security teams*
