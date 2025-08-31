# WDAC

<span style="background-color:yellow; color:black; padding:3px 6px; border-radius:4px; font-weight:bold;">
  Current State: In Progress
</span>

---

Windows Defender Application Control (WDAC) is a security feature that controls which binaries can run on a Windows device.[^1]

Before getting started with WDAC, there are several important considerations. WDAC is not just a technical tool — in production environments, it should be introduced as part of a well-planned process. This includes defining how policies will be created and updated, ensuring proper scaling, and thoroughly testing before deployment to avoid incidents.

In the best case, WDAC operates without blocking legitimate executables. In the worst case, a misconfigured policy can prevent all binaries from running, potentially affecting every device in your environment.

This repository is designed to help you learn WDAC, build a custom WDAC architecture, and safely roll it out in your company.


- 📢 [Disclaimer](3_Literature/Disclaimer.md)
- 🧾 [See Architecture](1_Architecture/Architecture.md)




[^1]: Microsoft. *manage-application-control-infrastructure*. https://learn.microsoft.com/en-us/windows-server/manage/windows-admin-center/use/manage-application-control-infrastructure
