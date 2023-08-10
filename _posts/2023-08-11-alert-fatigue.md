---
title: Alert Fatigue
date: 2023-08-11 02:20:00 +/-TTTT
categories: [SRE, ALERTS]
tags: [sre]
---

IDC reports that 30% of alerts are ignored by employees working in 1500-5000 member size firms. Alert fatigue is real and a growing problem. [Reference](https://www.criticalstart.com/resources/in-cybersecurity-every-alert-matters/)

DevOps and SRE team get bombarded with alerts of all kinds and it is difficult to go through each one of them. 
Below are some scenarios that may generate non-useful alerts:
1. **Low threshold, high sensitivity**: Suppose a server did not respond to a few calls and you get an alert for it. But when you go and investigate everything looks fine. This is a classic case where an application has transient hiccups. Should we bother SRE everytime these transient issues occur?
2. **False positives**: Suppose you get alerts for suspicious login. These can happen because of IP address change, switch in IP address during the login process. Credential access alert when we know that penetration testing is going on.
3. **One incident, multiple alerts**: One single incident sometimes generates alerts from multiple sources. Suppose a kubernetes service is down, you might get alerts from both kubernetes monitoring and application gateway. Alerts may keep on coming until the issue is resolved or the alert rule is temporarily disabled.
4. **Wrong alert type to SRE**: Developers and SRE should decide on the type of alerts they should get. Suppose a database is going to be full. Is it the responsibility of SRE to take care of it or the developers. SRE should only get alerts which are actionable to them. A good criteria for this is if SRE needs to inform other teams about the alert then the alert should have been directly gone to the specific team. 
<br>
<br>
<br>


How can we fix these issues:
1. **Low threshold, high sensitivity**: We should revise our threshold once we have more information about the behavior of the application. If the application drops few connections but works in a stable manner most of the time then we should increase the threshold.
2. **False positives**: False positives are tricky to be dealt with. We cannot ignore(if we cannot confirm its false) them neither can we reduce their priority. Reducing false positives will require creating more intelligent detection mechanisms.
3. **One incident, multiple alerts**: Platform should be intelligent enough to group alerts generated from a single event. Tags can be used for grouping. Also, when setting up alerts we should be mindful of scenarios where we get multiple alerts for a single event.
4. **Wrong alert type to SRE**: If the alert coming to SRE is not actionable and they need to contact developers, then it is better to send the alert directly to developers. There should be a clear distinction between what is the responsibility of Developer vs SRE.
<br>
<br>


In this blog I have mentioned some ways to handle alert fatigue. I will later talk about how to handle alerts.
