---
title: Organize work in the new workspaces in Power BI
description: Learn about the new workspaces, which are collections of dashboards and reports built to deliver key metrics for your organization.
author: maggiesMSFT
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/07/2020
ms.author: maggies

LocalizationGroup: Share your work
---

# Organize work in the new workspaces in Power BI

*Workspaces* are places to collaborate with colleagues to create collections of dashboards, reports, datasets, and paginated reports. The new workspace experience helps you better manage access to content. This article describes the new workspaces, and how they differ from the classic workspaces.  As with classic workspaces, you still use them to create and distribute apps. Ready to create a new workspace? Read [Create a new workspace experience](service-create-the-new-workspaces.md).

New, upgraded workspaces can coexist side by side with existing classic workspaces. The new workspace experience is the default workspace type. You can still create and use [classic workspaces](service-create-workspaces.md) based on Microsoft 365 Groups, if you need to. Ready to migrate your classic workspace? See [Upgrade classic workspaces to the new workspaces in Power BI](service-upgrade-workspaces.md) for details.

With the new workspaces, you can:

- Assign workspace roles to user groups: security groups, distribution lists, Microsoft 365 groups, and individuals.
- Create a workspace in Power BI without creating an underlying, associated Microsoft 365 group. All the workspace administration is in Power BI, not in Microsoft 365.
- Continue managing user access to content through Microsoft 365 groups, if you want. You just add a Microsoft 365 group in the workspace access list.
- Use more granular workspace roles for more flexible permissions management in a workspace.

Power BI continues to list all Microsoft 365 Groups that you're a member of. This avoids changing existing workflows.

## New and classic workspace differences

With the new workspaces, we've redesigned some features. Here are the main differences.

- Creating these workspaces doesn't create Microsoft 365 groups like classic workspaces do. However, you can now use a Microsoft 365 group to give users access to your workspace by assigning it a role.
- In classic workspaces, you can add only individuals to the members and admin lists. In the new workspaces, you can add multiple Active Directory security groups, distribution lists, or Microsoft 365 groups to these lists, for easier user management.
- You can create an organizational content pack from a classic workspace. You can't create one from the new workspaces.
- You can consume an organizational content pack from a classic workspace. You can't consume one from the new workspaces.

### Workspace features that work differently

Some features work differently from current workspaces in the new workspaces. These differences are intentional, based on feedback we've received from customers. They enable a more flexible approach to collaboration with workspaces.

- **Licensing enforcement**: Publishing reports to new workspace experience enforces existing licensing rules. Users collaborating in workspaces or sharing content to others in the Power BI service need a Power BI Pro license. Users without a Pro license see the error "Only users with Power BI Pro licenses can publish to this workspace."
- **Members can or can't reshare**: The Contributor role replaces this setting.
- **Read-only workspaces**: Instead of granting users read-only access to a workspace, assign them to the Viewer role. It allows similar read-only access to the content in a workspace.
- **Users without a Pro license** can access the workspace if the workspace is in a Power BI Premium capacity, but only if they have the Viewer role.
- **Allow users to export data**: Users with the Viewer role can export data if they have Build permission on the datasets in the workspace. Read more about [Build permission for datasets](../connect-data/service-datasets-build-permissions.md).
- No **Leave workspace** button.

### Workspace contact list

The new **Contact list** feature allows you to specify which users receive notification about issues occurring in the workspace. By default, any user or group specified as a workspace admin is notified, but you can customize the list. Users or groups listed in the contact list will be shown in the user interface (UI) to help users get help related to the workspace. 

