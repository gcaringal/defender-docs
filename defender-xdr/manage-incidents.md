---
title: Manage incidents in Microsoft Defender
description: Learn how to assign, update the status,
ms.service: defender-xdr
f1.keywords: 
  - NOCSH
ms.author: diannegali
author: diannegali
ms.localizationpriority: medium
manager: deniseb
audience: ITPro
ms.collection: 
  - m365-security
  - tier1
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid: 
  - MOE150
  - MET150
ms.date: 08/19/2024
appliesto: 
- Microsoft Defender XDR
- Microsoft Sentinel in the Microsoft Defender portal
---

# Manage incidents in Microsoft Defender

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/microsoft-defender.md)]

Incident management is critical to ensuring that incidents are named, assigned, and tagged to optimize time in your incident workflow and more quickly contain and address threats.

You can manage incidents from **Incidents & alerts > Incidents** on the quick launch of the Microsoft Defender portal ([security.microsoft.com](https://security.microsoft.com)). Here's an example.

:::image type="content" source="/defender/media/incidents-queue/fig1-manageincidents.png" alt-text="Screenshot highlighting the manage incident option within the incident queue and quick launch pane in the Microsoft Defender portal." lightbox="/defender/media/incidents-queue/fig1-manageincidents.png":::

Here are the ways you can manage your incidents:

- [Edit the incident name](#edit-the-incident-name).
- [Assign or change severity](#assign-or-change-incident-severity).
- [Add incident tags](#add-incident-tags).
- [Assign the incident to a user account](#assign-an-incident).
- [Resolve them](#resolve-an-incident).
- [Specify its classification](#specify-the-classification).
- [Add comments](#add-comments).
- Assess the activity audit and add comments in the [Activity log](#activity-log).
- [Export incident data to PDF](#export-incident-data-to-pdf).

You can manage incidents from the **Manage incident** pane for an incident. Here's an example.

:::image type="content" source="/defender/media/incidents-queue/fig2-new-manageincidents.png" alt-text="Screenshot showing the Manage incident pane in the Microsoft Defender portal." lightbox="/defender/media/incidents-queue/fig2-new-manageincidents.png":::

You can display this pane from the **Manage incident** link on the:

- **Alert story** page.
- Properties pane of an incident in the incident queue.
- **Summary** page of an incident.
- Manage incident option located on the upper right side of the Incident page.

In cases where you want to move alerts from one incident to another, you can also do so from the **Alerts** tab, thus creating a larger or smaller incident that includes all relevant alerts.

## Edit the incident name

Microsoft Defender automatically assigns a name based on alert attributes such as the number of endpoints affected, users affected, detection sources or categories. The incident name allows you to quickly understand the scope of the incident. For example: *Multi-stage incident on multiple endpoints reported by multiple sources.*

You can edit the incident name from the **Incident name** field on the **Manage incident** pane.

> [!NOTE]
> Incidents that existed before the rollout of the automatic incident naming feature will retain their name.

## Assign or change incident severity

You can assign or change the severity of an incident from the **Severity** field on the **Manage incident** pane. The severity of an incident is determined by the highest severity of the alerts associated with it. The severity of an incident can be set to *high*, *medium*, *low*, or *informational*.

## Add incident tags

You can add custom tags to an incident, for example to flag a group of incidents with a common characteristic. You can later filter the incident queue for all incidents that contain a specific tag.

The option to select from a list of previously used and selected tags appear after you start typing.

An incident can have system tags and/or custom tags with certain color backgrounds. Custom tags use the white background while system tags typically use red or black background colors. System tags identify the following in an incident:

- A **type of attack**, like credential phishing or BEC fraud
- **Automatic actions**, like automatic investigation and response and automatic attack disruption
- **Defender Experts** handling an incident
- **Critical assets** involved in the incident

> [!TIP]
> Microsoft's Security Exposure Management, based on predefined classifications, automatically tags devices, identities, and cloud resources as a **critical asset**. This out-of-the-box capability ensures the protection of an organization's valuable and most important assets. It also helps security operations teams to prioritize investigation and remediation. Know more about [critical asset management](/security-exposure-management/critical-asset-management).

## Assign an incident

You can select the **Assign to** box and specify the user account to assign an incident. To reassign an incident, remove the current assignment account by selecting the "x" next to the account name and then select the **Assign to** box. Assigning ownership of an incident assigns the same ownership to all the alerts associated with it.

You can get a list of incidents assigned to you by filtering the incident queue. 

1. From the incident queue, select **Filters**.
2. In the **Incident assignment** section, clear **Select all**. Select **Assigned to me**, **Assigned to another user**, or **Assigned to a user group**.
3. Select **Apply**, and then close the **Filters** pane.

You can then save the resulting URL in your browser as a bookmark to quickly see the list of incidents assigned to you.

## Resolve an incident

When an incident is remediated and resolved, select **Resolved** from the **Status** drop-down list. Resolving an incident also resolves all the linked and active alerts related to the incident.

When you change an incident's status to **Resolved**, a new field is displayed immediately following the **Status** field. Enter a note in this field that explains why you consider the incident resolved. This note is visible in the activity log of the incident, near the entry recording the incident's resolution.

:::image type="content" source="/defender/media/incidents-queue/resolve-incidents.png" alt-text="Screenshot of incident management panel with incident resolution note.":::

On both the incidents queue page and the incident page of a resolved incident, you can see the incident resolution note in the side panel, in the *Incident details* section.

:::image type="content" source="/defender/media/incidents-queue/resolution-note-in-side-panel.png" alt-text="Screenshot of appearance of resolution note in the incident details panel." lightbox="/defender/media/incidents-queue/resolution-note-in-side-panel.png":::

Resolving an incident also resolves all the linked and active alerts related to the incident. An incident that isn't resolved displays as **Active**.

## Specify the classification

From the **Classification** field, you specify whether the incident is:

- **Not set** (the default).
- **True positive** with a type of threat. Use this classification for incidents that accurately indicate a real threat. Specifying the threat type helps your security team see threat patterns and act to defend your organization from them.
- **Informational, expected activity** with a type of activity. Use the options in this category to classify incidents for security tests, red team activity, and expected unusual behavior from trusted apps and users.
- **False positive** for types of incidents that you determine can be ignored because they're technically inaccurate or misleading.

Classifying incidents and specifying their status and type helps tune Microsoft Defender XDR to provide better detection determination over time.

## Add comments

You can add multiple comments to an incident with the **Comment** field. The comment field supports text and formatting, links, and images. Each comment is limited to 30,000 characters.

All comments are added to the historical events of the incident. You can see the comments and history of an incident from the **Comments and history** link on the **Summary** page.

## Activity log

The **Activity log** displays a list of all the comments and actions performed on the incident, known as *Audits and comments*. All changes made to the incident, whether by a user or by the system, are recorded in the activity log. The activity log is available from the **Activity log** option on the incident page or on the incident side pane.

:::image type="content" source="/defender/media/incidents-queue/fig3-manageincidents-new.png" alt-text="Screenshot highlighting the activity log option from the incident page in the Microsoft Defender portal." lightbox="/defender/media/incidents-queue/fig3-manageincidents-new.png":::

You can filter the activities within the log by comments and actions. Click the **Content: Audits, Comments** then select the content type to filter activities. Here's an example.

:::image type="content" source="/defender/media/incidents-queue/fig4-manageincidents.png" alt-text="Screenshot highlighting the filter options within the activity log pane from the incident page in the Microsoft Defender portal." lightbox="/defender/media/incidents-queue/fig4-manageincidents.png":::

You can also add your own comments using the comment box available within the activity log. The comment box accepts text and formatting, links, and images.

:::image type="content" source="/defender/media/incidents-queue/fig5-res-manageincidents.png" alt-text="Screenshot highlighting the comment box from the incident page in the Microsoft Defender portal." lightbox="/defender/media/incidents-queue/fig5-manageincidents.png":::

## Export incident data to PDF

> [!IMPORTANT]
> Some information in this article relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.
>
> The export incident data feature is currently available to Microsoft Defender XDR and Microsoft Defender unified security operations center (SOC) platform customers with the Microsoft Copilot for security license.

You can export an incident's data to PDF through the **Export incident as PDF** function and save it into PDF format. This function allows security teams to review an incident's details offline at any given time.

The incident data exported includes the following information:

- An overview containing the incident details
- The [attack story](investigate-incidents.md#attack-story) graph and threat categories
- The impacted [assets](investigate-incidents.md#assets), covering up to 10 assets for each asset type
- The [evidence list](investigate-incidents.md#evidence-and-response) covering up to 100 items
- Supporting data, including all [related alerts](investigate-incidents.md#alerts) and activities recorded in the [activity log](#activity-log)

Here's an example of the exported PDF:

:::image type="content" source="/defender/media/incidents-queue/export-incident-results-small.png" alt-text="Screenshot of the exported PDF's first page." lightbox="/defender/media/incidents-queue/export-incident-results.png":::

If you have the [Copilot for Security](/security-copilot/microsoft-security-copilot) license, the exported PDF contains the following additional incident data:

- [Incident summary](security-copilot-m365d-incident-summary.md)
- [Incident report](security-copilot-m365d-create-incident-report.md)

The export to PDF function is also available in the Copilot side panel of a generated incident report.

![Screenshot of additional actions in the incident report results card.](/defender/media/incidents-queue/export-incident-more-actions1.png)

To generate the PDF, perform the following steps:

1. Open an incident page. Select the **More actions** ellipsis (...) on the upper right corner and choose **Export incident as PDF**. The function becomes grayed out while the PDF is being generated.

   :::image type="content" source="/defender/media/incidents-queue/export-incident-main-small.png" alt-text="Screenshot highlighting the export incident to PDF option." lightbox="/defender/media/incidents-queue/export-incident-main.png":::

1. A dialog box appears, indicating that the PDF is being generated. Select **Got it** to close the dialog box. Additionally, a status message indicating the current state of the download appears below the incident title. The export process may take a few minutes depending on the incident's complexity and the amount of data to be exported.

   :::image type="content" source="/defender/media/incidents-queue/export-incident-predownload-small.png" alt-text="Screenshot highlighting export message and status before download." lightbox="/defender/media/incidents-queue/export-incident-predownload.png":::

1. Once the PDF is ready, the status message indicates that the PDF is ready and another dialog box appears. Select **Download** from the dialog box to save the PDF to your device.

   :::image type="content" source="/defender/media/incidents-queue/export-incident-download-small.png" alt-text="Screenshot highlighting export message and status when download is available." lightbox="/defender/media/incidents-queue/export-incident-download.png":::

The report is cached for a couple of minutes. The system provides the previously generated PDF if you try to export the same incident again within a short time frame. To generate a newer version of the PDF, wait for a few minutes for the cache to expire.

## Next steps

For new incidents, begin your [investigation](investigate-incidents.md).

For in-process incidents, continue your [investigation](investigate-incidents.md).

For resolved incidents, perform a [post-incident review](respond-first-incident-remediate.md).

## See also

- [Incidents overview](incidents-overview.md)
- [Prioritize incidents](incident-queue.md)
- [Investigate incidents](investigate-incidents.md)

[!INCLUDE [Microsoft Defender XDR rebranding](../includes/defender-m3d-techcommunity.md)]
