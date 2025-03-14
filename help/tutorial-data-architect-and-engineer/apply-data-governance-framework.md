---
title: Apply the data governance framework
seo-title: Apply the data governance framework | Getting Started with Adobe Experience Platform for Data Architects and Data Engineers
breadcrumb-title: Apply the data governance framework
description: In this lesson, you will apply the data governance framework to the data you've ingested into your sandbox. 
role: Data Architect
feature: Data Governance
kt: 4348
thumbnail: 4348-apply-data-governance-framework.jpg
exl-id: 3cc3c794-5ffd-41bf-95d8-be5bca2e3a0f
---
# Apply the data governance framework

<!--15min-->

In this lesson, you will apply the data governance framework to the data you've ingested into your sandbox. 

Adobe Experience Platform Data Governance allows you to manage customer data and ensure compliance with regulations, restrictions, and policies applicable to data use. It plays a key role within Experience Platform at various levels, including  controlling usage of data.

Before you begin the exercises, watch these short videos about data governance:
>[!VIDEO](https://video.tv.adobe.com/v/36653?quality=12&learn=on)

>[!VIDEO](https://video.tv.adobe.com/v/29708?quality=12&learn=on)

<!--
## Permissions required

In the [Configure Permissions](configure-permissions.md) lesson, you set up all the access controls required to complete this lesson, specifically:

* Permission items **[!UICONTROL Data Governance]** > **[!UICONTROL Manage Usage Labels]**, **[!UICONTROL Manage Data Usage Policies]** and **[!UICONTROL View Data Usage Policies]**
* Permission items **[!UICONTROL Data Management]** > **[!UICONTROL View Datasets]** and **[!UICONTROL Manage Datasets]**
* Permission item **[!UICONTROL Sandboxes]** > `Luma Tutorial`
* User-role access to the `Luma Tutorial Platform` Product Profile
-->

## Business Scenario

Luma makes a promise to members of their Loyalty program, that Loyalty data will not be shared with any third parties. We will implement this scenario in the rest of the lesson.

## Apply data governance labels

The first step in the data governance process, is to apply governance labels to your data. Before we do that, let's take a quick look at what labels are available:

1. In the Platform user interface, select **[!UICONTROL Policies]** in the left navigation
1. Go to the **[!UICONTROL Labels]** tab to see all labels in the account.

There are many out-of-the-box labels, plus you can create your own via the [!UICONTROL Create label] button. There are three main types: [!UICONTROL Contract labels], [!UICONTROL Identity labels], and [!UICONTROL Sensitive labels] that correspond to common reasons data might be restricted. Each of the labels has a [!UICONTROL Friendly Name] and a short [!UICONTROL Name] which is just an abbreviation of the type and a number. For example, the [!DNL C1] label is for "No third-party export" which is what we need for our Loyalty policy.

![Data Governance Label](assets/governance-policies.png)

Now it's time to label the data whose usage we want to restrict:

1. In the Platform user interface, select **[!UICONTROL Datasets]** in the left navigation
1. Open the `Luma Loyalty Dataset`
1. Go to the **[!UICONTROL Data Governance]** tab
1. You can either apply labels to individual fields or apply them to the entire dataset. We will apply the label to the entire dataset. Click the pencil icon. If you don't see the icon, try making your browser wider or scrolling the middle panel to the right.
    ![Data Governance](assets/governance-dataset.png)
1. In the modal, expand the **[!UICONTROL Contract Labels]** section and check the **[!UICONTROL C2]** label
1. Select the **[!UICONTROL Save changes]** button
    ![Data Governance](assets/governance-applyLabel.png)
1. Returning to the main [!UICONTROL Data Governance] screen, with the **[!UICONTROL Show inherited labels]** toggle on, you can see how the label has been applied to all of the fields in the dataset.
    ![Data Governance](assets/governance-labelsAdded.png)


<!--adding extra, unnecessary fields from field groups makes it harder to see which fields really need labels-->
<!--Are there any best practices for applying governance labels-->

## Create data governance policies

Now that our data is labeled, we can create a policy.

1. In the Platform user interface, select **[!UICONTROL Policies]** in the left navigation
1. On the Browse tab, there is already an out-of-the-box policy called "3rd party export restriction" that associates the C2 label with the marketing action [!UICONTROL Export to Third Party]&mdash;exactly what we need!
1. Select the policy and then enable it via the **[!UICONTROL Policy status]** toggle
    ![Data Governance](assets/governance-enablePolicy.png)

You can create your own policies by selecting the **[!UICONTROL Create policy]** button. This opens a wizard which allows you can combine multiple labels and marketing action restrictions.

## Enforce governance policies

Enforcement of governance policies is obviously a key component to the framework. Enforcement happens downstream when data is activated and sent out of Platform, especially with the Real-Time Customer Data Platform, which you may or may not be licensing. Either way, it's out of the scope of this tutorial. But so you're not left hanging, you can learn more about how policies are enforced in this video, which I've queued up to the relevant portion. It will also show you what happens when a policy is violated.

>[!VIDEO](https://video.tv.adobe.com/v/33631/?t=151&quality=12&learn=on)


## Additional Resources

* [Data Governance documentation](https://experienceleague.adobe.com/docs/experience-platform/data-governance/home.html)
* [Dataset Service API reference](https://www.adobe.io/experience-platform-apis/references/dataset-service/)
* [Governance Policy Service API reference](https://www.adobe.io/experience-platform-apis/references/policy-service/)

Now let's move on to [query service](run-queries.md).
