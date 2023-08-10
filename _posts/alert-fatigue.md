---
# the default layout is 'page'
icon: fas fa-info-circle
order: 4
---

IDC reports that 30% of alerts are ignored by employees working in 1500-5000 member size firm. Alert fatigue is real and a growing problem. [Reference](https://www.criticalstart.com/resources/in-cybersecurity-every-alert-matters/)

DevOps and SRE team get bombarded with alerts of all kind and it is difficult to go through each one of them. 
Below are some scenarios that may generate non-useful alerts:
1. **Low threshold, high sensitivity**: Suppose a server did not respond to few calls and you get an alert for it. But when you go and investigate everything looks fine. This is classic case where application has transient hiccups. Should we bother SRE everytime these transient issues occur?
2. **False positives**: Suppose you get alerts for suspicious login. These can happen because of IP address change, switch in IP address during the login process. Credential access alert when we know that penetration testing is going on.
3. **One incident, multiple alerts**: One single incident sometimes generate alerts from multiple sources. Suppose a kubernetes service is down, you might get alerts form both kubernetes monitoring and application gateway. Alerts may keep on coming until the issue is resolved or the alert rule is temporarily disbaled.
4. **Wrong alert type to SRE**: Developers and SRE should decide on the type of alerts they should get. Suppose a database is going to be full. Is it responsibility of SRE to take care of it or the developers. SRE should only get alerts which is actionable to them. A good criteria for this is if SRE needs to inform other teams about the alert then the alert should have been directly gone to the specific team. 
<br>
<br>
<br>


How can we fix these issues:
1. **Low threshold, high sensitivity**: We should revise our threshold once we have more information about the behaviour of the application. If the application drops few connections but works in a stable manner most of the time then we should increase the threshold.
2. **False positives**: False positives is tricky to be dealt with. We cannot ignore(if we cannot confirm its false) them neither we can reduce their priority. Reducing false positives will require to create more intelligent detection mechanism.
3. **One incident, multiple alerts**: Platform should be intelligent enough to group alerts generated from a single event. Tags can be used for grouping. Also, when setting up alerts we should be mindful of scenarios where we get multiple alerts for a single event.
4. **Wrong alert type to SRE**: If the alert coming to SRE is not actionable and they need to contact developers, then it is better to send the alert directly to developers. There should be a clear distinction between what is the responsibility of Developer vs SRE.
<br>
<br>
In this blog I have mentioned some ways to handle alert fatigue. I will later talk about how to handle alerts.
