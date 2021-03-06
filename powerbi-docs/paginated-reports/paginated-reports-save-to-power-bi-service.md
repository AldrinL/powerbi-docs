---
title: "Publish a paginated report to the Power BI service"
description: In this tutorial, you learn to publish a paginated report to the Power BI service by uploading it from your local computer.  
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 01/03/2020
---

# Publish a paginated report to the Power BI service

In this article, you learn about publishing a paginated report to the Power BI service by uploading it from your local computer. You can upload paginated reports to your My Workspace or any other workspace, as long as the workspace is in a Premium capacity. Look for the diamond icon ![Power BI Premium capacity diamond icon](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) next to the workspace name. 

If your report data source is on premises, you need to create a gateway after you upload the report. See the [Create a gateway](#create-a-gateway) section later in this article.

## Add a workspace to a Premium capacity

If the workspace doesn't have the diamond icon ![Power BI Premium capacity diamond icon](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) next to the name, you need to add the workspace to a Premium capacity. 

1. Select **Workspaces**, select the ellipsis (**...**) next to the workspace name, then select **Edit workspace**.

    ![Select Edit workspace](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. In the **Edit workspace** dialog box, expand **Advanced**, then slide **Dedicated capacity** to **On**.

    ![Select Dedicated capacity](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   You may not be able to change it. If not, then contact your Power BI Premium capacity admin to give you assignment rights to add your workspace to a Premium capacity.

## From Report Builder, publish a paginated report

1. Create your paginated report in Report Builder and save it to your local computer.

1. On the Report Builder **File** menu, select **Save as**.

    ![File menu > Save > Save as](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-save-as.png)

    If you aren't signed in to Power BI yet, you need to sign in or create an account now. In the upper-right corner of Report Builder, select **Sign in** and complete the steps.

2. In the list of workspaces on the left, select a workspace with the diamond icon ![Power BI Premium capacity diamond icon](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) next to its name. Type a **File name** in the box > **Save**. 

    ![Select a Premium workspace](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-workspace.png)

4. Open the Power BI service in a browser and browse to the Premium workspace where you published the paginated report. On the **Reports** tab, you see your report.

    ![Paginated report in Reports list](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

5. Select the paginated report to open it in the Power BI service. If it has parameters, you need to select them before you can view the report.

    ![Select parameters](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. If your report data source is on premises, read about how to [create a gateway](#create-a-gateway) in this article to access the data source.

## From the Power BI service, upload a paginated report

You can also start from the Power BI service and upload a paginated report.

1. Create your paginated report in Report Builder and save it to your local computer.

1. Open the Power BI service in a browser and browse to the Premium workspace where you want to publish the report. Note the diamond icon ![Power BI Premium capacity diamond icon](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) next to the name. 

1. Select **Get Data**.

    ![Power BI Get Data](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. In the **Files** box, select **Get**.

    ![Power BI Get Files](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Select **Local file** > browse to the paginated report > **Open**.

    ![Select Local File](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Select **Continue** > **Edit credentials**.

    ![Select Edit credentials](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Configure your credentials > **Sign in**.

    ![Edit credentials](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   On the **Reports** tab, you see your report.

    ![Paginated report in Reports list](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Select it to open it in the Power BI service. If it has parameters, you need to select them before you can view the report.
 
    ![Select parameters](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

6. If your report data source is on premises, read about how to [create a gateway](#create-a-gateway) in this article to access the data source.

## Create a gateway

Just like any other Power BI report, if the report data source is on premises, then you need to create or connect to a gateway to access the data.

1. Next to the report name, select **Manage**.

   ![Manage the paginated report](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. See the Power BI service article [What is an on-premises data gateway](../service-gateway-onprem.md) for details and next steps.

### Gateway limitations

Currently gateways don't support multi-value parameters.


## Next steps

- [View a paginated report in the Power BI service](../consumer/paginated-reports-view-power-bi-service.md)
- [What are paginated reports in Power BI Premium?](paginated-reports-report-builder-power-bi.md)
- [Tutorial: Embed Power BI paginated reports into an application for your customers](../developer/embed-paginated-reports-customers.md)

