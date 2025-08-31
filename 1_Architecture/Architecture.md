# Windows Defender Application Control (WDAC) Architectures

Windows Defender Application Control (WDAC) is Microsoft’s modern solution for application whitelisting and execution control.  
It replaces older models like AppLocker and aligns with a **default deny** security approach[^1].  
This document explains the main WDAC architectures available today.

---

## 1. Single Base Policy

### Overview
The **Single Base Policy** was the original WDAC format, used in early Windows 10 versions.  
Only **one policy** could be active per device.  

While simple, this approach is **rigid** — any change requires replacing the entire policy.  
Microsoft has moved away from this model in favor of multiple policies[^1].

### Pros
- Simple design for very small environments.  
- One central whitelist for all devices.  

### Cons
- No ability to test safely (no side-by-side audit and enforce).  
- Replacing the policy risks service disruption.  
- Not aligned with Microsoft’s modern WDAC roadmap[^1].  

### When to Use
- Legacy environments (Windows 10 before version 1903).  
- Very small businesses with minimal software diversity.  

---

## 2. Multiple Base Policies

### Overview
From **Windows 10 version 1903 onward**, WDAC supports the **Multiple Policy Format**,  
allowing more than one base policy to run in parallel[^1].  

This is now Microsoft’s **recommended approach**. It enables scenarios like running an **audit-mode policy**  
alongside an **enforcement-mode policy**, making testing and refinement much safer[^1][^2].  

### Pros
- Safer rollouts with audit/enforce side-by-side.  
- Supports personas or departments (e.g., IT vs. HR).  
- Scales better for SMBs and enterprises.  

### Cons
- Slightly more complex to track and document.  
- Requires Windows 10 (1903+), Windows 11, or Windows Server 2022.  

### When to Use
- All modern deployments (SMB or enterprise).  
- Testing new policies in audit mode without risking production.  
- Organizations aligned with Microsoft’s security roadmap.  

---

## 3. Base Policy + Supplemental Policies

### Overview
A **Base Policy** defines the security baseline: which applications, binaries, and OS components are always trusted.  
**Supplemental Policies** extend the base without modifying it, creating a modular system[^1][^3].  

This design is particularly useful for SMBs, because it separates “global trust” (base) from “local exceptions” (supplemental).  

### Example
- **Base Policy**: Microsoft-signed binaries, Windows components, core productivity apps.  
- **Supplemental Policy**: ERP app for Finance, Docker for Developers, or a unique line-of-business tool.  

### Pros
- Modular and scalable.  
- Easier rollback — remove a supplemental policy without touching the base.  
- Helps isolate problems to specific apps or departments.  

### Cons
- Requires careful version control and tracking of multiple policies.  
- Available only on Windows 10 (1903+) or newer.  

### When to Use
- Organizations with diverse departmental software needs.  
- SMBs that want to minimize risk by keeping the base stable.  
- Scenarios where rollback safety is critical[^1].  



## Conclusion

- **Single Base Policy** → legacy only, not recommended today.  
- **Multiple Base Policies** → the modern standard; flexible and safe.  
- **Base + Supplemental Policies** → best practice for modular management.  


---

## Citations
[^1]: CIAOPS. *Comprehensive Application Control for Windows with Microsoft 365 Business Premium* (2025).  
[^2]: [Microsoft Docs – Multiple Policy Format](https://learn.microsoft.com/windows/security/threat-protection/windows-defender-application-control/multiple-policy-format)  
[^3]: [Microsoft Docs – Supplemental Policies](https://learn.microsoft.com/windows/security/threat-protection/windows-defender-application-control/deploy-supplemental-policies)  
[^4]: [Microsoft Docs – Attack Surface Reduction Rules](https://learn.microsoft.com/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)  
