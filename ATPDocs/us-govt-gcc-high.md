---
title: US Government offerings
description: This article provides an overview of Microsoft Defender for Identity's US Government offerings.
ms.date: 02/14/2023
ms.topic: overview
---

# Microsoft Defender for Identity for US Government offerings

The Microsoft Defender for Identity GCC High offering uses the same underlying technologies and capabilities as the commercial instance of Defender for Identity.

## Get started with US Government offerings

The Defender for Identity GCC, GCC High, and Department of Defense (DoD) offerings are built on the Microsoft Azure Government Cloud and are designed to inter-operate with Microsoft 365 GCC, GCC High, and DoD. Use Defender for Identity public documentation as a [starting point](deploy-defender-identity.md) for deploying and operating the service.

## Licensing requirements

Defender for Identity for US Government customers requires one of the following Microsoft volume licensing offers:

| **GCC**                                   | **GCC High**                              | **DoD**                                   |
| ----------------------------------------- | ----------------------------------------- | ----------------------------------------- |
| Microsoft 365 GCC G5                      | Microsoft 365 E5 for GCC High             | Microsoft 365 G5 for DOD                  |
| Microsoft 365 G5 Security GCC             | Microsoft 365 G5 Security for GCC High    | Microsoft 365 G5 Security for DOD         |
| Standalone Defender for Identity licenses | Standalone Defender for Identity licenses | Standalone Defender for Identity licenses |

## URLs

To access Microsoft Defender for Identity for US Government offerings, use the appropriate addresses in this table:

|US Government offering  |Microsoft 365 Defender Portal  |Defender for Identity (classic) Portal | Sensor (agent) endpoint  |
|---------|---------|---------|---------|
|DoD    |   `security.microsoft.us`      | `<workspacename>.atp.azure.us` |  `<your-instance-name>sensorapi.atp.azure.us`       |
|GCC-H   |  `security.microsoft.us`       | `<workspacename>.atp.azure.us`    |  `<your-instance-name>sensorapi.atp.azure.us`       |
|GCC     |     `security.microsoft.com`    | `<workspacename>.gcc.atp.azure.com` |     `<your-instance-name>sensorapi.gcc.atp.azure.com`    |

You can also use the IP address ranges in our Azure service tag (**AzureAdvancedThreatProtection**) to enable access to Defender for Identity. For more information about service tags, see [Virtual network service tags](/azure/virtual-network/service-tags-overview) or download [the Azure IP Ranges and Service Tags – US Government Cloud file](https://www.microsoft.com/download/details.aspx?id=57063).

## Required connectivity settings

Use [this link](prerequisites.md#ports) to configure the minimum internal ports necessary that the Defender for Identity sensor requires.

## How to migrate from commercial to GCC

1. Go to the [Azure Portal](https://portal.azure.com/) > Azure Active Directory > Groups
1. Rename the following three groups (where _instanceName_ is the name of your workspace), by adding to them a " - commercial" suffix:
   - "Azure ATP _instanceName_ Administrators" --> "Azure ATP _instanceName_ Administrators - commercial"
   - "Azure ATP _instanceName_ Viewers" --> "Azure ATP _instanceName_ Viewers - commercial"
   - "Azure ATP _instanceName_ Users" --> "Azure ATP _instanceName_ Users - commercial"
1. Go to the GCC portal for Defender for Identity: `https://portal.gcc.atp.azure.com`
1. Create a new instance of Defender for Identity
1. Configure a Directory Service account
1. Download the new sensor agent package and copy the workspace key
1. Make sure sensors have access to *.gcc.atp.azure.com (directly or through proxy)
1. Uninstall existing sensor agents from the domain controllers
1. [Reinstall sensors with the new workspace key](install-sensor.md#install-the-sensor)
1. Migrate any settings after the initial sync (use the two portals to compare)
1. Eventually, delete the previous workspace (historical data will be lost)

>[!NOTE]
> No data is migrated from the commercial service.
>
> If you also have Microsoft Defender for Cloud Apps deployed, it should be migrated before you start the Defender for Identity migration.

## Feature parity with the commercial environment

Unless otherwise specified, new feature releases, including preview features, documented in [What's new with Defender for Identity](whats-new.md), will be available in GCC, GCC High, and DoD environments within 90 days of release in the Defender for Identity commercial environment. Preview features may not be supported in the GCC, GCC High, and DoD environments.

## Next steps

- [Deploy Microsoft Defender for Identity with Microsoft 365 Defender](deploy-defender-identity.md)
- [Check out the Defender for Identity forum!](<https://aka.ms/MDIcommunity>)