Read more about the [setting the workspace contact list](service-create-the-new-workspaces.md#workspace-contact-list).

### Workspace OneDrive

The Workspace OneDrive feature allows you to configure a Microsoft 365 Group whose SharePoint Document Library file storage is available to workspace users. You create the group outside of Power BI.

Power BI doesn't synchronize permissions of users or groups who are configured to have workspace access with the Microsoft 365 Group membership. The best practice is to manage workspace access through the same Microsoft 365 Group whose file storage you configure in this setting.

Read about how to [set and access the Workspace OneDrive](service-create-the-new-workspaces.md#workspace-onedrive).  

## Roles in the new workspaces

To grant access to a new workspace, add user groups or individuals to one of the workspace roles: admins, members, contributors, or viewers. Everyone in a user group gets the role you've defined. If an individual is in several user groups, they get the highest level of permission provided by the roles they're assigned.

Roles let you manage who can do what in a workspace, so teams can collaborate. New workspaces allow you to assign roles to individuals, and to user groups: security groups, Microsoft 365 groups, and distribution lists.

When you assign roles to a user group, the individuals in the group have access to content. If you nest user groups, all the contained users have permission.

[!INCLUDE [power-bi-workspace-roles-table](../includes/power-bi-workspace-roles-table.md)]

> [!NOTE]
> To enforce row-level security (RLS) for users browsing content in a workspace, use the Viewer role. To enforce RLS without giving access to the workspace, publish a Power BI app to those users, or use sharing to distribute content.

## Licensing
Everyone you add to a workspace in the shared capacity needs a Power BI Pro license. In the workspace, these users can all collaborate on dashboards and reports that you plan to publish to a wider audience, or even to your entire organization. 

If you want to distribute content to others inside your organization, you can assign Power BI Pro licenses to those users or place the workspace in a Power BI Premium capacity.

When the workspace is in a Power BI Premium capacity, users with the Viewer role can access the workspace even if they don't have a Power BI Pro license. However, if you assign these users a higher role like Admin, Member, or Contributor, they're prompted to start a Pro Trial when they try to access the workspace. To make use of the Viewer role for users without Pro licenses, make sure they don't have other workspace roles, too, either individually or through a user group.

> [!NOTE]
> Publishing reports to new workspace experience has stricter enforcement of existing licensing rules. If you try to publish from Power BI Desktop or other client tools without a Pro license, you see the error, "Only users with Power BI Pro licenses can publish to this workspace."

## Administering new workspace experience workspaces

Administration for new workspace experience workspaces is now in the Power BI admin portal. Power BI admins decide who in an organization can create workspaces and distribute apps. Admins can see the state of all the workspaces in their organization. They can also manage and recover workspaces. Read more about [Creating the new workspaces](../admin/service-admin-portal.md#create-the-new-workspaces) in the Admin portal article.

## Guest users

By default, [Azure AD B2B Guest users](../admin/service-admin-azure-ad-b2b.md) can't access workspaces. Power BI admins can [allow external guest users to edit and manage content in the organization](../admin/service-admin-azure-ad-b2b.md#guest-users-who-can-edit-and-manage-content). Enabled Guest users can access workspaces to which they have permission.

## Auditing

The following activities are audited by Power BI for new workspace experience workspaces.

| Friendly name | Operation name |
|---|---|
| Created Power BI folder | CreateFolder |
| Deleted Power BI folder | DeleteFolder |
| Updated Power BI folder | UpdateFolder |
| Updated Power BI folder access| UpdateFolderAccess |

Read more about [Power BI auditing](../admin/service-admin-auditing.md).

## Limitations and considerations

Limitations to be aware of:

- Workspaces can contain a maximum of 1,000 datasets, or 1,000 reports per dataset. 
- A person with a Power BI Pro license can be a member of a maximum 1,000 workspaces.
- Power BI publisher for Excel isn't supported.

## Frequently asked questions

**Are links to existing content affected by the new workspace experience**

No. Links to existing items in classic workspaces aren't affected by the new workspace experience. The general availability (GA) of the new workspace experience changes the default workspace you create, but doesn't change existing workspaces. 

**Are existing workspaces upgraded to the new workspace experience with GA**

No. The new workspace experience GA only changes the default workspace type to the new workspace experience. Existing classic workspaces that are based on Microsoft 365 Groups remain unchanged.

**Are workspaces still automatically created for Microsoft 365 Groups**

Yes. Since we support both types of workspaces side by side, we continue to list all Microsoft 365 Groups you have access to in the workspaces list.

## Next steps

* [Create the new workspaces in Power BI](service-create-the-new-workspaces.md)
* [Create the classic workspaces](service-create-workspaces.md)
* [Install and use apps in Power BI](service-create-distribute-apps.md)
* Questions? [Try asking the Power BI Community](https://community.powerbi.com/)

