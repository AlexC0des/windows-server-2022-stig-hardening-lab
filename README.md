# Windows Server 2022 STIG Hardening Lab

A hands-on DoD-style cybersecurity hardening lab built on Windows Server 2022,
following DISA STIG Version 2 Release 8 compliance standards and the NIST
Risk Management Framework (RMF).

## Environment

- Host: Windows 10 PC
- Hypervisor: Oracle VirtualBox
- Guest OS: Windows Server 2022 Standard Evaluation (Desktop Experience)
- STIG: DISA Windows Server 2022 STIG Version 2, Release 8 (01 Apr 2026)
- Tools: DISA STIG Viewer 3.0, DISA SCAP Compliance Checker (SCC)

## CAT I Controls Assessed (10 total)

| V-ID | STIG ID | Title | Status |
|---|---|---|---|
| V-254250 | WN22-00-000130 | Local volumes use NTFS format | Not a Finding |
| V-254293 | WN22-AC-000090 | Reversible password encryption disabled | Not a Finding |
| V-254374 | WN22-CC-000430 | Windows Installer elevated privilege disabled | Not a Finding |
| V-254393 | WN22-DC-000090 | AD GPO object permissions | Not Applicable |
| V-254413 | WN22-DC-000290 | Domain Controller PKI certificates | Not Applicable |
| V-254467 | WN22-SO-000230 | Anonymous share enumeration blocked | Not a Finding |
| V-254469 | WN22-SO-000250 | Anonymous Named Pipes access restricted | Not a Finding |
| V-254474 | WN22-SO-000300 | LAN Manager hash storage prevented | Not a Finding |
| V-254496 | WN22-UR-000060 | Create token object right empty | Not a Finding |
| V-254500 | WN22-UR-000100 | Debug programs — Administrators only | Not a Finding |

## How Controls Were Applied

**Security Options (secpol.msc):**
Anonymous enumeration, Named Pipes access, LAN Manager hash storage — all
configured via Local Policies → Security Options with registry verification
confirming each change was written correctly.

**Group Policy Editor (gpedit.msc):**
Windows Installer elevated privilege and reversible password encryption
configured via Computer Configuration. User Rights Assignment verified
for Debug programs and Create token object rights.

**Registry Verification:**
Each fix verified directly in regedit confirming the correct REG_DWORD
values were written — the same verification method used in the STIG
check text.

**Not Applicable Controls:**
Two Domain Controller specific controls (WN22-DC-) marked Not Applicable —
system is a standalone server, not promoted to Active Directory Domain
Controller.

## SCAP Compliance Scan

Automated compliance scan performed using DISA SCAP Compliance Checker (SCC)
with Windows Server 2022 SCAP content loaded from the DISA STIG package.
HTML compliance report generated showing pass/fail status across all
automated rules. Report available in /screenshots folder.

## RMF Documentation

System Security Plan (SSP) covers this system alongside RHEL 10 across
all 6 steps of the NIST RMF — categorized per FIPS 199, controls mapped
to NIST SP 800-53, and continuous monitoring strategy documented.
See SSP-CyberLab-Combined.docx in this repository.

## Evidence

/screenshots folder contains:
- Windows Server 2022 VM configuration verification screenshots
- Registry verification screenshots for each applicable control
- STIG Viewer 3.0 checklist export showing all 10 controls documented
- SCC HTML compliance scan report

## Related Project
[RHEL 10 STIG Hardening Lab](https://github.com/AlexC0des/rhel10-stig-hardening-lab)

## Skills Demonstrated

Windows Server 2022 · Group Policy Editor · Local Security Policy ·
PowerShell · Registry Editor · DISA STIG Viewer 3.0 · DISA SCC ·
SCAP scanning · RMF · NIST SP 800-53 · NTLMv2 · NTFS · VirtualBox ·
DoD Cybersecurity
