---
title: Intro to datasets across workspaces (Preview)
description: Learn how you can share a dataset with users across the organization. Then they can build reports based on your dataset in their own workspaces.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/16/2019
ms.author: maggies

LocalizationGroup: Share your work
---
# Intro to datasets across workspaces (Preview)

Business intelligence is a collaborative activity. It's important to establish standardized datasets that can be the 'one source of truth.' Then discovering and reusing those standardized datasets is key. When expert data modelers in your organization create and share optimized datasets, report creators can start with those datasets to build accurate reports. Then your organization has consistent data for making decisions, and a healthy data culture.

![Select a shared dataset](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

In Power BI, dataset creators can control who has access to their data by using the [Build permission](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Dataset creators can also *certify* or *promote* datasets so others can discover them. That way, report authors know which datasets are high quality and official, and they can use those datasets wherever they author in Power BI. Tenant administrators have a new tenant setting to [govern the use of datasets across workspaces](service-datasets-admin-across-workspaces.md).

## Dataset sharing and the new workspace experience

Building reports based on datasets in different workspaces, and copying reports to different workspaces, are tightly coupled with the [new workspace experience](service-create-the-new-workspaces.md):

- In the service, when you open the dataset catalog from a new workspace experience, the dataset catalog shows datasets that are in your My Workspace and in other new workspace experience workspaces. 
- When you open the dataset catalog from a classic workspace, you only see the datasets in that workspace, not the ones in other workspaces.
- In Power BI Desktop, you can publish Live Connect reports to different workspaces, as long as their datasets are in new experience workspaces.
- When copying reports across workspaces, the target workspace needs to be a new experience workspace.

## Discover datasets (Preview)

When building a report on top of an existing dataset, the first step is to connect to the dataset, either in the Power BI service or Power BI Desktop. Read about [discovering datasets from different workspaces (Preview)](service-datasets-discover-across-workspaces.md)

## Copy a report

When you find a report you like, in a workspace or an app, you can make a copy of it, and then modify it to fit your needs. You don't have to worry about creating the data model. That's already created for you. And it's much easier to modify an existing report than it is to start from scratch. Read more about [copying reports](service-datasets-copy-reports.md).

## Build permission for datasets

With the Build permission type, if you're a dataset creator you can determine who in your organization can build new content on your datasets. People with build permission can also build new content on the dataset outside Power BI, such as Excel sheets via Analyze in Excel, XMLA, and export. Read more about the [Build permission](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## Promotion and certification

If you create datasets, when you create one that others can benefit from, you can make it easier for them to discover it by [promoting your dataset](service-datasets-promote.md). You can also request that experts in your organization [certify your dataset](service-datasets-certify.md).

## Licensing

The specific features and experiences built on shared dataset capabilities are licensed according to their existing scenarios. For example:

- In general, discovering and connecting to shared datasets is available to anyone. However, users without a Pro license can only connect to datasets that reside in their personal My Workspace.
- Users without a Pro license can only consume reports and dashboards built on a shared dataset if both workspaces (the one containing the content and the one containing the dataset) are hosted in a Premium capacity.
- In Power BI Desktop, users without a Pro license can only see datasets from their My Workspace.
- Copying reports between workspaces requires a Pro license.
- Copying reports from an app requires a Pro license, as was required for organizational content packs.
- Promoting and certifying datasets requires a Pro license.

## Considerations and limitations

- Building a report on top of a dataset in a different workspace requires the new workspace experience at both ends: The report needs to be in a new workspace experience and the dataset needs to be in a new workspace experience.
- Say you create a report in Workspace A that's based on a dataset in Workspace B. When you create an app for Workspace A, you can only include that report in the Workspace A app if you are also a member of Workspace B.
- In a classic workspace, the dataset discovery experience only shows the datasets in that workspace.
- If you want to add a report based on a shared dataset to an app, you have to be a member of the dataset workspace. This is a known issue.
- By design, “Publish to web” doesn’t work for a report based on a shared dataset.
- If two people are members of a workspace that is accessing a shared dataset, it's possible that only one of them can see the related dataset in the workspace. Only people with at least Read access to the dataset can see the shared dataset. 

## Next steps

- [Promote datasets](service-datasets-promote.md)
- [Certify datasets](service-datasets-certify.md)
- [Govern the use of datasets across workspaces](service-datasets-admin-across-workspaces.md)
- Questions? [Try asking the Power BI Community](http://community.powerbi.com/)
