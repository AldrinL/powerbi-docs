---
title: Connect to Snowflake with Power BI
description: Snowflake with SSO for Power BI
author: cpopell
ms.reviewer: 

ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/20/2019
ms.author: gepopell

LocalizationGroup: Connect to services
---
#  Connecting to Snowflake in Power BI Service

## Introduction

Connecting to Snowflake in the Power BI service only differs from other connectors in one way, which is that an additional capability is offered for AAD (with an option for SSO). Different parts of the integration require different administrative roles across Snowflake, Power BI, and Azure. You can also choose to enable AAD authentication without using SSO. Basic authentication works similarly to other connectors in the service.

If you're interested in configuring AAD integration, as well as optionally enabling SSO:
* If you are the Snowflake admin, please read the [Power BI SSO to Snowflake - Getting Started](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html) article in the Snowflake documentation.
* (SSO) If you are a Power BI admin, look at the 'Power BI Service configuration - Admin Portal' section
* (SSO) If you are a Power BI dataset creator, look at the 'Power BI Service configuration - Enabling a dataset' section

## Power BI Service configuration

### Admin Portal

If you want to enable SSO, the tenant admin is required to go to the Admin Portal and approve sending Power BI AAD credentials to  Snowflake.

![Tenant admin setting for Snowflake SSO](media/service-connect-snowflake/snowflakessotenant.png)

Navigate to your "Admin Portal", select the "Tenant Settings" sidebar item, scroll down to "Integration Settings" and you will see an option for "Snowflake  SSO".

As warned, you have to manually enable this to consent to sending your AAD token to the  Snowflake  servers. To enable it, click the 'Disabled' toggle, , press apply and wait for the settings change to take effect. It may take up to an hour for the service to propagate the configuration.

Once this is done you will be able to use reports with SSO.

### Configuring a Dataset with AAD

Once a report based on the Snowflake connector has been published to the web, in the Power BI web service, the dataset creator needs to navigate to the appropriate workspace, select 'Datasets', and select 'Settings' (under the '...' menu for additional actions next to the relevant dataset).

Due to the way that Power BI works, SSO will only work when no data sources are run through the on-premise data gateway.

* If you are using only a Snowflake source in your data model, then you can use SSO if you choose not to use the on-premise data gateway
* If you are using a Snowflake source alongside another source, then you can use SSO if none of the sources use the on-premise data gateway
* If you are using a Snowflake source through the on-premise data gateway, AAD credentials are not currently supported. This might be relevant in case you're trying to access a VNet from a single IP with the Gateway installed on it, rather than from the entire Power BI IP range.
* If you are using a Snowflake source alongside another source that requires a Gateway, you will be required to use Snowflake through the on-premise data gateway as well and will not be able to use SSO.

For more about how to use the on-premises data gateway, see the article [What is an on-premises data gateway?](https://docs.microsoft.com/power-bi/service-gateway-onprem)

If you aren't using the Gateway, you're all set. If you have Snowflake credentials configured on your on-premises data gateway, but are only using that data source in your model, you can click the toggle on the Dataset settings page to turn off the gateway for that data model.

![Dataset setting to toggle off Gateway](media/service-connect-snowflake/snowflake_gateway_toggle_off.png)

The dataset creator needs to select 'Data source credentials' and sign in. The dataset can be signed into Snowflake with Basic credentials or OAuth2 (AAD) credentials. If you choose to use AAD, the dataset can be enabled to use SSO. When this first user goes to sign in to Snowflake  for the dataset, they need to select the option that other users will have their Oauth2 credentials used to retrieve data. This will enable AAD SSO. Regardless of whether the initial user signs in with Basic authentication or OAuth2 (AAD), the AAD credentials are what will be sent for SSO. 

![Dataset setting for Snowflake SSO](media/service-connect-snowflake/snowflakessocredui.png)

Once this is done, any additional users should automatically use their AAD authentication to connect to data from that Snowflake dataset.

If you choose not to enable SSO, then users refreshing the report will use the credentials of the user who signed in, like most other Power BI reports.

### Troubleshooting

If you run into any issues with the integration, please refer to the Snowflake [troubleshooting guide](https://docs.snowflake.net/manuals/LIMITEDACCESS/oauth-powerbi.html#troubleshooting).

