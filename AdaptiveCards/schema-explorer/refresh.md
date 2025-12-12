---
title:  Refresh Element
author: luywang
description: This page provides documentation for the `Refresh` element in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Refresh

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Refresh

Defines how a card can be refreshed by making a request to the target Bot.

**Introduced in version 1.4**

### Refresh Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **action** | `Action.Execute` | No | The action to be executed to refresh the card. Clients can run this refresh action automatically or can provide an affordance for users to trigger it manually. | 1.4 |
| **expires** | `string` | No | A timestamp that informs a Host when the card content has expired, and that it should trigger a refresh as appropriate. The format is ISO-8601 Instant format. E.g., 2022-01-01T12:00:00Z. | 1.6 |
| **userIds** | `string[]` | No | A list of user Ids informing the client for which users should the refresh action should be run automatically. Some clients will not run the refresh action automatically unless this property is specified. Some clients may ignore this property and always run the refresh action automatically. | 1.4 |

---

## Properties

### action

The action to be executed to refresh the card. Clients can run this refresh action automatically or can provide an affordance for users to trigger it manually.

* **Type**: `Action.Execute`
* **Required**: No
* **Allowed values**:
    * `Action.Execute`

### expires

A timestamp that informs a Host when the card content has expired, and that it should trigger a refresh as appropriate. The format is ISO-8601 Instant format. E.g., 2022-01-01T12:00:00Z.

* **Type**: `string`
* **Version**: 1.6
* **Required**: No

### userIds

A list of user Ids informing the client for which users should the refresh action should be run automatically. Some clients will not run the refresh action automatically unless this property is specified. Some clients may ignore this property and always run the refresh action automatically.

* **Type**: `string[]`
* **Required**: No
