---
title: Create an XDM schema
description: Learn how to create an XDM schema for mobile app events.
exl-id: c6b0d030-437a-4afe-b7d5-5a7831877983
---
# Create an XDM schema

Learn how to create an XDM schema for mobile app events.

Standardization and interoperability are key concepts behind Adobe Experience Platform. Experience Data Model (XDM), driven by Adobe, is an effort to standardize customer experience data and define schemas for customer experience management.

## What are XDM schemas?

XDM is a publicly documented specification designed to improve the power of digital experiences. It provides common structures and definitions that allow any application to communicate with Platform services. By adhering to XDM standards, all customer experience data can be incorporated into a common representation that can deliver insights in a faster, more integrated way. You can gain valuable insights from customer actions, define customer audiences through segments, and express customer attributes for personalization purposes.

Experience Platform uses schemas to describe the structure of data in a consistent and reusable way. By defining data consistently across systems, it becomes easier to retain meaning and therefore gain value from data.

Before data can be ingested into Platform, a schema must be composed to describe the data’s structure and provide constraints to the type of data that can be contained within each field. Schemas consist of a base class and zero or more schema field groups. 

For more information on the schema composition model, including design principles and best practices, see the [basics of schema composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en) or the course [Model Your Customer Experience Data with XDM](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm).

>[!TIP]
>
>If you're familiar with Analytics Solution Design Reference (SDRs), you can think of a schema as a more robust SDR.

## Prerequisites

To complete the lesson, you must have permission to create an Experience Platform schema.

## Learning objectives

In this lesson, you will:

* Create a schema in the Data Collection interface
* Add a standard field group to the schema
* Create and add a custom field group to the schema

## Navigate to schemas

1. Log into the Adobe Experience Cloud.

1. Open the app switcher, then select **[!UICONTROL Data Collection]** 

    ![3x3 drop down](assets/mobile-schema-navigate1.png)

1. Make sure you are in the Experience Platform sandbox you are using for this tutorial.

    >[!NOTE]
    >
    > Customers of Platform-based applications like Real-Time CDP should use a development sandbox for this tutorial. Other customers will use the default production sandbox.


1. Select **[!UICONTROL Schemas]** under **[!UICONTROL Data Management]**.

    ![tags home screen](assets/mobile-schema-navigate3.png)

You are now on the main schemas page and are presented with a list of any existing schemas. You can also see tabs corresponding to the core building blocks of a schema:

* **Field groups** are reusable components that define one or more fields to capture specific data, such as personal details, hotel preferences, or address. 
* **Classes** define the behavioral aspects of the data that the schema contains. For example: `XDM ExperienceEvent` captures time-series, event data and `XDM Individual Profile` captures attribute data about an individual.
* **Data types** are used as reference field types in classes or field groups in the same way as basic literal fields.

The above descriptions are a high-level overview. For more details, see the [Schema building blocks](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/schema-building-blocks.html) video or read [Basics of schema composition](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html?lang=en) in the product documentation.

In this tutorial, you use the Consumer Experience Event field group and create a custom one to demonstrate the process. 

>[!NOTE]
>
>Adobe continues to add more standard field groups and they should be used whenever possible since these fields are implicitly understood by Experience Platform services and provide greater consistency when used across Platform components. Using standard field groups provides tangible benefits such automatic mapping in Analytics and AI features in Platform.

## Luma app schema architecture

In a real-world scenario, the schema design process might look like this:

* Gather business requirements.
* Find prebuilt field groups to cover as many requirements as possible.
* Create custom field groups for any gaps.

For learning purposes, you will use prebuilt and custom field groups. 

* **Consumer Experience Event**: Prebuilt field group that has many common fields.
* **App Information**: Custom field group designed to mimic TrackState/TrackAction Analytics concepts.

<!--Later in the tutorial, you can [update the schema](lifecycle-data.md) to include the **[!UICONTROL AEP Mobile Lifecycle Details]** field group.-->

## Create a schema 

1. Select **[!UICONTROL Create Schema]** to bring the options dropdown menu, then select **[!UICONTROL XDM ExperienceEvent]**.

    ![Selecting ExperienceEvent from drop down](assets/mobile-schema-create.png)

1. Search for `Consumer Experience Event`.

1. You can preview the fields and/or read the description for more details before selecting.

1. Select the checkbox and then **[!UICONTROL Add field groups]**.

    ![Selecting field group](assets/mobile-schema-select-field-groups.png)

    You are brought back to the main schema composition screen where you can see all the available fields.

