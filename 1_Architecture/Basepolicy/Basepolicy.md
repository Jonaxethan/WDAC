# Basepolicy

Windows Defender Application [WDAC] use the Basepolicy. 
A Basepolicy contains basic setting 
| Rule option | Description | Valid supplemental option |
|-------------|-------------|---------------------------|
| **0 Enabled:UMCI** | App Control policies restrict both kernel-mode and user-mode binaries. By default, only kernel-mode binaries are restricted. Enabling this rule option validates user mode executables and scripts. | No |
| **1 Enabled:Boot Menu Protection** | This option isn't currently supported. | No |
| **2 Required:WHQL** | By default, kernel drivers that aren't Windows Hardware Quality Labs (WHQL) signed are allowed to run. Enabling this rule requires that every driver is WHQL signed and removes legacy driver support. Kernel drivers built for Windows 10 should be WHQL certified. | No |
| **3 Enabled:Audit Mode (Default)** | Instructs App Control to log information about applications, binaries, and scripts that would have been blocked, if the policy was enforced. You can use this option to identify the potential impact of your App Control policy, and use the audit events to refine the policy before enforcement. To enforce an App Control policy, delete this option. | No |
| **4 Disabled:Flight Signing** | If enabled, binaries from Windows Insider builds aren't trusted. This option is useful for organizations that only want to run released binaries, not prerelease Windows builds. | No |
| **5 Enabled:Inherit Default Policy** | This option is reserved for future use and currently has no effect. | Yes |
| **6 Enabled:Unsigned System Integrity Policy (Default)** | Allows the policy to remain unsigned. When this option is removed, the policy must be signed and any supplemental policies must also be signed. The certificates that are trusted for future policy updates must be identified in the UpdatePolicySigners section. Certificates that are trusted for supplemental policies must be identified in the SupplementalPolicySigners section. | Yes |
| **7 Allowed:Debug Policy Augmented** | This option isn't currently supported. | Yes |
| **8 Required:EV Signers** | This option isn't currently supported. | No |
| **9 Enabled:Advanced Boot Options Menu** | The F8 preboot menu is disabled by default for all App Control policies. Setting this rule option allows the F8 menu to appear to physically present users. | No |
| **10 Enabled:Boot Audit on Failure** | Used when the App Control policy is in enforcement mode. When a boot-critical driver fails during startup, the App Control policy is placed in audit mode so that Windows loads. Administrators can validate the reason for the failure in the CodeIntegrity event log. | No |
| **11 Disabled:Script Enforcement** | This option disables script enforcement options, covering PowerShell, Windows Based Script Host (wscript.exe), Windows Console Based Script Host (cscript.exe), HTA files run in Microsoft HTML Application Host (mshta.exe), and MSXML. Some script hosts may behave differently even when your policy is in audit mode. **NOTE:** This option isn't supported on Windows Server 2016 or Windows 10 1607 LTSB and shouldn't be used on those operating systems. | No |
| **12 Required:Enforce Store Applications** | If this rule option is enabled, App Control policies also apply to Universal Windows applications. | No |
| **13 Enabled:Managed Installer** | Use this option to automatically allow applications installed by a managed installer. | Yes |
| **14 Enabled:Intelligent Security Graph Authorization** | Use this option to automatically allow applications with "known good" reputation as defined by Microsoft's Intelligent Security Graph (ISG). | Yes |
| **15 Enabled:Invalidate EAs on Reboot** | When the Intelligent Security Graph option (14) is used, App Control sets an extended file attribute that indicates that the file was authorized to run. This option causes App Control to periodically revalidate the reputation for files previously authorized by the ISG. | No |
| **16 Enabled:Update Policy No Reboot** | Use this option to allow future App Control policy updates to apply without requiring a system reboot. **NOTE:** This option is only supported on Windows 10, version 1709 and later, or Windows Server 2019 and later. | No |
| **17 Enabled:Allow Supplemental Policies** | Use this option on a base policy to allow supplemental policies to expand it. **NOTE:** This option is only supported on Windows 10, version 1903 and later, or Windows Server 2022 and later. | No |
| **18 Disabled:Runtime FilePath Rule Protection** | This option disables the default runtime check that only allows FilePath rules for paths that are only writable by an administrator. **NOTE:** This option is only supported on Windows 10, version 1903 and later, or Windows Server 2022 and later. | Yes |
| **19 Enabled:Dynamic Code Security** | Enables policy enforcement for .NET applications and dynamically loaded libraries. **NOTE:** This option is only supported on Windows 10, version 1803 and later, or Windows Server 2019 and later. **NOTE:** This option is always enforced if any App Control UMCI policy enables it. There's no audit mode for .NET dynamic code security hardening. | No |
| **20 Enabled:Revoked Expired As Unsigned** | Use this option to treat binaries signed with revoked certificates, or expired certificates with the Lifetime Signing EKU on the signature, as "Unsigned binaries" for user-mode process/components, under enterprise signing scenarios. | No |
| **Enabled:Developer Mode Dynamic Code Trust** | Use this option to trust UWP apps that are debugged in Visual Studio or deployed through device portal when Developer Mode is enabled on the system. | No |

