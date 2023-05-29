---
title: What's new 
description: This article is updated frequently to let you know what's new in the latest release of Microsoft Defender for Identity.
ms.date: 05/23/2023
ms.topic: overview
---

# What's new in Microsoft Defender for Identity

This article is updated frequently to let you know what's new in the latest releases of Microsoft Defender for Identity.

## Defender for Identity deployment schedule

Defender for Identity releases are deployed gradually across customer tenants. If there's a feature documented here that you don't see yet in your tenant, check back later for the update.

## RSS feed

Get notified when this page is updated by copying and pasting the following URL into your feed reader: `https://learn.microsoft.com/api/search/rss?search=%22This+article+is+updated+frequently+to+let+you+know+what%27s+new+in+the+latest+release+of+Microsoft+Defender+for+Identity%22&locale=en-us`

## Other what's new resources

For more information on what's new with other Microsoft Defender security products, see:

- [What's new in Microsoft 365 Defender](/microsoft-365/security/defender/whats-new)
- [What's new in Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/whats-new-in-microsoft-defender-endpoint)
- [What's new in Microsoft Defender for Cloud Apps](/cloud-app-security/release-notes)

For updates about versions and features released 6 months ago or earlier, see the [What's new archive for Microsoft Defender for Identity](whats-new-archive.md).

## May 2023

### Defender for Identity release 2.203

Released May 15, 2023

- New health alert for verifying that ADFS Container Auditing is configured correctly. For more information, see [Microsoft Defender for Identity sensor health alerts](health-alerts.md#auditing-on-the-adfs-container-is-not-enabled-as-required).

- The Microsoft Defender 365 **Identity** page includes UI updates for the lateral movement path experience. No functionality was changed. For more information, see [Understand and investigate Lateral Movement Paths (LMPs) with Microsoft Defender for Identity](understand-lateral-movement-paths.md).

- This version includes improvements and bug fixes for internal sensor infrastructure.

### Identity timeline enhancements

The identity **Timeline** tab now contains new and enhanced features! With the updated timeline, you can now filter by *Activity type*, *Protocol*, and *Location*, in addition to the original filters. You can also export the timeline to a CSV file and find additional information about activities associated with MITRE ATT&CK techniques. For more information, see [Investigate users in Microsoft 365 Defender](/microsoft-365/security/defender/investigate-users).

### Alert tuning in Microsoft 365 Defender

Alert tuning, now available in Microsoft 365 Defender, allows you to adjust your alerts and optimize them. Alert tuning reduces false positives, allows your SOC teams to focus on high-priority alerts, and improves threat detection coverage across your system. 

In Microsoft 365 Defender, create rule conditions based on evidence types, and then apply your rule on any rule type that matches your conditions. For more information, see [Tune an alert](/microsoft-365/security/defender/investigate-alerts#public-preview-tune-an-alert).

## April 2023

### Defender for Identity release 2.202

Released April 23, 2023

-	New health alert for verifying that Directory Services Configuration Container Auditing is configured correctly, as described in the [health alerts page](health-alerts.md#auditing-on-the-configuration-container-is-not-enabled-as-required).
-	New workspaces for AD tenants mapped New Zealand will be created in the Australia East region. For the most current list of regional deployment, see [Defender for Identity components](architecture.md#defender-for-identity-components).
- Version includes improvements and bug fixes for internal sensor infrastructure.

## March 2023

### Defender for Identity release 2.201

Released March 27, 2023

- We're in the process of disabling the SAM-R honeytoken alert. While these types of accounts should never be accessed or queried, we're aware that certain legacy systems may use these accounts as part of their regular operations. If this functionality is necessary for you, you can always create an advanced hunting query and use it as a custom detection. Additionally, we'll be reviewing the LDAP honeytoken alert over the coming weeks, but it will remain functional for now.

- We fixed detection logic issues in the [Directory Services Object Auditing health alert](health-alerts.md#directory-services-object-auditing-is-not-enabled-as-required) for non-English operating systems, and for Windows 2012 with Directory Services schemas earlier than version 87.

- We removed the prerequisite of configuring a Directory Services account for the sensors to start. For more information, see [Microsoft Defender for Identity Directory Service account recommendations](directory-service-accounts.md#number-of-dsa-entries).

- We no longer require logging 1644 events. If you have this registry setting enabled, you can remove it. For more information, see [Event ID 1644](configure-windows-event-collection.md#event-id-1644).

- Version includes improvements and bug fixes for internal sensor infrastructure.

### Defender for Identity release 2.200

Released March 16, 2023

- Version includes improvements and bug fixes for internal sensor infrastructure.

### Defender for Identity release 2.199

Released March 5, 2023

- Some exclusions for the **Honeytoken was queried via SAM-R** alert weren't functioning properly. In these instances, alerts were being triggered even for excluded entities. This has now been fixed.

- **Updated NTLM protocol name for the Identity Advanced Hunting tables**: The old protocol name `Ntlm` will now be the new protocol name `NTLM`, in Advanced Hunting Identity tables: IdentityLogonEvents, IdentityQueryEvents, IdentityDirectoryEvents.
If you're currently using the `Ntlm` protocol in case-sensitive format from the Identity event tables, you should change it to `NTLM`.

- Version includes improvements and bug fixes for internal sensor infrastructure.

## February 2023

### Defender for Identity release 2.198

Released February 15, 2023

- **Identity timeline is now available as part of the new Identity page in Microsoft 365 Defender**: The updated User page in Microsoft 365 Defender now has a new look and feel, with an expanded view of related assets and a new dedicated timeline tab. The timeline represents activities and alerts from the last 30 days, and it unifies the user’s identity entries across all available workloads (Defender for Identity/Defender for Cloud Apps/Defender for Endpoint). By using the timeline, you can easily focus on activities that the user performed (or were performed on them), in specific timeframes. For more information, see [Investigate users in Microsoft 365 Defender](/microsoft-365/security/defender/investigate-users)

- **Further improvements for honeytoken alerts**: In [release 2.191](whats-new-archive.md#defender-for-identity-release-2191) we introduced several new scenarios to the honeytoken activity alert.  

  Based on customer feedback, we've decided to split the honeytoken activity alert into five separate alerts:

  - Honeytoken user was queried via SAM-R.
  - Honeytoken user was queried via LDAP.
  - Honeytoken user authentication activity
  - Honeytoken user had attributes modified.
  - Honeytoken group membership changed.

  Additionally, we have added exclusions for these alerts, providing a customized experience for your environment.

  We're looking forward to hearing your feedback so we can continue to improve.

- New security alert - **Suspicious certificate usage over Kerberos protocol (PKINIT).**: Many of the techniques for abusing Active Directory Certificate Services (AD CS) involve the use of a certificate in some phase of the attack. Moving forward, Microsoft Defender for Identity will alert users when it observes such suspicious certificate usage. This behavioral monitoring approach will provide comprehensive protection against AD CS attacks, triggering an alert when a suspicious certificate authentication is attempted against a domain controller with a Defender for Identity sensor installed. For more information, see [Microsoft Defender for Identity now detects suspicious certificate usage](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/microsoft-defender-for-identity-now-detects-suspicious/ba-p/3743335).
- **Automatic attack disruption**: Defender for Identity now works together with Microsoft 365 Defender to offer Automated Attack Disruption. This means that, for signals coming from Microsoft 365 Defender, we can trigger the **Disable User** action. These actions are triggered by high-fidelity XDR signals, combined with insights from the continuous investigation of thousands of incidents by Microsoft’s research teams. The action suspends the compromised user account in Active Directory and syncs this information to Azure AD. For more information about automatic attack disruption, read [the blog post by Microsoft 365 Defender](https://techcommunity.microsoft.com/t5/microsoft-365-defender-blog/what-s-new-in-xdr-at-microsoft-ignite/ba-p/3648872).

  You can also exclude specific users from the automated response actions. For more information, see [Configure Defender for Identity automated response exclusions](automated-response-exclusions.md).
- **Remove learning period**: The alerts generated by Defender for Identity are based on various factors such as profiling, deterministic detection, machine learning, and behavioral algorithms that it has learned about your network. The full learning process for Defender for Identity can take up to 30 days per domain controller. However, there may be instances where you would like to receive alerts even before the full learning process has been completed. For example, when you install a new sensor on a domain controller or when you're evaluating the product, you may want to get alerts immediately. In such cases, you can turn off the learning period for the affected alerts by enabling the **Remove learning period** feature. For more information, see [Removing the learning period for alerts](advanced-settings.md#removing-the-learning-period-for-alerts).

- **New way of sending alerts to M365D**: A year ago, we announced that all of [Microsoft Defender for Identity experiences are available in the Microsoft 365 Defender portal](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/all-microsoft-defender-for-identity-features-now-available-in/ba-p/3130037).  In the upcoming month, we'll gradually switch our primary alert pipeline from "Defender for Identity > Defender for Cloud Apps > Microsoft 365 Defender" to "Defender for Identity > Microsoft 365 Defender". This means that status updates in Defender for Cloud Apps **will not be** reflected in Microsoft 365 Defender and vice versa. This change should significantly reduce the time it takes for alerts to appear in the Microsoft 365 Defender portal. As part of this migration, all Defender for Identity policies will no longer be available in the Defender for Cloud Apps portal as of March 5. As always, we recommend using the Microsoft 365 Defender portal for all Defender for Identity experiences.

- Version includes improvements and bug fixes for internal sensor infrastructure.

## January 2023

### Defender for Identity release 2.197

Released January 22, 2023

- Version includes improvements and bug fixes for internal sensor infrastructure.

### Defender for Identity release 2.196

Released January 10, 2023

- New health alert for verifying that Directory Services Object Auditing is configured correctly, as described in the [health alerts page](health-alerts.md#directory-services-object-auditing-is-not-enabled-as-required).

- New health alert for verifying that the sensor’s power settings are configured for optimal performance, as described in the [health alerts page](health-alerts.md#power-mode-is-not-configured-for-optimal-processor-performance).

- We've added [MITRE ATT&CK](https://attack.mitre.org/) information to the IdentityLogonEvents, IdentityDirectoryEvents and IdentityQueryEvents tables in Microsoft 365 Defender Advanced Hunting.  In the **AdditionalFields** column, you can find details about the Attack Techniques and the Tactic (Category) associated with some of our logical activities.

- Since all major Microsoft Defender for Identity features have now been made available in the Microsoft 365 Defender portal, the portal redirection setting will be automatically enabled for each tenant starting January 31, 2023. For more information, see [Redirecting accounts from Microsoft Defender for Identity to Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-security-mdi-redirection#what-to-expect).

## December 2022

### Defender for Identity release 2.195

Released December 7, 2022

- Defender for Identity data centers are now also deployed in the Australia East region. For the most current list of regional deployment, see [Defender for Identity components](architecture.md#defender-for-identity-components).

- Version includes improvements and bug fixes for internal sensor infrastructure.



## Next steps

- [What is Microsoft Defender for Identity?](what-is.md)
- [Frequently asked questions](technical-faq.yml)
- [Defender for Identity prerequisites](prerequisites.md)
- [Defender for Identity capacity planning](capacity-planning.md)
- [Check out the Defender for Identity forum!](<https://aka.ms/MDIcommunity>)
