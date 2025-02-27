---
title: Grant access to managed security service provider (MSSP)
description: Take the necessary steps to configure MSSP integration with the Microsoft Defender for Endpoint.
ms.service: defender-endpoint
ms.subservice: onboard
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: deniseb
audience: ITPro
ms.collection: 
- m365-security
- tier3
ms.topic: conceptual
search.appverid: met150
ms.date: 12/18/2020
---

# Grant managed security service provider (MSSP) access (preview)

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/microsoft-defender.md)]

**Applies to:**
- [Microsoft Defender for Endpoint Plan 1](microsoft-defender-endpoint.md)
- [Microsoft Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)

> Want to experience Defender for Endpoint? [Sign up for a free trial.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!IMPORTANT]
> Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.
>
> Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

To implement a multitenant delegated access solution, take the following steps:

1. Enable [role-based access control](rbac.md) in Defender for Endpoint and connect with Microsoft Entra ID groups.

2. Configure [Governance Access Packages](/azure/active-directory/governance/identity-governance-overview) for access request and provisioning.

3. Manage access requests and audits in [Microsoft MyAccess](/azure/active-directory/governance/entitlement-management-request-approve).

## Enable role-based access controls in Microsoft Defender for Endpoint

1. **Create access groups for MSSP resources in Customer Entra ID: Groups**

    These groups are linked to the Roles you create in Defender for Endpoint. To do so, in the customer Entra ID tenant, create three groups. In our example approach, we create the following groups:

    - Tier 1 Analyst
    - Tier 2 Analyst
    - MSSP Analyst Approvers

2. Create Defender for Endpoint roles for appropriate access levels in Customer Defender for Endpoint.

    To enable RBAC in the customer [Microsoft Defender portal](https://security.microsoft.com), go to **Settings** > **Endpoints** > **Permissions** > **Roles**, and then select **Turn on roles**. 

    Then, create RBAC roles to meet MSSP SOC Tier needs. Link these roles to the created user groups via assigned user groups. There are two possible roles: Tier 1 Analysts, and Tier 2 Analysts.

    - **Tier 1 Analysts** - Perform all actions except for live response and manage security settings.

    - **Tier 2 Analysts** - Tier 1 capabilities with the addition to [live response](live-response.md)

    For more information, see [Use role-based access control](rbac.md).

## Configure Governance Access Packages

1. **Add MSSP as Connected Organization in Customer Entra ID: Identity Governance**

    Adding the MSSP as a connected organization allows the MSSP to request and have access provisioned.

    To do so, in the customer Entra ID tenant, access Identity Governance: Connected organization. Add a new organization and search for your MSSP Analyst tenant via Tenant ID or Domain. We suggest creating a separate Entra ID tenant for your MSSP Analysts.

2. **Create a resource catalog in Customer Entra ID: Identity Governance**

    Resource catalogs are a logical collection of access packages, created in the customer Entra ID tenant.

    To do so, in the customer Entra ID tenant,  access Identity Governance: Catalogs, and add **New Catalog**. In our example, it's called, **MSSP Accesses**.

    :::image type="content" source="media/goverance-catalog.png" alt-text="The new catalog page" lightbox="media/goverance-catalog.png":::

    Further more information, see [Create a catalog of resources](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **Create access packages for MSSP resources Customer Entra ID: Identity Governance**

    Access packages are the collection of rights and accesses that a requestor is granted upon approval.

    To do so, in the customer Entra ID tenant, access Identity Governance: Access Packages, and add **New Access Package**. Create an access package for the MSSP approvers and each analyst tier. For example, the following Tier 1 Analyst configuration creates an access package that:

    - Requires a member of the Entra ID group **MSSP Analyst Approvers** to authorize new requests
    - Has annual access reviews, where the SOC analysts can request an access extension
    - Can only be requested by users in the MSSP SOC Tenant
    - Access auto expires after 365 days

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/new-access-package.png" alt-text="The New access package page" lightbox="media/new-access-package.png":::

    For more information, see [Create a new access package](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Provide access request link to MSSP resources from Customer Entra ID: Identity Governance**

    The My Access portal link is used by MSSP SOC analysts to request access via the access packages created. The link is durable, meaning the same link may be used over time for new analysts. The analyst request goes into a queue for approval by the **MSSP Analyst Approvers**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="media/access-properties.png" alt-text="The Properties page" lightbox="media/access-properties.png":::

    The link is located on the overview page of each access package.

## Manage access

1. Review and authorize access requests in Customer and/or MSSP MyAccess.

    Access requests are managed in the customer My Access, by members of the MSSP Analyst Approvers group.

    To do so, access the customer's MyAccess using: `https://myaccess.microsoft.com/@<Customer Domain>`.

    Example: `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Approve or deny requests in the **Approvals** section of the UI.

    At this point, analyst access is provisioned, and each analyst should be able to access the customer's Microsoft Defender portal: `https://security.microsoft.com/?tid=<CustomerTenantId>`

## Related articles

- [Access the MSSP customer portal](access-mssp-portal.md)
- [Configure alert notifications](configure-mssp-notifications.md)
- [Fetch alerts from customer tenant](api/fetch-alerts-mssp.md)

[!INCLUDE [Microsoft Defender for Endpoint Tech Community](../includes/defender-mde-techcommunity.md)]
