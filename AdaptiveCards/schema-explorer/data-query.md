---
title:  Data.Query Action
author: luywang
description: This page provides documentation for the `Data.Query` input in the Adaptive Cards schema.
ms.author: luywang
ms.date: 12/11/2025
ms.topic: concept-article
---

# Data.Query

> [!NOTE]
> **Are you building Copilot, Teams or Outlook scenarios powered by Adaptive Cards?**
> Visit [**Adaptive Card Documentation Hub**](https://adaptivecards.microsoft.com/), the new one-stop-shop for all your Adaptive Card needs! It has all the resources you're looking for, including complete documentation for many new features, such as [Responsive layout](https://adaptivecards.microsoft.com/?topic=responsive-layout), [Icon](https://adaptivecards.microsoft.com/?topic=Icon), [Badge](https://adaptivecards.microsoft.com/?topic=Badge), [Carousel](https://adaptivecards.microsoft.com/?topic=Carousel), [Charts](https://adaptivecards.microsoft.com/?topic=Chart.Line), and much more!

> **Important note about accessibility:**
> In version 1.3 of the schema we introduced a [**label**](/adaptive-cards/authoring-cards/input-validation#labels) property on Inputs to improve accessibility. If the [Host app you are targeting](/adaptive-cards/resources/partners) supports v1.3 you should use **label** instead of a **TextBlock** as seen in some samples below. Once most Host apps have updated to the latest version we will update the samples accordingly.

## Data.Query

The data populated in the event payload for fetching dynamic choices, sent to the card-author to help identify the dataset from which choices might be fetched to be displayed in the dropdown. It might contain auxiliary data to limit the maximum number of choices that can be sent and to support pagination.

### Data.Query Properties

| Property | Type | Required | Description | Version |
| :--- | :--- | :--- | :--- | :--- |
| **dataset** | `string` | Yes | The dataset to be queried to get the choices. | 1.6 |
| **count** | `number` | No | The maximum number of choices that should be returned by the query. It can be ignored if the card-author wants to send a different number. | 1.6 |
| **skip** | `number` | No | The number of choices to be skipped in the list of choices returned by the query. It can be ignored if the card-author does not want pagination. | 1.6 |

---

## Properties

### dataset

The dataset to be queried to get the choices.

* **Type**: `string`
* **Version**: 1.6
* **Required**: Yes

### count

The maximum number of choices that should be returned by the query. It can be ignored if the card-author wants to send a different number.

* **Type**: `number`
* **Version**: 1.6
* **Required**: No

### skip

The number of choices to be skipped in the list of choices returned by the query. It can be ignored if the card-author does not want pagination.

* **Type**: `number`
* **Version**: 1.6
* **Required**: No