1. Give your schema a name by selecting **[!UICONTROL Untitled schema]** from the top left and then providing a **[!UICONTROL Display name]** & **[!UICONTROL Description]**, for example `Luma Tutorial Mobile` and `"Luma App" schema for Adobe Tutorial`

1. Select **[!UICONTROL Save]**.

    ![Selecting apply](assets/mobile-schema-name-save.png)

>[!NOTE]
>
>Keep in mind that you do not have to use all the fields in a group. If it’s helpful, you can think of a schema as an empty data layer. In your app, you populate the relevant values at the appropriate time.
>
>The `Consumer Experience Event` has a data type called `Web information`, which describes events like page view and link clicks. At the time of writing, there isn’t a mobile app parity to this feature, so you are going to create your own. 

## Create a custom data type

You begin by creating a custom data type describing the two events:

* Screen view
* App interaction

1. Select the **[!UICONTROL Data types]** tab, then select **[!UICONTROL Create data type]**.

    ![Selecting data type menu](assets/mobile-schema-datatype-create.png)

1. Give it a **[!UICONTROL Display name]** and **[!UICONTROL Description]**, for example `App Information` and `Custom data type describing "Screen Views" & "App Actions"`

    ![Providing name & description](assets/mobile-schema-datatype-name.png)

    >[!TIP]
    >
    > Always use readable, descriptive [!UICONTROL display names] for your custom fields, as this practice makes them more accessible to marketers when the fields surface in downstream services like the segment builder.


1. To add a field, select the (+) button. 

    This field is a container object for app interaction. Give it a camel-case **[!UICONTROL Field name]** `appInteraction`, **[!UICONTROL display name]** `App Interaction`, and **[!UICONTROL type]** `Object`.

1. Select **[!UICONTROL Apply]**.

    ![Adding new app action event](assets/mobile-schema-datatype-app-action.png)

1. To measure how often an action has occurred, add a field by selecting the (+) button next to the `appInteraction` object you created. 

1. Give it a camel-case **[!UICONTROL Field name]** `appAction`, **[!UICONTROL display name]** of `App Action` and **[!UICONTROL type]** `Measure`. 

    This step would be the equivalent of a success event in Adobe Analytics.

1. Select **[!UICONTROL Apply]**.

    ![Adding action name field](assets/mobile-schema-datatype-action-name.png)

1. Add a field describing the type of interaction by selecting the (+) button next to the `appInteraction` object. 

1. Give it a **[!UICONTROL Field name]** `name`, **[!UICONTROL display name]** of `Name` and **[!UICONTROL type]** `String`. 

    This step is the equivalent of a dimension in Adobe Analytics. 

    ![Selecting apply](assets/mobile-schema-datatype-apply.png)

1. Scroll to the bottom of the right rail and select **[!UICONTROL Apply]**.

1. Follow the same pattern to create an `appStateDetails` object containing a Measure field called `screenView` and two Strings called `screenName` and `screenType`.

1. Select **[!UICONTROL Save]**.

    ![Final state of data type](assets/mobile-schema-datatype-final.png)

## Add a custom field group

Now add a custom field group using your custom data type:

1. Open the schema that you created earlier in this lesson.

1. Select **[!UICONTROL Add]** next to **[!UICONTROL Field groups]**.

    ![Adding new field group](assets/mobile-schema-fieldgroup-add.png)

1. This time you create a custom field group by selecting the **[!UICONTROL Create new field group]** radio button near the top, then provide a name and description, for example, `App Interactions` and `Fields for app interactions`.

    ![Providing name & description](assets/mobile-schema-fieldgroup-name.png)

1. From the main composition screen, add a field to the root of the schema. 

1. Select the (+) next to the name of the schema. 

1. In the right rail, provide a **[!UICONTROL Field name]** of `appInformation`, a display name of `App Information`. 

1. Select `App Information` from the **[!UICONTROL Type]** drop down, the data type you created in the previous exercise.

1. Select **[!UICONTROL Apply]**.

    ![Selecting apply](assets/mobile-schema-fieldgroup-apply.png)

>[!NOTE]
>
>Custom field groups are always placed under your Experience Cloud Org identifier.
>
>`_techmarketingdemos` is replaced with your Org's unique value.

You now have a schema to use for the rest of the tutorial.

Next: **[Create a [!UICONTROL datastream]](create-datastream.md)**

>[!NOTE]
>
>Thank you for investing your time in learning about Adobe Experience Platform Mobile SDK. If you have questions, want to share general feedback, or have suggestions on future content, please share them on this [Experience League Community discussion post](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-platform-launch/tutorial-discussion-implement-adobe-experience-cloud-in-mobile/td-p/443796)