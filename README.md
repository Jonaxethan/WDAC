# WDAC
Windows Defender Application Control (WDAC) is a security feature that controls which binaries can run on a Windows device.[^1]

Before getting started with WDAC, there are several important considerations. WDAC is not just a technical tool — in production environments, it should be introduced as part of a well-planned process. This includes defining how policies will be created and updated, ensuring proper scaling, and thoroughly testing before deployment to avoid incidents.

In the best case, WDAC operates without blocking legitimate executables. In the worst case, a misconfigured policy can prevent all binaries from running, potentially affecting every device in your environment.


Productivity Suite (Office, Teams, PDF readers)

Development Tools (Visual Studio, Git, Docker)

Line-of-Business Apps (ERP, CRM)

Security/IT Tools (AV, RMM, PowerShell if allowed)




[^1]: Microsoft. *manage-application-control-infrastructure*. https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/use/manage-application-control-infrastructure