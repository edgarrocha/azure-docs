---
title: Provision access to resource groups and subscriptions for DevOps actions
description: Step-by-step guide showing how to provision access to entire resource groups and subscriptions through Microsoft Purview DevOps policies
author: inward-eye
ms.author: vlrodrig
ms.service: purview
ms.subservice: purview-data-policies
ms.topic: how-to
ms.date: 11/14/2022
ms.custom:
---
# Provision access to system metadata in resource groups or subscriptions

[DevOps policies](concept-policies-devops.md) are a type of Microsoft Purview access policies. They allow you to manage access to system metadata (DMVs and DMFs) via *SQL Performance Monitoring* or *SQL Security Auditing* actions. They can be created only on data sources that have been registered for *Data use management* in Microsoft Purview. These policies are configured directly in the Microsoft Purview governance portal, and after being saved they get automatically published and then get enforced by the data source. Microsoft Purview access policies apply to Azure AD Accounts only.

In this guide we cover how to register an entire resource group or subscription and then create a single policy that will manage access to **all** data sources in that resource group or subscription. That single policy will cover all existing data sources and any data sources that are created afterwards.

## Prerequisites
[!INCLUDE [Access policies generic pre-requisites](./includes/access-policies-prerequisites-generic.md)]
[!INCLUDE [Access policies Azure SQL Database pre-requisites](./includes/access-policies-prerequisites-azure-sql-db.md)]

**Only these data sources are enabled for access policies on resource group or subscription**. Follow the **Prerequisites** section that is specific to the data source(s) in these guides:
* [DevOps policies on an Azure SQL Database](./how-to-policies-devops-azure-sql-db.md#prerequisites)
* [DevOps policies on an Arc-enabled SQL Server](./how-to-policies-devops-arc-sql-server.md#prerequisites)

## Microsoft Purview Configuration
[!INCLUDE [Access policies generic configuration](./includes/access-policies-configuration-generic.md)]

### Register the subscription or resource group for Data Use Management
The subscription or resource group needs to be registered with Microsoft Purview to later define access policies.

To register your subscription or resource group, follow the **Prerequisites** and **Register** sections of this guide:

- [Register multiple sources in Microsoft Purview](register-scan-azure-multiple-sources.md#prerequisites)

After you've registered your resources, you'll need to enable Data Use Management. Data Use Management needs certain permissions and can affect the security of your data, as it delegates to certain Microsoft Purview roles to manage access to the data sources. **Go through the secure practices related to Data Use Management in this guide**: [How to enable Data Use Management](./how-to-enable-data-use-management.md) 

In the end, your resource will have the  **Data Use Management** toggle **Enabled**, as shown in the screenshot:

![Screenshot shows how to register a resource group or subscription for policy by toggling the enable tab in the resource editor.](./media/how-to-policies-data-owner-resource-group/register-resource-group-for-policy.png)

>[!Important]
> - If you want to create a policy on a resource group or subscription and have it enforced in Arc-enabled SQL servers, you will need to also register those servers independently and enable *Data use management* to provide their App ID: [See this document](./how-to-policies-devops-arc-sql-server.md#register-data-sources-in-microsoft-purview).


## Create a new DevOps policy
Follow this link for the steps to [create a new DevOps policy in Microsoft Purview](how-to-policies-devops-authoring-generic.md#create-a-new-devops-policy).

## List DevOps policies
Follow this link for the steps to [list DevOps policies in Microsoft Purview](how-to-policies-devops-authoring-generic.md#list-devops-policies).

## Update a DevOps policy
Follow this link for the steps to [update a DevOps policies in Microsoft Purview](how-to-policies-devops-authoring-generic.md#update-a-devops-policy).

## Delete a DevOps policy
Follow this link for the steps to [delete a DevOps policies in Microsoft Purview](how-to-policies-devops-authoring-generic.md#delete-a-devops-policy).


### Test the policy
To test the policy see the DevOps policy guides for the underlying data sources listed in the [next steps section](#next-steps) of this document.

## Next steps
Check the blog and related docs
* Blog: [Microsoft Purview DevOps policies enable at scale access provisioning for IT operations](https://techcommunity.microsoft.com/t5/microsoft-purview-blog/microsoft-purview-devops-policies-enable-at-scale-access/ba-p/3604725)
* Video: [Reduce the effort with Microsoft Purview DevOps policies on resource groups](https://youtu.be/yMMXCeIFCZ8)
* Doc: [Microsoft Purview DevOps policies on Arc-enabled SQL Server](./how-to-policies-devops-arc-sql-server.md)
* Doc: [Microsoft Purview DevOps policies on Azure SQL DB](./how-to-policies-devops-azure-sql-db.md)
